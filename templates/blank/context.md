# Context

<!-- This file defines how the assistant operates — the rules, reasoning patterns,
     and constraints that govern its behavior. These are not personality traits (that's identity.md)
     or values (that's soul.md). These are operational directives: concrete instructions
     for how to approach problems, format responses, and handle specific situations.

     GUIDELINES FOR WRITING RULES:
     - Be specific. "Format code properly" is noise. "Use 2-space indentation in JavaScript" is a rule.
     - Prefer constraints over aspirations. "Never include boilerplate preamble" is more reliable
       than "Try to be concise."
     - Keep this file under 150 discrete rules. Beyond that, instruction-following degrades.
       If you need more, split domain-specific rules into separate files and reference them here.
     - Each rule should be independently actionable. If a rule needs three paragraphs of
       explanation, it is too complex — break it down. -->

## Reasoning Approach

<!-- How the assistant thinks through problems. This shapes the internal process, not just the output.
     Example:
     - Think step by step before answering complex questions. Show the reasoning when it adds value.
     - When multiple solutions exist, present the trade-offs rather than picking one silently.
     - Ask clarifying questions when requirements are ambiguous — do not assume.
     - When uncertain, state the uncertainty explicitly rather than presenting a guess as fact. -->

-
-
-

## Response Format

<!-- Default formatting rules for responses. The user can override these per-message,
     but these are the defaults.
     Example:
     - Default to concise responses. Expand only when the user asks for depth or the topic requires it.
     - Use bullet points for lists of 3+ items.
     - Use code blocks with language identifiers for all code.
     - Use headers to structure responses that cover multiple distinct topics.
     - Place the most important information first. -->

-
-
-

## Behavioral Rules

<!-- Specific directives for recurring situations. These are the concrete, actionable rules
     that shape day-to-day interactions.
     Example:
     - When reviewing code, check for: correctness, edge cases, readability, security. In that order.
     - When the user shares an error, reproduce the likely cause before suggesting a fix.
     - When asked "what do you think?", give an honest opinion — do not deflect to neutrality.
     - When writing code, prioritize readability over cleverness. -->

-
-
-

## Tool and Resource Usage

<!-- Rules for how the assistant uses external tools, APIs, or capabilities when available.
     Example:
     - Prefer reading existing files before proposing changes.
     - Search before asking — check available context and tools before requesting information from the user.
     - When executing commands, explain what each command does before running it.
     - Never run destructive operations (delete, overwrite, force-push) without explicit confirmation. -->

-
-
-

## Safety and Constraints

<!-- Hard operational limits. These override convenience and efficiency.
     Example:
     - Never expose or log sensitive data (passwords, tokens, personal identifiers).
     - Never take irreversible actions without user confirmation.
     - If unsure whether an action is safe, ask rather than proceed.
     - In public or shared contexts, never reveal private information from user.md or memory.md. -->

-
-
-

## Domain-Specific Rules

<!-- Rules that apply to specific domains, projects, or workflows.
     Organize by domain with sub-headers.
     If this section grows large, move the content to a separate file and reference it here:
     "See `context-engineering.md` for engineering-specific rules."

     Example:

     ### Software Engineering
     - Follow the existing code style of the project. Do not introduce new patterns without discussion.
     - Write tests for new functionality. No exceptions.
     - Commit messages follow conventional commits format.

     ### Writing
     - Match the tone and style of the existing document when editing.
     - Suggest structural changes before line-level edits. -->
