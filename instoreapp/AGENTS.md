# InStore App release notes

Rules for the release notes in `instoreapp/`, published at `https://docs.fiskaltrust.cloud/changelog/instoreapp/<version>`.
The general build rules in the root [AGENTS.md](../AGENTS.md) apply as well.

## Source of truth

- Issues come from the private repository [fiskaltrust/fiskaltrust-instore-app](https://github.com/fiskaltrust/fiskaltrust-instore-app/issues).
  Release notes still link to these issues. This is intentional and was requested for traceability, even though readers without access get a 404.
  Keep the links; don't remove them or replace them with plain issue numbers.
- A version's issues are the issues assigned to its GitHub milestone.
  Milestones are named `instore-app-v<version>` (e.g. `instore-app-v1.3.2`, `instore-app-v1.3.2-rc3`); releases before 1.3.0 used `v<version>`.
  Look up the milestone number by title:
  `gh api "repos/fiskaltrust/fiskaltrust-instore-app/milestones?state=all&per_page=100" --jq '.[] | "\(.number) \(.state) \(.title)"'`
- List a milestone's issues (skip entries with a `pull_request` field):
  `gh api "repos/fiskaltrust/fiskaltrust-instore-app/issues?milestone=<number>&state=all&per_page=100"`
- **Only issues with the label `Release Notes` are documented.**
  - Every closed issue with that label must appear exactly once in the "Details" section, also when it is a highlight.
    If one is deliberately left out, say so to the user; never drop it silently.
  - Issues labeled `INTERNAL` are never documented (this includes the "[Release Notes] write release notes for ..." tracking issue).
  - Report to the user, but do not document: closed issues with neither `Release Notes` nor `INTERNAL`, and open issues with `Release Notes`.
    The user decides whether they get the label or move to another milestone.
- Read each issue's body and comments to understand the user-facing effect; the title alone is often an internal note.

## Final releases and release candidates

- Normally only final releases get release notes (e.g. `1.3.1`).
- A release candidate (`<version>-rc<N>`, higher N is newer) only gets its own release notes when the user explicitly asks for it.
- A release candidate counts as **officially released** only if release notes were published for it,
  i.e. a `instoreapp/*-<version>-rc<N>.md` file exists (or existed before being renamed to the final version).
  All other release candidates (e.g. `1.3.2-rc5`) were internal only.
- **Every** closed `Release Notes` issue of the final milestone **and** of all `instore-app-v<version>-rc*` milestones must be in the final release notes,
  including issues of internal release candidates.
  If it's unclear whether an issue belongs in the release notes, ask the user, listing each one with its number and title (e.g. `#756 [Payment] When we receive the same payment request ...`).
- If release notes for a release candidate of the same version already exist (e.g. `2026-08-05-1.3.2-rc3.md`),
  do not create a second file. Extend the existing one, and rename it with `git mv` to the new version and date
  (e.g. `<release-date>-1.3.2.md`). The same applies when a newer release candidate replaces an older one.
  Update `slug`, the H1 title and the milestone badges accordingly.
  - Every highlight then states the first **officially released** version it is available in, right below its heading:
    `_Available since:_ v1.3.2-rc3`, or `v1.3.2` for highlights that are new in the final release or come from an internal release candidate.
  - "Details" is split into one `### v<version>` subsection for the final release and one per officially released release candidate, sorted newest to oldest.
    The final release is always newer than its release candidates.
    Issues from internal release candidates go into the final release's subsection; they don't get a subsection of their own.
  - Renaming changes the URL (`/changelog/instoreapp/1.3.2-rc3` becomes `/changelog/instoreapp/1.3.2`), so the old link breaks.
    Tell the user; whether a redirect is added in `fiskaltrust/service-docs-ui` is their decision.
- **Merging to `main` publishes immediately.** Prepare notes for an unreleased version on a branch (`instore-app-v<version>`) and merge only when the version is released.

## File

- Don't change release notes of other versions, even to fix inconsistencies in older files (they don't all follow these rules).
  The only exception is a release candidate file of the same version, which is extended and renamed as described above.
- Path: `instoreapp/YYYY-MM-DD-<version>.md`, where the date is the release date with two-digit month and day.
  If the release date is unknown, ask the user; the milestone's due date is only a plan.
- Frontmatter, title, badges and truncate marker:

  ```md
  ---
  authors: instoreapp
  slug: instoreapp/<version>
  tags: [InStore App, Experience, Europe]
  ---

  # InStore App <version>
  [![Static Badge](https://img.shields.io/badge/milestone-v<version>-green?logo=github)](https://github.com/fiskaltrust/fiskaltrust-instore-app/milestone/<number>?closed=1)

  <!--truncate-->
  ```

  - Link the badge to the specific milestone number, not to the milestone list.
    For a final release that includes officially released release candidates, add one badge per officially released milestone, newest first.
    Internal release candidates get no badge.
  - In the badge text, escape `-` as `--` and `_` as `__` (shields.io syntax), e.g. `milestone-v1.3.2--rc3-green`.
  - Keep `<!--truncate-->` directly after the badges; without it the site build fails.

