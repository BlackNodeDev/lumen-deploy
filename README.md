# Lumen Deploy

A simple, mobile-first GitHub Pages dashboard. One static app — no backend. You paste a fine-grained personal access token in Settings; it stays in this browser's `localStorage` and is sent only to `api.github.com`.

Not published yet. Do not create the GitHub repo, push, or enable Pages until Josh approves.

## Use it

1. Open `index.html` (or the hosted URL, once approved).
2. In **Settings**, paste a fine-grained token with:
   - **Contents** read/write
   - **Workflows** read/write (needed to add `.github/workflows/lumen-pages.yml`)
   - **Pages** read/write
   - **Actions** read/write
   - **Deployments** read
   - **Administration** write — only if enabling Pages still returns 403
3. Pick a repo, confirm, and publish. Prefer the Actions workflow. Legacy branch/folder is the fallback.
4. **Deploy now** triggers `workflow_dispatch`, or a Pages build request for legacy sites.

## Limits (honest)

- GitHub Pages has **one live URL per repo**, not Vercel-style preview subdomains. If a deployment has an `environment_url`, it is linked. Other branches still show commit, status and logs.
- Job log text often fails in the browser: GitHub's logs endpoint redirects to a signed URL that blocks this origin (CORS). The app then shows **Open on GitHub**.

## Local files

- `index.html` — the app
- `manifest.json`, `sw.js`, `icons/` — installable PWA shell
- `.github/workflows/pages.yml` — workflow to host *this* dashboard, used only after approval
- `test.js` — mocked API screenshots (not part of the site)

Suggested public repo name once approved: **lumen-deploy** (`https://blacknodedev.github.io/lumen-deploy/`).
