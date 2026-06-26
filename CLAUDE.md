# Prototype guide for Claude Code

Real-time AI-powered X-wing fleet monitoring dashboard with anomaly detection and predictive maintenance alerts.

The source PRD / Epic: https://bytecubed.atlassian.net/browse/AL-394

## How this repo works

Each ticket for this prototype is filed as a GitHub issue. When an issue is opened,
the workflow in `.github/workflows/claude.yml` runs you (Claude Code) to implement it
and open a pull request. Work one issue at a time and keep every change runnable.

## Tech stack & conventions

Stack: Python backend (FastAPI) with WebSocket support, SQLite for state, scikit-learn for ML anomaly detection, React frontend with real-time updates. Run: `pip install -r requirements.txt && python app.py` for backend (runs on :8000), then `npm start` in frontend/ for React dev server. Use mock X-wing telemetry data with realistic patterns. Focus on a working end-to-end slice: fleet status display → individual aircraft metrics → anomaly detection alerts → predictive maintenance warnings. Keep ML models simple but functional (isolation forest for anomalies, simple linear regression for maintenance forecasting). Prioritize real-time WebSocket updates and responsive UI over production-grade scalability. All data flows: telemetry ingestion → validation → storage → ML processing → WebSocket broadcast to connected clients.

## Working agreement

- Build the simplest thing that satisfies the issue's acceptance criteria — this is a
  prototype, not production. Favor a working end-to-end slice over breadth.
- Keep the project runnable at every step. Document any new setup/run command in the
  README under a "Running" section.
- Open one pull request per issue and reference the issue with "Closes #<number>".
- Don't introduce secrets or external services that require credentials the repo
  doesn't have.
