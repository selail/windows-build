# windows-build

On-demand `windows-latest` GitHub Actions build for Luxi's Windows "Download app" feature. Dispatched via `repository_dispatch` from the Luxi server (`WindowsAppBuildService`/`GithubActionsDispatchClient`); no standing Windows build machine.

The server dispatches the build, then polls the Actions REST API for the run's status and its uploaded artifact — there's no callback into Luxi, so this needs no public ingress on the server's side and works the same whether the server is running on dev or prod.

Public by design: free/unlimited Actions minutes on `windows-latest`, and this workflow contains no Luxi source or secrets. No repository secrets are needed — only a fine-grained PAT (held server-side, not in this repo, scoped to `contents: read` + `actions: read/write` on this repo) can trigger a build or read its results.
