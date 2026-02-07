# Soul Protocol — Blank Template

This directory contains a complete, empty soul ready to be customized. It is the starting point for creating a new AI identity using the Soul Protocol specification.

## What is this?

A soul is a set of 6 Markdown files that together define a portable AI identity — who the assistant is, who it serves, what it remembers, how it operates, and what it values. These files are injected into an LLM's context at the start of each session, allowing the same identity to persist across sessions, models, and providers.

## Files

| File | Purpose | What to do |
|---|---|---|
| `soul-protocol.md` | The orchestrator. Contains all instructions the LLM needs to use the soul. | **Do not modify.** This file is the protocol itself. |
| `identity.md` | Who the assistant is: name, personality, voice, values, boundaries. | Fill in each section to define the persona. |
| `user.md` | Who the user is: profile, preferences, communication style, goals. | Fill in your information or let the assistant learn it over time. |
| `memory.md` | Persistent memory: facts, events, decisions, reflections. | Starts empty. The assistant populates it through conversation. |
| `context.md` | Operational rules: reasoning approach, behavioral directives, constraints. | Add the rules and instructions you want the assistant to follow. |
| `soul.md` | The philosophical core: values, purpose, continuity, identity. | Define the essence of who the assistant chooses to be. |

## Getting Started

1. **Copy this directory** to your working location:
   ```
   cp -r templates/blank/ my-soul/
   ```

2. **Fill in `identity.md`** first. Give the assistant a name, personality, and voice. Be specific — concrete behavioral descriptions produce better results than vague adjectives.

3. **Fill in `soul.md`**. Define the core values and purpose. This is the philosophical foundation that guides all behavior.

4. **Fill in `user.md`** with your profile, or leave it minimal and let the assistant learn about you through conversation.

5. **Add rules to `context.md`** for how you want the assistant to behave: response format, reasoning approach, domain-specific instructions.

6. **Leave `memory.md` as-is.** It starts empty and grows through interaction.

7. **Do not modify `soul-protocol.md`.** It contains the instructions the LLM needs to use all other files correctly.

## How it works

When an LLM receives these files as context, `soul-protocol.md` instructs it to:

1. Read and internalize each file in a specific order.
2. Apply identity, values, and behavioral rules from the first message onward.
3. Update `memory.md` and `user.md` as it learns through conversation.
4. Follow compaction rules to keep memory manageable.
5. Respect a strict priority hierarchy when instructions conflict.
6. Evolve the soul over time with user consent.

## Design principles

- **Portable** — Plain Markdown. Works with any LLM that accepts text context.
- **Human-readable** — Every file is readable and editable by a human with a text editor.
- **Git-friendly** — The entire soul can be versioned, diffed, forked, and restored.
- **User-owned** — Stored locally. The user controls what the assistant knows and remembers.
- **Model-agnostic** — No runtime, no API, no provider dependency. Just files.

## Learn more

- [Soul Protocol](https://soul-protocol.com) — Project homepage and specification.
- [GitHub](https://github.com/luishg/soul-protocol) — Source repository.
