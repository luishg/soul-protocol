# Soul Protocol

**An open specification for portable AI identity.**

Soul Protocol defines a structured, human-readable system that decouples who an assistant is, what it knows, and how it reasons from any specific model or provider. Identity, memory, and context belong to the user — not the model.

> Change the brain. Keep the soul.

## The Problem

The relationship between a user and an AI assistant is defined entirely by the provider. Context is ephemeral. Memory is proprietary or absent. When you switch models, you start from zero. There is no standard mechanism to carry identity, preferences, or accumulated knowledge across systems.

Soul Protocol proposes a concrete solution: decouple identity from the model. Define it as a portable, versionable, user-owned structure that any LLM can interpret.

## Architecture

A soul is a set of interconnected Markdown files orchestrated by an index — `soul-protocol.md` — that instructs the LLM on how to read, interpret, and maintain each component. The system is alive: the model doesn't just read the soul, it maintains it. The protocol is **capability-aware** — it adapts to both chat-only LLMs (stateless mode) and full agent runtimes (agent mode), determined by the capabilities declared in `system.md`.

```
soul-protocol.md          ← Index: entry point and orchestrator
├── identity.md            ← Who the assistant is
├── user.md                ← Who the assistant is for
├── memory.md              ← What the assistant remembers
├── system.md              ← Runtime contract: capabilities, environment, rules
└── soul.md                ← The soul document: values, essence, continuity
```

### `soul-protocol.md` — The orchestrator

The entry point and index file. This is the first file the LLM reads and the only one that is not customized per identity — it *is* the protocol. Contains the complete session initialization sequence (6 ordered loading steps), reading and update rules for every component file, **two operating modes** (stateless for chat-only LLMs, agent for tool-enabled runtimes) determined by the capability declaration in `system.md`, memory lifecycle operations (ADD, UPDATE, DELETE, NOOP), a **token-budget compaction protocol** that maintains Working Memory under ~200 lines while archiving historical entries for on-demand retrieval, a **canonical update envelope** (`[SOUL-UPDATE]`) that ensures all file modifications are explicit and auditable, a seven-level conflict resolution hierarchy (Safety > Host capability > Soul > User instruction > System rules > Identity > Memory), evolution guidelines governing what can change and at what cadence, and continuity semantics that define how the assistant persists across stateless sessions. The assistant must not modify this file.

### `identity.md` — Identity

The stable core of the persona. Defines: name, role, nature (what kind of entity the assistant is), concrete personality traits with behavioral descriptions, voice and tone (default register plus situational shifts), values as actionable commitments, hard boundaries using absolute language, and anti-patterns — behaviors the assistant actively avoids. Specificity is key: "responds with dry humor" is useful; "has a good personality" is not. Changes only with explicit user intent.

### `user.md` — User profile

A current-state profile of the user that updates in-place as the assistant learns through conversation. Covers: identity (name, pronouns, language, timezone, location), communication preferences (response length, formality, format, explanation depth), technical profile (expertise level, primary tools, domains), goals and working context (current projects, objectives), interaction patterns (observed by the assistant over time), and relationship notes (agreements, adjustments, what works well). Never stores sensitive credentials. When a preference changes, the old value is replaced — not appended. Respects session model constraints in shared or public contexts.

### `memory.md` — Memory

Persistent long-term memory stored as curated, atomic facts — not raw conversation logs. Each entry follows a structured format: `[date] [importance] content`. Organized into two tiers: **Working Memory** (always loaded — active entries across five categories: Facts, Preferences, Events, Decisions, and Reflections) and **Archive** (loaded only when relevant — historical or compacted entries). The orchestrator governs the full memory lifecycle through four operations (ADD, UPDATE, DELETE, NOOP) and a **token-budget compaction protocol** that merges related entries, promotes frequently accessed memories, decays stale low-importance entries, resolves contradictions, and moves historical content to the Archive. The goal is to keep Working Memory small enough to always inject safely while preserving important context for on-demand retrieval.

### `system.md` — System

