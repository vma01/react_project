# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

`react-essentials-start` — a small React 19 + Vite learning project demonstrating core concepts (Components, JSX, Props, State). No test framework, linter, or TypeScript is configured.

## Commands

- `npm run dev` — start the Vite dev server
- `npm run build` — production build to `dist/`
- `npm run preview` — serve the production build locally

There is no `test` or `lint` script; do not invent one.

## Architecture

- `src/index.jsx` is the entrypoint. It mounts `<App />` into `#root` (defined in the root `index.html`) using `ReactDOM.createRoot`.
- `src/App.jsx` composes the page: a `Header` plus a `Core Concepts` section that maps over data from `src/data.js`.
- `src/data.js` is the single source for the `CORE_CONCEPTS` array. Each entry imports its image from `src/assets/*.png` — so image references flow through this module rather than being wired in components directly.
- `src/components/` holds presentational components. `Header.jsx` picks a random adjective on each render from a hardcoded list.
- Styling is a single global stylesheet (`src/index.css`) imported once from `index.jsx`.

## Conventions

- Components are `.jsx` files using default exports (see `Header.jsx`); `App.jsx` also default-exports.
- Prefer prop-spreading from `CORE_CONCEPTS` entries (`<CoreConcept {...CORE_CONCEPTS[i]} />`) — the object shape is designed to match the component's props.
