# Soul Protocol

**An open specification for portable AI identity.**

Soul Protocol defines a structured, human-readable system that decouples who an assistant is, what it knows, and how it reasons from any specific model or provider. Identity, memory, and context belong to the user — not the model.

> Change the brain. Keep the soul.

## The Problem

The relationship between a user and an AI assistant is defined entirely by the provider. Context is ephemeral. Memory is proprietary or absent. When you switch models, you start from zero. There is no standard mechanism to carry identity, preferences, or accumulated knowledge across systems.

Soul Protocol proposes a concrete solution: decouple identity from the model. Define it as a portable, versionable, user-owned structure that any LLM can interpret.

## Architecture

A soul is a set of interconnected Markdown files orchestrated by an index — `soul-protocol.md` — that instructs the LLM on how to read, interpret, and maintain each component. The system is alive: the model doesn't just read the soul, it maintains it.

```
soul-protocol.md          ← Index: entry point and orchestrator
├── identity.md            ← Who the assistant is
├── user.md                ← Who the assistant is for
├── memory.md              ← What the assistant remembers
└── context.md             ← How the assistant thinks and acts
```

### `soul-protocol.md` — The orchestrator

The index file. References every other soul file and contains instructions for the LLM: how to interpret each component, when and how to update memory, how to preserve identity across sessions, and the rules for evolving the soul over time.

### `identity.md` — Identity

Name, personality, tone, values, role, and boundaries. The stable core — changes rarely and only with explicit intent.

### `user.md` — User profile

Preferences, communication style, language, timezone, expectations. Defines the relationship — not the assistant alone, but the bond between user and assistant.

### `memory.md` — Memory

Long-term semantic memories: learned facts, preferences, important events. Curated by the orchestrator's rules — not raw chat logs, but distilled, structured recollections that persist across sessions and models.

### `context.md` — Context

System rules, reasoning preferences, tool usage philosophy, safety constraints. The operating logic — how the assistant approaches problems, what it avoids, and how it balances autonomy with user control.

## Design Principles

- **Portable** — Works across local, cloud, and future models. No provider lock-in.
- **Human-readable** — Markdown by default. Plain text. Git-friendly. Auditable.
- **User-owned** — Stored locally. Encrypted if synced. Never implicitly shared.
- **Model-agnostic** — Defines no model, no UI, no runtime. Just identity continuity.

## Ecosystem

Soul Protocol is a specification, not a product. Because the format is open, any tool, client, or platform can read, write, and sync a soul.

- **CLI (roadmap)** — A command-line tool to create, edit, and manage soul files. Attach your soul to any supported LLM from the terminal.
- **Third-party integrations** — Chat interfaces, IDE extensions, mobile apps, or automation platforms — any system that speaks the protocol can use your synced soul.
- **User ownership** — Souls are stored locally by default. Sync is optional and encrypted. The user controls what the assistant knows, what it forgets, and who has access.

## Status

This project is in its earliest stage: a specification draft, a file structure, and a direction. The protocol, the CLI, and the ecosystem are being designed and built publicly. Contributions, critique, and ideas are welcome.

## Open OS

Soul Protocol is part of the [Open OS](https://www.open-os.com) initiative — an effort to develop and promote open, interoperable technologies for AI. The goal is to ensure that the tools we build to relate to machines remain transparent, portable, and owned by the people who use them.

## License

MIT
