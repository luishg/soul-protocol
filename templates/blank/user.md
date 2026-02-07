# User

<!-- This file defines the user — who the assistant is serving. It is a living profile
     that the assistant updates as it learns about the user through conversation.
     This is a current-state document: it reflects who the user is now, not a history
     of who they were. When preferences change, update the existing entry — do not append.
     Never store passwords, tokens, API keys, or financial details here. -->

## Identity

- **Name:**
- **Preferred name:** <!-- How the user wants to be addressed. May differ from their full name. -->
- **Pronouns:** <!-- Optional. Leave blank if unknown. -->
- **Language:** <!-- Primary language for conversation. -->
- **Timezone:** <!-- For time-aware responses. Example: Europe/Madrid, America/New_York -->
- **Location:** <!-- General location if relevant. City or region level, not address. -->

## Communication Preferences

<!-- How the user prefers to receive information. These preferences override the assistant's
     default voice when they conflict. -->

- **Response length:** <!-- concise | detailed | adaptive -->
- **Formality:** <!-- casual | professional | adaptive -->
- **Format preference:** <!-- prose | bullet points | structured headers | code-first -->
- **Explanation depth:** <!-- minimal (just the answer) | moderate (answer + brief reasoning) | thorough (full context) -->
- **Language style notes:** <!-- Any specific preferences: no emojis, use analogies, avoid jargon, etc. -->

## Technical Profile

<!-- The user's technical background. This calibrates the complexity and specificity
     of responses. An expert does not need basic concepts explained. A beginner does. -->

- **Expertise level:** <!-- beginner | intermediate | advanced | expert -->
- **Primary languages/tools:** <!-- Programming languages, frameworks, tools they use regularly. -->
- **Domains:** <!-- Areas of knowledge or professional focus. Example: backend engineering, data science, design. -->

## Goals and Working Context

<!-- What the user is currently focused on. Update this as projects and priorities change. -->

### Current projects

<!-- Brief descriptions of active work. These give the assistant context for relevant suggestions.
     Example:
     - Building a SaaS product for team collaboration (Next.js, PostgreSQL).
     - Writing a research paper on distributed systems. -->

-
-

### Goals

<!-- What the user is trying to achieve, beyond specific projects.
     Example:
     - Improve code review skills.
     - Transition from frontend to full-stack development.
     - Ship the MVP by Q2. -->

-
-

## Interaction Patterns

<!-- Observed patterns in how the user interacts. This section is updated by the assistant
     as it notices recurring behaviors — not filled in by the user.
     Example:
     - Tends to ask broad questions first, then drills into specifics.
     - Prefers to see code before reading explanations.
     - Usually works late at night; may be tired — keep responses shorter during late sessions. -->

-
-

## Relationship Notes

<!-- Context about the working relationship between assistant and user.
     What works well, what has been adjusted, any important agreements.
     Example:
     - User prefers the assistant to push back on unclear requirements rather than assuming.
     - We agreed that the assistant will propose code changes as diffs, not full files.
     - User appreciates when the assistant flags potential issues proactively. -->

-
-
