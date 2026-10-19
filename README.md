# flowstash-observability-skill

Agent skill for investigating managed Flowstash runs, logs, spans, exchanges, record provenance, stored payloads, and builds through the read-only Flowstash CLI.

## Skills

| Name | Description |
|------|-------------|
| `flowstash-observability` | Use for execution evidence and build failures — runs, spans, logs, data exchanges, record provenance, stored payloads, builds — not current application record state or local execution |

## Installation

```bash

# From GitHub (after publishing)
npx skills add flowstash/flowstash-observability-skill -s flowstash-observability

# Targeting a specific agent
npx skills add flowstash/flowstash-observability-skill -s flowstash-observability -a claude-code

# From a local path
npx skills add ./flowstash-observability-skill -s flowstash-observability

```

## Note
To use this skill the `flowstash` CLI needs to be installed, and either an existing keyring developer login or a `FLOWSTASH_API_KEY` with `observability:read` scope needs to be configured.

## Usage

Once installed, the skill activates when you ask the agent to:

- `"why did this run fail"`
- `"find failed exchanges for this pipeline"`
- `"show me the logs for this run"`
- `"what happened to this record"`
- `"check the last build"`

The agent will use `flowstash context`, `flowstash obs ...`, and `flowstash builds ...` to retrieve read-only execution evidence, preferring `--json` and one focused resource at a time.

## Requirements

- [`flowstash`](https://www.flowstash.dev) CLI installed and on `PATH`
- A linked workspace, or an explicit `--project PROJECT_ID`
- Read access (`observability:read` scope) to the managed environment being inspected
