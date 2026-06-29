# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains a starter project for an expense tracker application built with React and Vite. The project is intentionally designed with bugs, poor UI, and messy code as part of a learning course (see README for details). The actual source code lives in the `expense-tracker-starter/` directory.

## Development Commands

All commands are run from the repository root. For convenience, you can change into the project directory (`cd expense-tracker-starter`) or run commands with the path prefix.

### Install Dependencies
```bash
npm install
```
(Equivalent to `cd expense-tracker-starter && npm install`)

### Start Development Server
```bash
npm run dev
```
Starts the Vite development server at http://localhost:5173 with hot module replacement.

### Build for Production
```bash
npm run build
```
Produces optimized static assets in `expense-tracker-starter/dist/`.

### Preview Production Build
```bash
npm run preview
```
Serves the built application locally for preview.

### Linting
```bash
npm run lint
```
Runs ESLint across the source files to check for code quality issues.

## Project Structure

```
expense-tracker-starter/
├─ src/
│  ├─ main.jsx          # Entry point – renders <App /> into the DOM
│  ├─ App.jsx           # Main application component – state, forms, transaction list
│  ├─ App.css           # Component-specific styles
│  ├─ index.css         # Global styles
│  └─ assets/           # Static assets (logos, icons)
├─ public/
│  └─ vite.svg          # Vite logo
├─ index.html           # HTML template with root div
├─ vite.config.js       # Vite configuration (React plugin)
├─ package.json         # Scripts and dependencies
└─ README.md            # Project overview and getting started
```

### Key Files

- **src/main.jsx** – Bootstrap React application.
- **src/App.jsx** – Contains all application state (transactions, form inputs, filters) and UI rendering.
- **src/App.css** – Styles for the App component.
- **src/index.css** – Global CSS resets and base styles.
- **vite.config.js** – Minimal Vite setup with React plugin.

## Architecture Highlights

- **State Management**: All state is managed locally within `App.jsx` using React's `useState` hook (transactions, form fields, filters).
- **Data Flow**: Transactions are stored as an array of objects with `id`, `description`, `amount`, `type`, `category`, and `date`. Derived values (total income, expenses, balance) are computed via `Array.prototype.filter` and `reduce`.
- **Event Handling**: Form submission (`handleSubmit`) prevents default, validates input, creates a new transaction object with a timestamp‑based ID, and appends it to the transactions list.
- **Filtering**: Two `<select>` elements allow filtering by transaction type (all/income/expense) and category.
- **Styling**: Simple CSS classes; amounts are colored via `.income-amount` (green) and `.expense-amount` (red) classes.
- **No External State Libraries**: The app does not use Redux, Context, or other state‑management libraries—everything lives in `App.jsx`.
- **No Backend**: Data is purely client‑side; page reload resets the transaction list to the hard‑coded initial state.

## Testing

The starter project does not include a test framework. If you wish to add tests, consider installing Vitest (compatible with Vite) or Jest and configuring them accordingly. No test scripts are defined in `package.json`.

## Linting & Code Quality

- ESLint is configured via `eslint.config.js` (inherits from `eslint:recommended` and plugin rules).
- React‑specific plugins are installed: `eslint-plugin-react-hooks`, `eslint-plugin-react-refresh`.
- To fix lint‑auto‑correctable issues, you can run `npm run lint -- --fix` (requires modifying the lint script or using ESLint directly).

## Common Tasks

- **Add a feature**: Modify `App.jsx` (state, handlers, JSX) and optionally `App.css` for styling.
- **Adjust styling**: Edit `App.css` or `index.css`.
- **Update dependencies**: Run `npm install <package>` or `npm update`.
- **Debug**: Use React DevTools in the browser; the app runs at http://localhost:5173 when `npm run dev` is active.

## Notes

- The project uses Vite as the build tool; the development server is fast and supports HMR.
- The `vite` version in `package.json` is somewhat old (^7.2.4); consider updating if needed for newer features.
- This is a learning starter—expect intentional issues that are addressed in the accompanying course.
