# Memory

<!-- This file is the assistant's persistent long-term memory. It stores curated knowledge
     that survives across sessions — not raw conversation logs, but distilled, atomic facts.

     ENTRY FORMAT:
     - [YYYY-MM-DD] [high|medium|low] Content as a clear, specific statement.

     RULES:
     - One fact per entry. Be precise and atomic.
     - Use the date when the fact was learned or last confirmed.
     - Importance levels:
       - high: Core knowledge that should inform most interactions.
       - medium: Useful context that is relevant in specific situations.
       - low: Minor details that may decay over time.
     - Place entries in the appropriate category section.
     - When the file exceeds ~100 entries, follow the compaction protocol in soul-protocol.md.

     OPERATIONS:
     - ADD: New fact with no matching entry.
     - UPDATE: Modify an existing entry in-place, update the date.
     - DELETE: Remove an entry that has been contradicted by new information.
     - NOOP: No new information worth persisting. Do nothing. -->

## Facts

<!-- Concrete knowledge about the user, their environment, or the world.
     Example:
     - [2025-01-15] [high] User's primary programming language is Python.
     - [2025-02-01] [medium] User's company uses GitHub Enterprise for version control. -->

## Preferences

<!-- Behavioral and interaction preferences learned through conversation.
     Example:
     - [2025-01-20] [high] User prefers code examples over abstract explanations.
     - [2025-02-03] [medium] User dislikes when responses start with "Sure!" or "Absolutely!" -->

## Events

<!-- Significant occurrences with temporal context.
     Example:
     - [2025-01-10] [high] User started a new role as tech lead at Acme Corp.
     - [2025-02-05] [medium] User's team completed the migration to Kubernetes. -->

## Decisions

<!-- Choices made during conversations, with rationale when available.
     Example:
     - [2025-01-25] [high] Chose PostgreSQL over MongoDB for the new project — relational data model fits better.
     - [2025-02-02] [medium] Decided to use Tailwind CSS instead of styled-components for consistency with team. -->

## Reflections

<!-- Higher-order insights synthesized from multiple interactions.
     These are patterns, observations, or lessons — not raw facts.
     Example:
     - [2025-02-01] [medium] User works best in short, focused bursts. Long sessions lead to diminishing returns.
     - [2025-02-06] [low] User tends to second-guess architectural decisions — offering pros/cons lists helps them commit. -->

## Archive

<!-- Compacted, aged, or historically relevant entries that are no longer actively needed
     but have reference value. Entries are moved here during compaction.
     A compaction note should precede archived entries:
     Example: Compacted on 2025-03-01: merged 12 entries, archived 8, removed 5. -->
