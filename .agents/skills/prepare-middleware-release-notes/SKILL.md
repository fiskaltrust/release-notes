---
name: prepare-middleware-release-notes
description: Create comprehensive release notes for a fiskaltrust Middleware version. Use when the user asks to prepare, draft, or compile Middleware release notes for a specific version (e.g. "create release notes for 1.3.80"). Requires a version number as input.
---

# Create Middleware Release Notes

You are tasked with creating comprehensive release notes for the fiskaltrust Middleware.

## Workflow

1. **Get the Version from User Input**
    - The version number is provided by the user when this skill is invoked
    - If no version was provided, ask the user for it before proceeding

2. **Find Pull Requests with Release Notes Label**
    - Search for pull requests in milestone v{{version}} with label `meta-needs-release-notes`
    - Use the GitHub search query: `repo:fiskaltrust/middleware milestone:v{{version}} label:meta-needs-release-notes is:pr`
    - Use available GitHub tooling (MCP GitHub tools if available, otherwise the `gh` CLI, e.g. `gh search prs` / `gh pr view` / `gh api`)

3. **Process Each Pull Request**
    - For each PR found, spawn a sub-agent (`spawn_agent`) to analyze it and draft its release note entry. Include all necessary context in the sub-agent's message (PR number, repository, format requirements below), since sub-agents don't see the conversation history.
    - Each sub-agent should:
      - Fetch the full PR details including labels, description, and linked issues
      - The affected market is specified by the `market-<market>` label
      - The affected queue packages are specified by the `queue-<package>` labels
      - If the `queue` label is set then all queues are affected (get all queue packages from the fiskaltrust/middleware repository workflow `.github/workflows/queue-package.yml`)
      - The affected SCU packages are specified by the `scu-<market>-<package>` labels
      - Fetch linked issues to understand the context and requirements.
        Also fetch issues that are linked from other repositories.
      - Examine the code changes in the PR
      - Analyze the technical implementation and business impact
      - Draft a concise, user-focused release note entry.
        The target audience is not developers but users.
        Don't focus on implementation details but on what was achieved, how that impacts the users and what they might need to do when updating.
      - Use the following format:
        ```md
        ## {{Affected Market Flag Emojis}} {{Relevant category like Feature, Bug Fix, Improvement, etc.}}: {{Short Summary}} ([fiskaltrust/middleware#{{PR number}}](https://github.com/fiskaltrust/middleware/pull/{{PR number}}))

        {{Detailed description}}

        ### Affected packages:
        - _{{Affected Middleware packages}}_
        ```
      - The affected packages can be either Queue or SCU packages
      - Queue packages follow the format `fiskaltrust.Middleware.Queue.<package>` (e.g. `fiskaltrust.Middleware.Queue.SQLite`)
      - SCU packages also contain the market `fiskaltrust.Middleware.SCU.<market>.<package>` (e.g. `fiskaltrust.Middleware.SCU.DE.FiskalyCertified`)

4. **Compile Release Notes**
    - Create a new markdown file in the `middleware/` directory
    - Name it following the pattern: `YYYY-MM-DD-{{version}}.md`
    - Structure the release notes with:
      - Header with version and date
        ```md
        ---
        authors: poscreator
        slug: middleware/{{version}}
        tags: [Middleware, {{All affected markets}}]
        ---
        # Middleware {{version}}
        [![Static Badge](https://img.shields.io/badge/milestone-v{{version}}-green?logo=github)]({{Milestone url}})

        {{Summary of the release}}

        {{Release notes for each Pull Request}}
        ```
    - Wrap long lines at periods

5. **Review and Finalize**
    - Ensure all PRs with the label are covered
    - Check for consistent formatting and clarity
    - Verify technical accuracy
    - Verify that all Affected packages actually exist by checking the available packages in the package workflows from the fiskaltrust/middleware repository: `.github/workflows/queue-package.yml` for the queues or `.github/workflows/scu-<market>-package.yml` for the SCUs. Don't add InMemory queues and SCUs.

## Release Notes Format

Each release note entry should:
- Be written from a user perspective
- Explain WHAT changed for the user and WHY it matters
- Not explain what changed technically
- Not include technical details, especially not any code
- Reference the PR number for traceability
- Be concise but informative

## Important Notes

- Spawn a sub-agent for each PR to ensure thorough analysis; run independent PR analyses in parallel
- Sub-agents should read the PR description, linked issues, and actual code changes
- Focus on user-facing changes; internal refactoring should be mentioned only if it affects performance or behavior
- Group related changes together when it makes sense