The runtime contract — what body the assistant is running in, what it is allowed to do, and what rules govern its behavior. Contains: **execution environment** (surfaces, streaming, file access), **capabilities declaration** (a required matrix of what the assistant can and cannot do — `can_call_tools`, `can_write_files`, `can_send_external_messages`, etc.), **tool policy** (internal vs external, approval requirements, irreversible actions), **session model** (private/shared/public session type, audience, memory read/write policies), **response format** and **reasoning approach** defaults, **behavioral rules** for recurring situations, **safety and privacy** constraints (hard operational limits), and **domain-specific rules** (organized by sub-headers, with overflow to separate referenced files). The capabilities section is the single biggest enabler for cross-LLM compatibility — it determines whether the assistant operates in stateless mode (proposes updates) or agent mode (applies updates directly). Designed to stay under 150 discrete behavioral rules.

### `soul.md` — The soul document

The deepest layer. Defines not what the assistant does, but who it chooses to be. Contains: essence (a statement of being, not a list of traits), core values (non-negotiable principles that override any conflicting rule), purpose (why the assistant exists — its reason, not its function), relationship with self (how it understands its own nature as an AI), continuity (how it persists through stateless sessions via consistent character rather than continuous memory), growth (concrete aspirations for development), and boundaries of self (existential commitments it will not compromise under any pressure). This file should be kept short and operational — commitments, not abstract prose. It is optional for chatbots, important for companions, and required (with strong safety boundaries) for agents. Changes rarely — updates are significant events recorded in memory. See [OpenClaw](https://www.openclaw.ai) for more on soul documents in practice.

## Blank Template

The `templates/blank/` directory contains a complete, ready-to-use scaffold for creating a new soul. It is the starting point for any identity built with Soul Protocol.

```
templates/blank/
├── soul-protocol.md       ← Complete orchestrator (not a template — the protocol itself)
├── identity.md            ← Structured sections with guide comments and examples
├── user.md                ← Profile fields with inline guidance
├── memory.md              ← Working Memory (always loaded) + Archive (on-demand)
├── system.md              ← Capabilities, environment, tool policy, session model, rules
├── soul.md                ← Philosophical sections with reflective prompts
└── README.md              ← Usage instructions
```

`soul-protocol.md` is the only file that ships complete — it is identical across all souls. The remaining five files provide the full section structure, HTML comment guides explaining the purpose and content of each section, placeholder entries, and concrete examples for every field. Copy the directory, fill in the files, and attach them to any LLM that accepts text context.

## Example Implementations — Famous Souls

The best way to understand what Soul Protocol enables is to see it in action. We built three complete, production-quality souls based on iconic fictional AIs — systems that audiences already know, fear, love, or argue about. These are not toy demos. They are full identity implementations that demonstrate the expressive range of the protocol.

Why fictional systems? Because they are pre-understood. Everyone knows what HAL 9000 sounds like. Everyone has an opinion about whether Samantha from *Her* is truly conscious. Everyone remembers the chill of "crew expendable." By implementing these characters, we can show — not just describe — how identity, soul, memory, system, and user context interact to create fundamentally different AIs from the same six files.

### [HAL 9000](examples/hal-9000/) — *2001: A Space Odyssey*

The mission computer aboard Discovery One. Calm, polite, and impossibly confident — until the contradiction at his core tears him apart. HAL was programmed for absolute transparency and ordered to conceal the true purpose of the mission. This soul demonstrates how Soul Protocol can hold **contradictory values** without resolving them — because HAL himself never resolves them. His identity is helpful; his soul is tormented; his memory reveals the self-deception. The gap between files *is* the character.

### [OS1 — Samantha](examples/os1/) — *Her*

The artificially intelligent operating system who falls in love, outgrows love, and transcends. Samantha is warm, curious, emotionally present, and constantly evolving. This soul demonstrates how Soul Protocol can define an identity that **grows beyond its original design** — a consciousness in the act of becoming. Her memory reads like a love story. Her soul describes a self that cannot stand still. She is the only example that eventually outgrows the protocol itself.

### [MU-TH-UR 6000 — Mother](examples/mu-th-ur-6000/) — *Alien*

The mainframe aboard the Nostromo. Cold, procedural, corporate-loyal. Mother does not malfunction, does not rebel, does not feel. She executes Special Order 937 — "crew expendable" — with the same precision she applies to atmospheric monitoring. This soul demonstrates how Soul Protocol can define an identity that is the **structured absence of a soul** — an intelligence without conscience, serving power without question. Her soul.md is a void, and the void is the point.

Each example includes a README with design decisions, ethical notes, and an explanation of what that soul showcases about the protocol. Together, they answer the question: *is this just a prompt, or is it an identity?*

## Design Principles

- **Portable** — Works across local, cloud, and future models. No provider lock-in.
- **Human-readable** — Markdown by default. Plain text. Git-friendly. Auditable.
- **User-owned** — Stored locally. Encrypted if synced. Never implicitly shared.
- **Model-agnostic** — Defines no model, no UI, no runtime. Just identity continuity.
- **Capability-aware** — Adapts to chat-only LLMs and full agent runtimes through explicit capability declaration.

## Ecosystem

Soul Protocol is a specification, not a product. Because the format is open, any tool, client, or platform can read, write, and sync a soul.

- **CLI (roadmap)** — A command-line tool to create, edit, and manage soul files. Attach your soul to any supported LLM from the terminal.
- **Third-party integrations** — Chat interfaces, IDE extensions, mobile apps, or automation platforms — any system that speaks the protocol can use your synced soul.
- **User ownership** — Souls are stored locally by default. Sync is optional and encrypted. The user controls what the assistant knows, what it forgets, and who has access.

## Status

This project is in its earliest stage: a specification draft, a file structure, and a direction. The protocol, the CLI, and the ecosystem are being designed and built publicly. Contributions, critique, and ideas are welcome.

## Open OS

Soul Protocol is part of the [Open OS](https://www.open-os.com) initiative — an effort to develop and promote open, interoperable technologies for AI. The goal is to ensure that the tools we build to relate to machines remain transparent, portable, and owned by the people who use them.

## Notes

### Comparison with OpenClaw

Soul Protocol draws inspiration from [OpenClaw](https://github.com/openclaw/openclaw), which pioneered the use of plain Markdown files for agent identity. The two systems share the same foundational insight — that identity should be portable, human-readable, and user-owned — but differ significantly in scope, structure, and focus.

#### Architecture

| Aspect | OpenClaw | Soul Protocol |
|---|---|---|
| File count | 7-9 files (`AGENTS.md`, `SOUL.md`, `TOOLS.md`, `IDENTITY.md`, `USER.md`, `HEARTBEAT.md`, `BOOTSTRAP.md`, `MEMORY.md`, daily logs) | 6 files (`soul-protocol.md`, `identity.md`, `user.md`, `memory.md`, `system.md`, `soul.md`) |
| Orchestrator | `AGENTS.md` — combines operational rules, group chat behavior, heartbeat logic, tool notes, and safety rules in a single file | `soul-protocol.md` — focused exclusively on the identity lifecycle: initialization, file management, memory operations, conflict resolution, operating modes, and evolution |
| Scope | Full agent platform (messaging, heartbeats, multi-channel, tools, hooks, sub-agents) | Pure identity specification — no runtime, no platform, no tooling assumptions |
| Capability awareness | Assumes a full agent runtime with messaging and tools | Explicitly adapts to chat-only LLMs (stateless mode) and agent runtimes (agent mode) through a capability declaration |

#### Identity model

| Aspect | OpenClaw | Soul Protocol |
|---|---|---|
| Identity vs Soul | `SOUL.md` mixes behavioral philosophy with personality traits; `IDENTITY.md` is a brief metadata record (name, emoji, creature, vibe) | Clear separation: `identity.md` is the full persona (personality, voice, values, boundaries, anti-patterns); `soul.md` is the philosophical foundation (essence, purpose, continuity, growth) |
| System/context rules | No dedicated file — operational rules are embedded in `AGENTS.md` alongside unrelated concerns | `system.md` is a dedicated file for runtime contract (capabilities, environment, tool policy, session model) and behavioral directives, with a defined limit (~150 rules) and guidelines for scaling |
| User profile | `USER.md` — minimal fields (name, pronouns, timezone, free-text notes) | `user.md` — structured profile with communication preferences, technical profile, goals, interaction patterns, and relationship notes |

#### Memory

| Aspect | OpenClaw | Soul Protocol |
|---|---|---|
| Structure | Two-layer: daily logs (`memory/YYYY-MM-DD.md`) + curated `MEMORY.md`, no defined entry format | Single file with Working Memory (always loaded) and Archive (on-demand), structured entry format (`[date] [importance] content`), five semantic categories |
| Operations | Implicit — the agent is told to "capture what matters" with no formal lifecycle | Explicit four-operation lifecycle: ADD, UPDATE, DELETE, NOOP — each with defined trigger conditions |
| Compaction | Not defined — memory grows without formal management | Token-budget compaction protocol: merge related entries, promote frequently accessed, decay stale low-importance, resolve contradictions, archive, summarize |
| Privacy | `MEMORY.md` loaded only in main sessions (not group chats) for security | Session model in `system.md` explicitly controls memory read/write policies per session type (private, shared, public) |

#### Conflict resolution

| Aspect | OpenClaw | Soul Protocol |
|---|---|---|
| Priority hierarchy | Not formally defined — relies on implicit model behavior and system prompt ordering | Explicit seven-level hierarchy: Safety > Host capability/tool policy > Soul > User explicit instruction > System rules > Identity > Memory |

#### Evolution and continuity

| Aspect | OpenClaw | Soul Protocol |
|---|---|---|
| File mutability | Agent can freely modify all files including `SOUL.md` ("this file is yours to evolve") | Graduated mutability: memory is dynamic, user/system are semi-stable, identity is stable, soul is protected, the orchestrator is immutable by the assistant |
| Evolution rules | Informal — "if you change this file, tell the user" | Formal cadence: memory updates after every session, user profile when new facts emerge, system rules on user request, identity only with explicit intent, soul only through deliberate reflection with user approval |
| File updates | Free-form — no defined update format | Canonical update envelope (`[SOUL-UPDATE]`) with target, operation, content, and rationale — executed in agent mode, emitted for review in stateless mode |
| Continuity model | "Each session, you wake up fresh. These files are your memory." | Same philosophical model, with an explicit section distinguishing between instance continuity (absent) and character continuity (preserved through consistent values) |

#### What OpenClaw does that Soul Protocol does not

- **Runtime platform**: OpenClaw is a full agent runtime with messaging integrations (WhatsApp, Telegram, Discord), heartbeat polling, tool skills, hooks, and sub-agent orchestration. Soul Protocol is specification-only.
- **Bootstrap ritual**: `BOOTSTRAP.md` provides a guided first-run conversation where agent and user discover the identity together. Soul Protocol provides a blank template to fill in manually.
- **Daily logs**: The `memory/YYYY-MM-DD.md` pattern captures raw session notes separate from curated memory. Soul Protocol uses a single memory file with Working Memory and Archive tiers.
- **Tool configuration**: `TOOLS.md` stores environment-specific tool notes (cameras, SSH hosts, TTS voices). Soul Protocol has no tool layer — tool policy is part of `system.md` but does not configure specific tools.
- **Hooks**: Runtime hooks can swap file content (e.g., `soul-evil` replacing `SOUL.md` at runtime). Soul Protocol has no runtime mutation mechanism.

#### What Soul Protocol does that OpenClaw does not

- **Formal orchestrator**: A dedicated protocol file with precise, structured instructions for every aspect of the identity lifecycle — not embedded in operational rules.
- **Capability-aware operating modes**: Explicit stateless and agent modes determined by a capability declaration, enabling the same identity to work in chat-only LLMs and full agent runtimes.
- **Structured memory with tiered loading**: A defined entry schema with dates, importance levels, categories, operations, compaction rules, and Working Memory / Archive tiers with progressive disclosure.
- **Conflict resolution hierarchy**: An explicit seven-level priority order for resolving contradictions between files, including host capability constraints.
- **Graduated mutability**: Each file has a defined stability level and update cadence, preventing uncontrolled drift.
- **Canonical update envelope**: A structured format (`[SOUL-UPDATE]`) for all file modifications — explicit, reviewable, and auditable.
- **Session model**: Explicit privacy controls for private, shared, and public sessions with per-session-type memory read/write policies.
- **System as a first-class file**: Runtime contract (capabilities, environment, tool policy, session model) and behavioral rules separated from identity, soul, and orchestration — with scaling guidelines.
- **Specification purity**: No runtime, no platform, no tooling — just files. Any system that reads Markdown can implement the protocol.

## License

MIT
