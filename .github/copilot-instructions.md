# Copilot instructions — REVAMP FE

Purpose: give AI coding agents immediate, actionable context for safe edits.

Preferred model: GPT-5 mini (agent preference only — cannot change server settings).

Big picture
- Single-page static frontend. Primary artifact: `demo.html` at repo root.
- No build system, package manifests, or backend discovered; treat edits as static HTML/CSS/JS changes.

Key files
- `demo.html` — single source of truth for UI and behavior. Inspect and edit this file for UI changes.

Common workflows & commands
- Serve locally for testing: `python3 -m http.server 8000` then open `http://localhost:8000/demo.html`.
- Alternate quick server: `npx http-server . -p 8000`.
- Debug in browser DevTools; prefer iterative small edits and reload.

Project-specific conventions
- Keep changes minimal and local: prefer in-file edits to introducing new build tools or frameworks unless requested.
- If extracting CSS/JS to new files, update `demo.html` references and keep commits small and reversible.
- Preserve existing layout and inline scripts unless the user asks to refactor.

Integration points & dependencies
- No external packages or APIs were found in the repo root. Before adding external dependencies, confirm with the repo owner.

Editing guidance for AI agents
- Make minimal atomic changes with clear commit messages.
- When adding interactive behavior, use unobtrusive DOM APIs (vanilla JS) to match the repo's current approach.
- If you need to run additional commands or create files (e.g., `package.json`), ask the user first.

Examples
- To add a button that shows an alert: open `demo.html`, insert a `<button id="demo-btn">Click</button>` in the body and a small `<script>` that attaches a click handler.

When uncertain
- Open `demo.html` and ask the user for intent before substantial refactors.

Notes about model preference
- The repository's instruction can request using GPT-5 mini as the preferred agent. Platform-level enabling is out-of-band; add this as an agent preference, not a configuration change.

If anything above is unclear or you want deeper coverage (tests, CI, or adding a build stack), say which area to expand.
