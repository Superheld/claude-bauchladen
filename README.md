# Claude Bauchladen

> A curated marketplace of Claude Code plugins.

## Add to Claude Code

```bash
/plugin marketplace add Superheld/claude-bauchladen
```

## Available Plugins

### [`agnz`](https://github.com/Superheld/cc-plugin-agnz) — Sandboxed Local-Model Agent

Exposes a locally-hosted LLM (LM Studio, Ollama, any OpenAI-compatible endpoint) as a sandboxed sub-agent. Parent Claude orchestrates; the sub-agent does the heavy file work — keeping your context window small.

**Install:** `/plugin install agnz@claude-bauchladen`

**What you get:**

| Component | Description |
|---|---|
| MCP server | 6 `agent_*` tools to start, message, pause, approve, and stop local agent threads |
| `/agnz:setup` | Configure LM Studio / Ollama profiles (base URL, model, temperature) |
| `/agnz:threads` | Inspect and resume persistent agent threads |

**Requires:** LM Studio, Ollama, or any OpenAI-compatible server running locally.

---

### [`stancl`](https://github.com/Superheld/cc-plugin-stancl) — Skills for the stancl Ecosystem

Skills for three Laravel packages by [stancl](https://github.com/stancl): tenancy, jobpipeline, and virtualcolumn. Claude loads the relevant skill automatically when you work with these packages.

**Install:** `/plugin install stancl@claude-bauchladen`

**What you get:**

| Skill | Activates when… |
|---|---|
| `tenancy` | Setting up multi-tenancy, scoping models, configuring bootstrappers, writing tenant-aware tests |
| `jobpipeline` | Chaining jobs as event listeners via `JobPipeline::make()` |
| `virtualcolumn` | Storing schemaless attributes in a JSON column on Eloquent models |

**Requires:** A Laravel project with the relevant `stancl/*` packages.

---

### [`ddd`](https://github.com/Superheld/cc-plugin-ddd) — Domain-Driven Design Guardrail

A skill that teaches Claude to apply Domain-Driven Design rigorously and pushes back when patterns are misapplied or terminology drifts. Based on Eric Evans' *Domain-Driven Design* and the 2015 *DDD Reference*.

**Install:** `/plugin install ddd@claude-bauchladen`

**What you get:**

| Skill | Activates when… |
|---|---|
| `ddd` | The conversation touches domain modeling, bounded contexts, aggregates, entities, value objects, services, repositories, context mapping, or any non-trivial business-logic design — even if "DDD" is not mentioned explicitly |

**Requires:** Nothing — language-agnostic.

---

## Install Everything

```bash
/plugin marketplace add Superheld/claude-bauchladen
/plugin install agnz@claude-bauchladen
/plugin install stancl@claude-bauchladen
/plugin install ddd@claude-bauchladen
```
