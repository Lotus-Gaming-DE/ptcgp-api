# Changelog

## [Unreleased]
### Added
- Asynchronous image checks using `httpx.AsyncClient` with TTL cache.
- Error logging for failed image requests.
- Application refactored into `app` package with modular routers.
- Data loading moved to `app/data.py`.
- Configurable logging with `LOG_LEVEL` and startup/deck creation logs.
- CORS origins configurable via `ALLOW_ORIGINS` environment variable.
- Optional API key authentication for write operations using the `API_KEY`
  environment variable and `X-API-Key` header.
- Filter indexes for sets, types and rarity for faster `/cards` queries.
- Optional profiling via `PROFILE_FILTERS` environment variable.
- Benchmark test suite in `tests/performance` (requires `pytest-benchmark`).
- `Language` and `VoteDirection` enums for better validation.
- `DATA_DIR` environment variable to configure the data path.
- Global exception handler that logs unexpected errors.
- GitHub Actions workflow with `ruff` linting and tests.
- `IMAGE_TIMEOUT` environment variable for configurable image request timeout.
- Coverage configuration and SBOM generation in CI.
- `scripts/summary.py` CLI for Datenübersicht.
- Packaging metadata in `pyproject.toml` allowing `pip install -e .`.
- Dependency caching and Snyk scanning in CI workflow.
- Snyk scan skipped on forked PRs when token is unavailable.
- CI: Skip Snyk test in forked PRs to prevent missing-secret auth errors.
- `pytest.ini` enabling `pytest-timeout`.
- Package versions pinned in `requirements*.txt` for reproducible installs.
- Coverage reporting via `pytest-cov` in CI.
- Pre-commit now runs Black, Flake8, Ruff and pip-audit with cached hooks.
- Dependabot konfiguriert automatische Updates für Python-Pakete und
  GitHub Actions.

### Changed
- Endpoints now await image URL resolution.
- Image URL checks cached for 24 hours to improve performance.
- CI workflow uses `ruff check` for compatibility.
- Dependabot aktualisiert Abhängigkeiten nun täglich und jeder PR läuft durch die komplette CI-Pipeline.
- Async tests share a session-scoped event loop.
- Startup instructions now reference `ptcgp_api:app` and document Railway command.

- Structured JSON logging using structlog with file rotation.
- Logs now rotate hourly to `logs/runtime-YYYY-MM-DD-HH.json`.
- CI uses `npx railway` with service and project IDs for log streaming.
- CI now runs pre-commit and pip-audit for security scanning.

### Removed
- Manual `sys.path` adjustments in tests; project installs as editable package.
- Application startup creates a single AsyncClient and closes it on shutdown.
- All user-facing errortexte sind jetzt auf Deutsch.
- Repository moved to src/ layout.
- Example environment file and MIT license added.
