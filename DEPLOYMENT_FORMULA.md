# Deployment Workflow (Strict)

To avoid cache stagnation and version mismatch issues on GitHub Pages, follow this **Strict Formula** for every visible update. 

**Rule #1: Atomic Deployments.** Never push code fixes separately from version bumps. ALL changes must be in requested in a single commit.

## The Formula
1.  **Code Changes:** Make your CSS/JS/HTML edits first. Verify they are applied locally.
2.  **Version Bump (Visual):** Update the version string in `composers.html` (e.g., `(v1.17)` -> `(v1.18)`).
3.  **Cache Bust (Link):** Update the incoming link in `index.html` (e.g., `composers.html?v=1.17` -> `composers.html?v=1.18`).
4.  **One Commit:** Adding all files (`git add .`) and commit with a clear message including the version number.
5.  **Wait:** Pause for 2-3 seconds to ensure filesystem/git lock stability.
6.  **Push:** Execute `git push origin main`.
7.  **Verify:** Instruct the user to navigate via the `index.html` card to force a fresh load.

*Reasoning:* GitHub Pages uses aggressive caching. Changing the query parameter on the incoming link is the most reliable way to force the browser to fetch the new version of the HTML. Partial pushes lead to "split-brain" states where HTML is old but CSS is new.
