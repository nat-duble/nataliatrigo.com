Push the current branch to GitHub Pages so the live site is updated.

This repo deploys via the `gh-pages` branch on `origin` (git@github.com:nat-duble/nataliatrigo.com.git). Pushing to that branch triggers GitHub Pages to rebuild and publish the site automatically.

Steps:
1. Confirm the current branch is `gh-pages`. If not, warn the user and stop.
2. Check for any uncommitted changes with `git status`. If there are any, tell the user to run /save first, then stop.
3. Run `git push origin gh-pages`.
4. Report success and remind the user that GitHub Pages usually takes 1–2 minutes to rebuild and go live.
