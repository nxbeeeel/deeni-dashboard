# deeni-dashboard

Auto-updated operations dashboard for **deen.in**. Refreshed every 30 min
by a GitHub Actions workflow in the private `deeni` repo. Do not edit by
hand — any local changes will be overwritten on the next push from the
workflow.

- Live URL: enable GitHub Pages on this repo's `main` branch (root), then
  visit `https://<your-github-username>.github.io/deeni-dashboard/`.
- Source: `.dashboard/` directory in the private `mnabeelca/deenin` repo.
- Plan: see `DASHBOARD_PLAN.md` in the private repo.

## Files

| File         | Purpose                                                       |
|--------------|---------------------------------------------------------------|
| `index.html` | The dashboard. Reads `state.json` on render.                  |
| `state.json` | Latest pulled state (Sentry / PostHog / GitHub / CDN / EAS).  |
| `STATUS.md`  | Human-readable mirror of `state.json`.                        |
| `.nojekyll`  | Disables Jekyll on Pages so files serve verbatim.             |
