# Support

onsystem, ondocs and signoff-ui have one maintainer: me, Diogo Esteves. This page says where to ask, what is supported, how releases work and how I handle AI-assisted pull requests. It applies to every repository under github.com/dgesteves that has no SUPPORT.md of its own.

## Where to ask

| You have | Where it goes |
|---|---|
| A question about setting it up or using it | The repository's Discussions, in **Q&A** |
| A bug: a wrong result, an error, a crash, or docs that don't work as written | An issue, with the **Bug report** form |
| An idea or a feature request | **Ideas** in Discussions first. It becomes an issue once we agree on the shape |
| Something you built with it | **Show and tell** in Discussions |
| A security problem | A private report. See [Security](#security). Never a public issue |

Per project:

| | Questions | Bugs | Security |
|---|---|---|---|
| onsystem | [Q&A](https://github.com/dgesteves/onsystem/discussions/categories/q-a) | [Bug report](https://github.com/dgesteves/onsystem/issues/new/choose). For a false positive, include the snippet and the output of `npx onsystem inspect` | [Report privately](https://github.com/dgesteves/onsystem/security/advisories/new) |
| ondocs | [Q&A](https://github.com/dgesteves/ondocs/discussions/categories/q-a) | [Bug report](https://github.com/dgesteves/ondocs/issues/new/choose). Say which setup (plugin, script tag, handler, MCP, CLI) and where the endpoint runs | [Report privately](https://github.com/dgesteves/ondocs/security/advisories/new) |
| signoff-ui | [Q&A](https://github.com/dgesteves/signoff-ui/discussions/categories/q-a) | [Bug report](https://github.com/dgesteves/signoff-ui/issues/new/choose). Say which adapter (AI SDK, AG-UI, ACP, assistant-ui) or the shadcn registry | [Report privately](https://github.com/dgesteves/signoff-ui/security/advisories/new) |

The smallest input that shows the problem helps more than anything else: a snippet, a page, a config, the version.

## Response times

One person maintains these projects, so there is no fixed response time. I read every issue, pull request and security report, and reply with a next step or a question. Security reports come first. If a thread has been quiet for a week, a comment on it is a fair nudge.

## What is supported

- **The latest release only.** Fixes ship in a new release of the latest minor version. I don't backport fixes to older versions.
- **Setups CI tests are supported.** Setups the docs describe but CI does not test, such as some MCP clients or some docs frameworks, are best effort: I fix what I can reproduce. If you're not sure which one yours is, ask in the issue.
- **Node:** the version in each package's `engines` field.

## Releases and versions

All three packages are 0.x, released with [Changesets](https://github.com/changesets/changesets). Each release has a changelog entry written for someone upgrading.

- **In 0.x, a minor can change things.** 0.10 to 0.11 may rename an option or change a default, and a caret range such as `^0.10.0` does not pick up 0.11. Read the changelog before you move to a new minor. Patch releases (0.11.0 to 0.11.1) only fix things.
- **Minors ship at most once a week, on Mondays. Patches can ship any day.**
- **Nothing is announced until its release is at least 24 hours old.** Some package managers hold back versions younger than a day, so the version a post describes is the one you can install.
- **The onsystem GitHub Action:** `uses: dgesteves/onsystem@v0` moves to every 0.x release. To decide when you upgrade, pin a commit SHA instead. The Claude Code plugin pins an exact onsystem version and moves only when the plugin updates.
- **1.0:** ondocs and signoff-ui plan 1.0 four to six weeks after their launch, once their APIs settle: for ondocs, the index format, the handler options and the embed URL; for signoff-ui, the props of DiffReview and ApprovalCard. ondocs removes its deprecated option names at 1.0. onsystem stays 0.x until its rule severities settle. After 1.0, a breaking change needs a major version.

## Security

Each repository's SECURITY.md says what counts as a vulnerability and how to report it: through GitHub's private vulnerability reporting, never in a public issue. A fix ships as a patch of the latest version, with an advisory once users can upgrade.

## AI-assisted contributions

I build these projects with AI coding agents. I review every change and merge it myself, and the tests and CI gates decide what is allowed in. Pull requests written with an AI agent are welcome on the same terms:

- **Say so.** Name the tool in the description, and say what you checked yourself.
- **Run the checks first.** Each CONTRIBUTING.md lists them. CI runs them too, and a red PR waits.
- **Open an issue first for a feature or a change in behaviour,** so we agree on the shape before any code exists. Small fixes with a test can go straight to a PR.
- **One change per pull request,** with a test that fails without it.
- **Keep the description short and true:** what changed, why, and how you tested it. Not a generated summary of the diff.

I may close a pull request without a full review when it skips these points, duplicates open work, or changes behaviour no issue agreed on. That is about my time, not about you. You are welcome to open an issue and try again.

**Good first issues** are kept for people new to the project. Comment on the issue before you start, so two people don't do the same one.

## Code of conduct

Every repository has a CODE_OF_CONDUCT.md. It applies in issues, pull requests and Discussions.
