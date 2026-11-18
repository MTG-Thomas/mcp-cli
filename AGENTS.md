# MCP CLI

This is the MTG operator-ready Bun/TypeScript fork of `mcp-cli`. Read [CONTRIBUTING.md](CONTRIBUTING.md) for required gates and [README.md](README.md) for configuration and command/output contracts. The entry point is `src/index.ts`; tests cover configuration, output, clients, errors, filtering, CLI behavior, and integration.

Install with `bun install --frozen-lockfile`. Before a PR run `bun run typecheck`, `bun run lint`, the exact unit-test list in CONTRIBUTING, `bun test --timeout 60000 tests/integration/`, and `bun run build:all`. `.github/workflows/ci.yml` is the matching gate; do not replace its explicit unit set with an unverified generic check. Report which platforms were compiled and which were actually executed.

Preserve stdout/stderr contracts, JSON tool results, schema discovery, server/tool filtering, stdio and HTTP support, and actionable errors. Inspect daemon connection ownership, idle shutdown, and cancellation when changing process behavior. Include Windows path, shell, process-spawning, and daemon IPC consequences in relevant changes. Keep upstream-useful fixes separate from fork-specific behavior.

MCP configurations can contain credentials and tools can mutate external systems. Use synthetic server fixtures for tests; do not commit real server tokens, customer data, or local-only configuration. Reading a tool schema does not authorize invoking its effects. Keep development checks independent of the operator's real MCP servers.

Update README, `SKILL.md`, or release notes when behavior changes. Releases are tag-driven from `main` via `.github/workflows/release.yml`; `./scripts/release.sh X.Y.Z` is for reviewed release scope after green CI and applicable authorization. Preserve Linux x64/ARM64, macOS x64/ARM64, Windows x64, and checksums artifact coverage.
