# Deployment Workflow

To avoid cache stagnation issues on GitHub Pages, follow this **Strict Formula** for every visible update:

1.  **Code Changes:** Make your CSS/JS/HTML edits.
2.  **Version Bump (Visual):** Update the version string in `composers.html` (e.g., `(v1.17)` -> `(v1.18)`).
3.  **Cache Bust (Link):** Update the incoming link in `index.html` (e.g., `composers.html?v=1.17` -> `composers.html?v=1.18`).
4.  **Commit & Push:** Commit all files together.
5.  **Verify:** Instruct the user to navigate via the `index.html` card to force a fresh load.

*Reasoning:* GitHub Pages uses aggressive caching. Changing the query parameter on the incoming link is the most reliable way to force the browser to fetch the new version of the HTML.
