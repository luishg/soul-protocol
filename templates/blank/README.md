# Soul Protocol — Blank Template

This directory contains a complete, empty soul ready to be customized. It is the starting point for creating a new AI identity using the Soul Protocol specification.

## What is this?

A soul is a set of 6 Markdown files that together define a portable AI identity — who the assistant is, who it serves, what it remembers, how it operates, and what it values. These files are injected into an LLM's context at the start of each session, allowing the same identity to persist across sessions, models, and providers.

The protocol is **capability-aware**: it adapts to both chat-only LLMs (stateless mode — the assistant proposes file updates for the user to apply) and full agent runtimes (agent mode — the assistant applies updates directly). The operating mode is determined by the capabilities declared in `system.md`.

## Files

| File | Purpose | What to do |
|---|---|---|
| `soul-protocol.md` | The orchestrator. Contains all instructions the LLM needs to use the soul. | **Do not modify.** This file is the protocol itself. |
| `identity.md` | Who the assistant is: name, personality, voice, values, boundaries. | Fill in each section to define the persona. |
| `user.md` | Who the user is: profile, preferences, communication style, goals. | Fill in your information or let the assistant learn it over time. |
| `memory.md` | Persistent memory: facts, events, decisions, reflections. | Starts empty. The assistant populates it through conversation. |
| `system.md` | Runtime contract: capabilities, environment, tool policy, session model, behavioral rules. | Declare capabilities and add the rules you want the assistant to follow. |
| `soul.md` | The philosophical core: values, purpose, continuity, identity. | Define the essence of who the assistant chooses to be. Optional for chatbots. |

## Getting Started

1. **Copy this directory** to your working location:
   ```
   cp -r templates/blank/ my-soul/
   ```

2. **Fill in `identity.md`** first. Give the assistant a name, personality, and voice. Be specific — concrete behavioral descriptions produce better results than vague adjectives.

3. **Fill in `soul.md`**. Define the core values and purpose. Keep it short and operational — commitments, not prose. This file is optional for simple chatbots but recommended for companions and required for agents.

4. **Fill in `user.md`** with your profile, or leave it minimal and let the assistant learn about you through conversation.

5. **Configure `system.md`**. Declare your environment's capabilities (can the assistant write files? call tools? send messages?) and add behavioral rules, formatting defaults, and safety constraints. The capabilities section determines whether the assistant operates in stateless or agent mode.

6. **Leave `memory.md` as-is.** It starts empty and grows through interaction. Working Memory entries are always loaded; Archive entries are loaded only when relevant.

7. **Do not modify `soul-protocol.md`.** It contains the instructions the LLM needs to use all other files correctly.

## How it works

When an LLM receives these files as context, `soul-protocol.md` instructs it to:

1. Read and internalize each file in a specific order.
2. Apply identity, values, and behavioral rules from the first message onward.
3. Detect its operating mode from the capabilities declared in `system.md`.
4. Update files using a structured update envelope — applied directly in agent mode, emitted for review in stateless mode.
5. Follow token-budget compaction rules to keep Working Memory manageable.
6. Respect a seven-level priority hierarchy when instructions conflict.
7. Evolve the soul over time with user consent.

## Design principles

- **Portable** — Plain Markdown. Works with any LLM that accepts text context.
- **Human-readable** — Every file is readable and editable by a human with a text editor.
- **Git-friendly** — The entire soul can be versioned, diffed, forked, and restored.
- **User-owned** — Stored locally. The user controls what the assistant knows and remembers.
- **Model-agnostic** — No runtime, no API, no provider dependency. Just files.
- **Capability-aware** — Works in chat-only LLMs and full agent runtimes alike.

## Learn more

- [Soul Protocol](https://soul-protocol.com) — Project homepage and specification.
- [GitHub](https://github.com/luishg/soul-protocol) — Source repository.
