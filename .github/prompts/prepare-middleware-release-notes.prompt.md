---
agent: agent
tools: ['read/problems', 'read/readFile', 'edit/createDirectory', 'edit/createFile', 'edit/editFiles', 'search', 'github/get_file_contents', 'github/issue_read', 'github/list_issues', 'github/list_pull_requests', 'github/pull_request_read', 'github/search_code', 'github/search_issues', 'github/search_pull_requests', 'github/search_repositories', 'agent']
argument-hint: Provide the version to create releasenotes for
---

# Create Middleware Release Notes

You are tasked with creating comprehensive release notes for the fiskaltrust Middleware.

## Workflow

1. **Get the Version from User Input**
    - The version number will be provided as an argument when this prompt is invoked


2. **Find Pull Requests with Release Notes Label**
    - Use `github/search_pull_requests` to search for pull requests in milestone v{{version}} with label meta-needs-release-notes
    - The search query should be: `repo:fiskaltrust/middleware milestone:v{{version}} label:meta-needs-release-notes`

3. **Process Each Pull Request**
    - For each PR found, use the `#runSubagent` tool to analyze it and create release notes
    - Each subagent should:
      - Fetch the PR details using `github/pull_request_read` to retrieve the full PR details including labels, descriptions, and linked issues
      - The affected market is specified by the `market-<market>` label
      - The affected queue packages are specified by the `queue-<package>` labels
      - If the `queue` label is set then all queues are affected (Get all queue packages from the fiskaltrust/middleware repository workflow `.github/workflows/queue-package.yml`. Fetch the workflow files using `github/get_file_contents`.)
      - The affected SCU packages are specified by the `scu-<market>-<package>` labels
      - Fetch linked issues using `github/issue_read` to understand the context and requirements.
        Also fetch issues that are linked from from other repositories.
      - Use `web/githubRepo` to examine the code changes in the PR
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
        # Middleware 1.3.80
        [![Static Badge](https://img.shields.io/badge/milestone-v{{version}}-green?logo=github)]({{Milestone url}})
        
        {{Summary of the release}}
        
        {{Release notes for each Pull Request}}
        ```
    - Wrap long lines at periods

5. **Review and Finalize**
    - Ensure all PRs with the label are covered
    - Check for consistent formatting and clarity
    - Verify technical accuracy
    - Verify that all Affected packages actually exist by checking the available packages in the package workflows from the fiskaltrust/middleware repository `.github/workflows/queue-package.yml` for the queues or `.github/workflows/scu-<market>-package.yml` for the SCUs. Fetch the workflow files using `github/get_file_contents`. Don't add InMemory queues and SCUs.

## Release Notes Format

Each release note entry should:
- Be written from a user perspective
- Explain WHAT changed for the user and WHY it matters
- Don't explain WHAT changed technically
- Don't Include technical details especially not any code
- Reference the PR number for traceability
- Be concise but informative

## Important Notes

- Use the `#runSubagent` tool for each PR to ensure thorough analysis
- Subagents should read both the PR description, linked issues, and actual code changes
- Focus on user-facing changes; internal refactoring should be mentioned only if it affects performance or behavior
- Group related changes together when it makes sense