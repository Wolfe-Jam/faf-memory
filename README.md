# FAF Memory — Permanent Memory Layer for Claude Code

Your Claude doesn't remember yesterday. **`.fafm` is the file that fixes that** — IANA-registered, cross-vendor, offline-first. Open the same memory in [`grok-faf-voice`](https://pypi.org/project/grok-faf-voice/) — same facts, both directions tested.

[![IANA](https://img.shields.io/badge/IANA-application%2Fvnd.fafm%2Byaml-FF6B35)](https://www.iana.org/assignments/media-types/application/vnd.fafm+yaml)
[![Zenodo DOI](https://img.shields.io/badge/DOI-10.5281%2Fzenodo.20348942-00D4D4)](https://doi.org/10.5281/zenodo.20348942)
[![Receipt](https://img.shields.io/badge/receipt-412×_faster_vs_grep-FF6B35)](https://github.com/Wolfe-Jam/faf-memory-proof)
[![MIT](https://img.shields.io/badge/license-MIT-green)](LICENSE)

## Install

```
/plugin install faf-memory
```

That's it. The plugin wires the [`faf-memory-mcp`](https://github.com/Wolfe-Jam/faf-memory-mcp) server into Claude Code via `uvx`, exposing five tools.

## What you get

| Tool | What it does |
|---|---|
| `etch(text, id?, type?, priority?, tags?)` | Write a durable fact. O(1) dedup by `id`. |
| `recall(query?, type?, tags?, min_priority?, limit?)` | Filter (substring + type + tags + priority floor), rank by priority then recency. |
| `list_facts()` | Enumerate all facts (no filter, no rank). |
| `save_soul(path?)` | Persist to a `.fafm` file. |
| `load_soul(path?)` | Load a `.fafm` from disk. |

Memory lives in **`.fafm`** — plain YAML, IANA-registered. Diffable like code. Portable to any tool that reads the format.

## How to know it's working

- Your agent doesn't ask *"what is this project?"* twice in the same week.
- `recall("X")` surfaces what you etched **last** session, not just the current one.
- The `.fafm` file grows readably — open it, diff it, share it.
- Open the same file in [`grok-faf-voice`](https://pypi.org/project/grok-faf-voice/) — same facts. Cross-vendor proven.

## Complementary, not competing

`.fafm` is the **structured source**. It sits alongside (not against) the rest of Anthropic's memory stack:

- **Anthropic `memory_20250818`** tool contract — speakable via the proprietary [`fafm-engine`](https://github.com/Wolfe-Jam/fafm-engine) (enterprise lane)
- **Anthropic `claude-md-management`** — maintains the rendered `CLAUDE.md`; `.fafm` is its memory sibling
- **Community `remember`** — conversational daily logs; `.fafm` is its structured peer

PML is the **standard underneath** — IANA-registered, cross-vendor, offline-first.

## The receipt

**400+× faster type-filter queries vs `grep`** on a real 492-file AI memory corpus. Falsifiable methodology + scripts + sanitized pilot at **[Wolfe-Jam/faf-memory-proof](https://github.com/Wolfe-Jam/faf-memory-proof)** — reproduce in 30 seconds with one paste.

## Tradeoff note

Biases toward **deterministic recall** (substring + type + tags + priority + recency) over **semantic recall**. For semantic / LLM smart-merge, see hosted namepoints in [`claude-fafm-sdk`](https://pypi.org/project/claude-fafm-sdk/). Offline-first ≠ offline-only.

## The FAF cluster

- **This plugin** — `faf-memory` — wraps `faf-memory-mcp`
- [`Wolfe-Jam/faf-memory-mcp`](https://github.com/Wolfe-Jam/faf-memory-mcp) — the MCP server
- [`Wolfe-Jam/faf-memory-proof`](https://github.com/Wolfe-Jam/faf-memory-proof) — the falsifiable receipt
- [`Wolfe-Jam/faf-plugin`](https://github.com/Wolfe-Jam/faf-plugin) — sibling: `.faf` context (FCL)
- [`claude-fafm-sdk`](https://pypi.org/project/claude-fafm-sdk/) — the open Python SDK
- [`Wolfe-Jam/faf`](https://github.com/Wolfe-Jam/faf) — the format spec + IANA registration

## License

MIT.
