# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run start     # Start Vite dev server
npm run build     # Production build (outputs to dist/)
npm run preview   # Preview the production build
```

## Architecture

Vanilla JavaScript todo app — no framework, no runtime dependencies. Vite is used only as the dev server and bundler.

- **Entry:** `src/index.html` + `src/index.js`
- **State:** Single in-memory `todos` array (not persisted — lost on refresh)
- **Rendering:** `displayTodo()` re-renders the full list after every mutation

### Interaction model

| Action | Behavior |
|---|---|
| Click checkbox/text | Toggle complete |
| Double-click text | Enter inline edit mode |
| Enter (in edit) | Save edit |
| Escape (in edit) | Cancel edit |
| Delete button | Remove todo |

New todo text is auto-capitalized on the first letter before being added to the array.

### Vite config note

`vite.config.js` sets `root: './src'`, so the dev server and build treat `src/` as the project root. The production build outputs to `dist/` at the repo root.