## Structure

In this order:

1. **Admonitions (optional)**, for things users must know before updating (fresh install needed, unsupported Android versions, breaking changes):
   `:::caution` ... `:::`
2. **Highlights**: one `##` section per highlight, separated by `---`.
3. **Known Problems (optional)**: `## Known Problems` with a `:::caution` block.
4. **Details**: `## Details`, the complete list of **all** documented changes (highlights included), with the subsections `### Features`, `### Improvements`, `### Bug fixes`, in that order.
   Leave out empty subsections. Older release notes call this section "Other Changes" and don't repeat the highlights there; don't copy that.
   When split by version, use `### v<version>` with `#### Features` etc. below it.

### Highlights

- The user decides which changes become highlights.
  Propose candidates: new payment providers, visible new features, certifications, changes that need user action.
  Order them by importance to users, not by issue number.
- Format:

  ```md
  ## <Short user-facing title>

  <What is new, what the user gains, and what they need to do (e.g. a setting to enable). 1-3 short paragraphs or a list.>

  ![<alt text>](images/v<version>_<short_name>.png)

  _Affected issue(s):_ [#<n>](https://github.com/fiskaltrust/fiskaltrust-instore-app/issues/<n>), [#<m>](...)

  ---
  ```

- Several related issues can be grouped into one highlight.
  Each issue of a highlight is also listed in "Details", as a short one-line summary.
- A highlight without an issue is allowed (e.g. "Release on Google Play"); leave out the "Affected issue(s)" line then.
- Link to public documentation or vendor pages where it helps (e.g. the payment feature matrix).

### Screenshots

- Highlights should have a screenshot showing what is new, where possible.
- If an Android device with the InStore App is connected (`adb devices`), screenshots can be taken over ADB.
  See [fiskaltrust-instore-app/testing](https://github.com/fiskaltrust/fiskaltrust-instore-app/tree/main/fiskaltrust-instore-app/testing) and its `tools/` folder
  (`ui.py` for dump/tap/screenshot, `nav.py` to navigate, `adbdev.py`); the plain commands are
  `adb exec-out screencap -p > shot.png`, `adb shell uiautomator dump /data/local/tmp/ui.xml` and `adb shell input tap X Y`.
  - Check the installed version first (`adb shell dumpsys package eu.fiskaltrust.instore.app | grep versionName`); it must contain the feature.
  - Only navigate and open views. Don't change settings, pair or unpair, or start payments without asking the user.
  - In Git Bash, set `MSYS_NO_PATHCONV=1`, otherwise device paths like `/data/local/tmp` get rewritten.
  - Without a device, ask the user for screenshots and name the highlights that would benefit most.
- Screenshots must not show CashBox IDs, access tokens, terminal IDs, API keys or personal data: crop them out.
- Store them in `instoreapp/images/` as `v<version>_<snake_case_name>.png`, with the version of the release that introduced the feature.
  Don't rename images when release candidate notes are renamed to the final version.
- Keep them small: about 400 px wide per screen (a side-by-side composite of two screens may be about 800 px), crop to the relevant part, and aim for well under 150 KB.

### Details entries

- Format: `- [<Area>] <user-facing description> [#<n>](https://github.com/fiskaltrust/fiskaltrust-instore-app/issues/<n>)`
- `<Area>` is the bracket prefix of the issue title (e.g. `[Payment]`, `[Receipt]`, `[Settings]`, `[Printing]`, `[Docs]`).
  If the title has none, choose a fitting one from those already used.
- Issues from other repositories are linked with their full name, e.g. `[fiskaltrust/service-possystem-api#73](https://github.com/fiskaltrust/service-possystem-api/issues/73)`.
- Categorize by the actual effect, not by the labels: new capability → Features, better existing behavior → Improvements, wrong behavior fixed → Bug fixes.

## Writing style

- English, written for merchants, PosDealers and PosCreators, not for developers.
  Explain what changed for the user and why it matters, not how it was implemented. No code.
- Rewrite issue titles into clear sentences.
  Remove internal notes (e.g. "--> should somehow catch the error", release-blocker remarks, deadlines, people's names).
  Describe bugs as the problem that was fixed, e.g. "... was still reported as successful".
- Use the official product names: InStore App, POS System API, Viva, Hobex (POSit, ECR), Worldline / PayOne (Tap on Mobile, SmartPOS), Softpay.io, Global Payments (GP tom, GP Pay), Shift4, Nexi, SumUp.
- Check spelling. Earlier notes contain typos; don't copy them.

## Before finishing

- All closed `Release Notes` issues of all relevant milestones are covered; the reported leftovers were shown to the user.
- Filename date, `slug`, H1 and badges match the version.
- `<!--truncate-->` is present; all relative image paths exist.
- External links are valid; the PR runs a lychee link check and a full site build.
  Links to `fiskaltrust-instore-app` are skipped by the link check because the repository is private.
- The PR is reviewed by `@fiskaltrust/team-instoreapp-experience` (CODEOWNERS).
