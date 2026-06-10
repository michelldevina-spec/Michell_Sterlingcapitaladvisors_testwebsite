---
description: Secret/security scan, README + GitHub Pages setup, commit & push, and update repo "About" on GitHub
---

Perform the following steps in order. Stop and report to the user (without pushing) if a
secret or security issue is found in step 1 or 2.

1. **Secret scan**: Search staged, unstaged, and untracked files for hardcoded credentials,
   API keys, tokens, passwords, private keys, or `.env`-style files. Confirm `.gitignore`
   excludes any local secret files. If anything sensitive is found, stop here and report it
   instead of proceeding to commit/push.

2. **Security review**: Invoke the `security-review` skill against the current changes to
   check for vulnerabilities (XSS, injection, exposed endpoints/credentials, unsafe external
   resources, etc.) before anything is published.

3. **README**: Ensure `README.md` exists at the project root and accurately reflects the
   current project (purpose, structure, how to run/preview, deployment). Create or update it
   if missing, empty, or stale.

4. **GitHub Pages workflow**: Ensure `.github/workflows/deploy-pages.yml` exists and deploys
   the static site to GitHub Pages on push to `main` (via actions/configure-pages,
   actions/upload-pages-artifact, actions/deploy-pages). Create it if missing.

5. **Commit & push**: Stage relevant changes (never secrets, `.env` files, or credentials),
   commit with a concise message describing what changed, and push to the current branch's
   remote.

6. **Repo "About"**: Use `gh repo edit` to set/update the repository description and
   homepage URL (GitHub Pages URL: `https://<owner>.github.io/<repo>/`) to match the
   project.

7. **Verify GitHub Pages**: Confirm Pages is enabled and built from GitHub Actions (e.g. via
   `gh api repos/:owner/:repo/pages`). If not enabled, enable it via the GitHub API or tell
   the user it requires admin access in repo settings.

End with a short summary: what was scanned, what changed, and the live Pages URL.
