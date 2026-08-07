---
name: observability-feature-integration
description: Workflow command scaffold for observability-feature-integration in SurfSense.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /observability-feature-integration

Use this workflow when working on **observability-feature-integration** in `SurfSense`.

## Goal

Adds or extends observability/telemetry features across backend services, including OpenTelemetry integration, metrics, and error/event helpers.

## Common Files

- `docker/docker-compose*.yml`
- `docker/otel-collector/config.yaml`
- `surfsense_backend/.env.example`
- `surfsense_backend/app/observability/**`
- `surfsense_backend/app/tasks/**`
- `surfsense_backend/app/agents/**/middleware/**`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Add or update observability-related config (e.g., docker-compose, .env, otel-collector).
- Implement new metrics, tracing, or telemetry helpers in observability modules.
- Instrument backend services, pipelines, or middleware to emit telemetry.
- Add or update unit tests for observability features.
- Update or add documentation for observability.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.