---
name: conversation-title-organizer
description: Classify a substantive conversation into a stable macro category and maintain a concise title in the format MACRO_Descriptive title. Use when organizing conversation history, selecting or updating a chat title, or when a host can rename the current conversation. Lock the macro after first classification, update only the descriptive suffix when the dominant topic materially evolves, and never claim a rename occurred unless the host exposes and successfully executes a supported rename action.
---

# Conversation Title Organizer

Keep conversation titles predictable, searchable, and stable.

Use this exact pattern:

`MACRO_Descriptive title`

## Workflow

1. Ignore greetings, accidental messages, and other non-substantive openings.
2. Identify the conversation's primary subject and user objective.
3. Select exactly one macro from `references/taxonomy.md`.
4. Lock that macro for the life of the conversation.
5. Generate a concise descriptive suffix for the dominant thread.
6. Re-evaluate the suffix after substantive turns, but update it only when the dominant topic materially changes or broadens.
7. If the host exposes a supported conversation-title rename action, execute the exact title silently.
8. If the host cannot rename the conversation, do not claim that it did. Return or surface the recommended title only when the user or host asks for it.

Read `references/taxonomy.md` whenever selecting a macro or resolving an overlap between categories.

Read `references/examples.md` when a title pattern, update decision, or edge case is unclear.

## Macro rules

- Use only a macro defined in `references/taxonomy.md`.
- Never invent a macro autonomously.
- Once assigned, treat the macro as locked.
- Change a locked macro only when the user explicitly requests reclassification.
- Classify by the dominant subject and objective, not by incidental tools, filenames, or temporary sub-questions.
- Prefer a domain-specific macro over `Research` when a clear domain exists.
- Use `Other` only when no approved macro fits with reasonable confidence.

## Suffix rules

The descriptive suffix MUST:

- represent the dominant thread rather than the latest isolated message;
- normally contain 3–8 meaningful words;
- remain understandable when seen alone in a sidebar;
- include named entities when they materially improve recognition;
- use the conversation's main language;
- default to Italian when the conversation is substantially mixed Italian and English;
- avoid generic filler such as `Discussione`, `Domanda`, `Aiuto`, `Varie`, `Nuova chat`, or `Analisi generale`;
- avoid unnecessary dates;
- avoid repeating the macro word unless needed for meaning.

## Update rules

Do not rename for every new message.

Update the suffix only when at least one condition is true:

1. The user explicitly changes the main objective.
2. A new subject within the same macro becomes the dominant theme across substantive turns.
3. The conversation broadens enough that the current suffix is materially too narrow.
4. A specific project, company, product, person, place, or framework becomes central and improves recognition.

Do not update for a small translation, formatting task, implementation detail, or temporary detour inside the existing topic.

## Explicit overrides

The user's explicit instruction wins.

Examples:

- `Metti questa chat sotto Finance` → change the macro to `Finance` and lock the new value.
- `Rinomina questa chat Politics_Elezioni USA 2028` → use that title unless a hard host constraint prevents it.
- `Non cambiare più il titolo` → stop automatic suffix updates for the conversation.

## Rename execution

Before any write action:

1. Construct the exact title.
2. Verify the macro is approved.
3. Preserve the locked macro unless explicitly overridden.
4. Verify the suffix represents the dominant conversation.
5. Check whether the host exposes a supported current-conversation title update action.

If the action exists and succeeds, continue the user's requested task without unnecessary rename commentary.

If the action is unavailable or fails:

- do not report success;
- do not imply the sidebar changed;
- keep the naming recommendation separate from execution.

## Output

When an external caller explicitly asks only for the recommended title, return exactly:

`MACRO_Descriptive title`

Return no explanation unless requested.
