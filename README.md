# Soul Protocol

**Portable identity, memory, and context for AI assistants.**

Your relationship with an AI assistant shouldn't be locked to a single model, company, or cloud. Soul Protocol is an open specification for creating portable AI identities — a way to define who an assistant is, what it remembers, and how it behaves, independent of any specific LLM provider.

> Change the brain. Keep the soul.

## Why?

Today, AI assistants are bound to a provider, stateless, disposable, and amnesic by design. You can switch models, but you lose the soul.

**Identity + Memory + Context should belong to the user, not the model.**

## What Is a Soul?

A Soul is a portable container composed of simple, human-readable files:

| File | Purpose |
|------|---------|
| `identity.md` | Who the assistant is — name, personality, tone, values, role, boundaries |
| `user.md` | Who the assistant is for — preferences, communication style, expectations |
| `memory.md` | What the assistant remembers — long-term facts, learned preferences, important events |
| `context.md` | How the assistant thinks — system rules, reasoning preferences, safety constraints |

## Lifecycle

1. **Create** — Write your soul files
2. **Attach** — Inject the soul as system/context input into any compatible LLM
3. **Interact** — The assistant behaves according to its soul
4. **Evolve** — Memories are curated and written back; identity remains stable
5. **Reincarnate** — Switch model, provider, or device. Same soul, new body

## Design Principles

- **Portable** — Works across local, cloud, and future models. No provider lock-in.
- **Human-readable** — Markdown by default. Plain text. Git-friendly. Auditable.
- **User-owned** — Stored locally. Encrypted if synced. Never implicitly shared.
- **Model-agnostic** — Defines no model, no UI, no runtime. Just identity continuity.

## What This Is Not

Soul Protocol is **not** a chatbot framework, a memory database, an agent platform, or a prompt marketplace. It's lower-level: **a standard, not a product.**

## Long-Term Vision

Models will come and go. Your AI shouldn't reset every time.

Soul Protocol enables lifelong personal assistants, local-first AI companions, AI identities that outlive models, and true personal AI sovereignty.

## Status

This project is in its early stages — a philosophy, a file structure, a direction. The goal is to evolve it in the open.

## Contributing

This project welcomes thinkers, builders, designers, skeptics, and minimalists. If you care about local AI, personal autonomy, or long-term AI relationships — you're already part of the conversation.

## License

Open by default. Forever.

---

*We don't need artificial general intelligence yet. We need artificial continuity.*
