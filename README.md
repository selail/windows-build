# windows-build

On-demand `windows-latest` GitHub Actions build for Luxi's Windows "Download app" feature. Dispatched via `repository_dispatch` from the Luxi server (`WindowsAppBuildService`/`GithubActionsDispatchClient`); no standing Windows build machine.

Public by design: free/unlimited Actions minutes on `windows-latest`, and this workflow contains no Luxi source or secrets — only a fine-grained PAT (held server-side, not in this repo) can trigger it.

## Setup

Add a repository secret `CALLBACK_TOKEN` matching the Luxi server's `WINDOWS_BUILDER_CALLBACK_TOKEN` env var.
