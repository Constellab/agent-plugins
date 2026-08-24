# Constellab plugins for Claude Code

Add the marketplace once, then install the plugins you need:

    /plugin marketplace add Constellab/agent-plugins
    /plugin install space@constellab
    /plugin install community@constellab

## Plugins

### `space` — Constellab Space

Works with your Constellab Spaces over the Space API's MCP tools. The `diagnose-lab-startup`
skill diagnoses a cloud data lab that fails to start: it walks the six layers a lab start
passes through and names the one it is blocked at, so you don't read logs from layers that
never ran.

Configuration: **Space API URL** — the base URL of your Constellab Space API, without a
trailing slash. Keep the default unless you use a dedicated or on-premise instance.

### `community` — Constellab community documentation

Searches and reads the Constellab community documentation, over the Community API's MCP
tools. The `search-community-doc` skill covers how the search actually matches (one literal
substring, no ranking) and how to tell a real hit from a match inside the page markup.

Configuration: **Community API URL** — defaults to `https://api.constellab.community`. Keep
the default unless you use a dedicated or on-premise instance.

## Repository layout

    .claude-plugin/marketplace.json   the marketplace manifest — every plugin is listed here
    plugins/<name>/.claude-plugin/plugin.json   plugin manifest: MCP servers and user config
    plugins/<name>/skills/<skill>/SKILL.md      the skills that drive those MCP tools

Adding a plugin means creating `plugins/<name>/` with its manifest and skills, then adding an
entry to `plugins` in `marketplace.json` with a `./`-prefixed `source` path.
