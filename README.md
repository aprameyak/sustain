# Sustain

A simple health log for open source projects. Maintainers record response time, issue backlog, and contributor count for each project, and the app flags the ones showing signs of burnout risk.

## Features

- Log a health check per project: average PR/issue response time, open issue backlog, active contributors, and last update date
- Each project is marked high or low burnout risk
- Risk rule is simple and visible: high if response time is over 14 days or the backlog is over 50 issues
- Entries are saved to a local JSON file

## Getting started

Requires Node.js.

```bash
npm install
npm start
```

Then open http://localhost:3011. `npm run dev` runs the same command.

## How it works

- `index.html` contains the form and the project list. It calls the API at `http://localhost:3011`.
- `server.js` is an Express app that serves the page and exposes:
  - `POST /api/projects` to save a health check.
  - `GET /api/projects` to return all entries with a computed `burnoutRisk` field.
- Data is written to `data.json`, created on first run and ignored by git.
- `utils.js` holds validation and file helpers that are not yet wired into `server.js`.

## Status

Prototype. All numbers are entered by hand; nothing is pulled from GitHub or any other service.

## License

MIT, see [LICENSE](LICENSE).
