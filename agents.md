# AGENTS.md

## Project overview
This repository contains a single-page task and notes manager app built in one HTML file: `task.html`.

The app is effectively a front-end utility called TaskSync Pro that lets users:
- manage tasks with create, edit, delete, complete/incomplete toggle, priority, category, and due date fields
- filter tasks by search text, status, priority, and category
- view task counts in the navigation badges
- create and edit notes with different color themes and pinning
- persist both tasks and notes in browser `localStorage`
- switch between light and dark mode and keep the preference in `localStorage`
- share task content using the browser native share API and social/email links

This is not a framework-based app and there is no backend, build pipeline, or package manager setup in the repository.

## Repository structure
- `task.html` — the complete app source (HTML, CSS, and JavaScript in one file)
- `README.md` — minimal project description
- `agents.md` — project instructions for coding agents

## Code conventions
- Keep changes minimal and surgical.
- Prefer editing the existing single-file app structure instead of introducing new folders, frameworks, or tooling.
- Preserve the current Tailwind-based styling and class naming conventions unless the task explicitly requires a redesign.
- Use browser-native JavaScript patterns already present in the file; do not add React, TypeScript, or a build system unless a task explicitly requires it.
- If you add or change data keys, keep them compatible with the current `localStorage` usage.

## Important implementation details
- The app stores task data under `tasks_hub_data` and note data under `notes_hub_data` in `localStorage`.
- Theme preference is saved under `theme`.
- Task form fields: title, priority, category, due date, description.
- Notes support a title, body, color theme, and pinned state.
- The app renders UI dynamically from arrays and then re-renders when filters or mutations change.
- The share flow depends on browser APIs and `window.open` for platform-specific share URLs.

## When making changes
- Preserve the current behavior of the task and notes views.
- Keep the modal flows, validation, and render logic consistent with the current UI.
- If UI text changes, keep it concise and aligned with the app’s “TaskSync Pro” style.
- If you change storage keys or behavior, ensure old data still loads safely or degrades gracefully.
- Avoid broad refactors in `task.html`; this file is self-contained and should stay easy to reason about.

## Validation guidance
Because this project has no automated test suite, validation should be lightweight and browser-focused:
- open `task.html` in a browser or serve it locally with a simple static server such as `python -m http.server`
- verify task creation, editing, deletion, completion toggling, filtering, and note creation work as expected
- verify the theme toggle persists correctly across reloads
- confirm localStorage-backed data remains available after refresh
- if a feature is added or modified, test the primary path manually rather than inventing a build system

## Working rules for agents
- Prefer the smallest change that solves the request completely.
- Avoid unrelated cleanup or large refactors.
- Keep the app’s single-file structure intact.
- Do not add dependencies or project scaffolding without a clear requirement.
- Update documentation only if the feature or behavior changes in a user-visible way.

## Expected final output
When working on this repo, final output should focus on the actual behavior of the app in `task.html`, not on assumptions about a backend or framework that does not exist here.
