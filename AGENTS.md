# 3C Portfolio Manager project guidance

Electron + React/Redux + TypeScript application for a 3Commas portfolio.
Read `README.md` for development setup and `FORMULA_DESCRIPTIONS.md` for metrics.

- `src/main/` owns Electron lifecycle, 3Commas API, configuration and SQLite.
  `src/preload.ts` owns the preload boundary; `src/app/` owns the UI/state;
  `src/utils/` owns shared calculations. Preserve these boundaries.
- `package.json`, `package-lock.json` and the webpack configuration own build
  commands. Build: `npm run build`. README's development setup uses
  `npm i --include=dev`, `npm run webpack`, `npm run rebuild`, then `npm run dev`.
  Native SQLite rebuilding may depend on the active Electron/platform version.
- No test or lint script is declared in the current package manifest. Do not
  invent `npm test`; use focused checks appropriate to changed code and report
  missing coverage. Packaging and opening the app are separate from a build.
- Preserve API credentials, account data, SQLite stores and existing settings.
  Use fixtures for verification; do not change live bots/deals or make trading
  requests while developing. Apply `calculation-checks` to substantive metric
  changes and use the actual client's permitted tools.
