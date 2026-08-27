# Architecture

## Overview

Conversation Title Organizer is split conceptually into two layers:

```text
Conversation
    |
    v
+-----------------------+
| Naming Engine         |
|-----------------------|
| detect substance      |
| classify macro        |
| lock macro            |
| generate suffix       |
| decide on update      |
+-----------------------+
    |
    v
Exact title string
    |
    v
+-----------------------+
| Rename Executor       |
|-----------------------|
| host capability check |
| supported title write |
+-----------------------+
```

The repository currently implements the **Naming Engine** as an Agent Skill.

The **Rename Executor** is deliberately host-dependent.

## State model

The naming logic treats a conversation as having three relevant pieces of state:

```text
macro: locked category
suffix: current descriptive title
rename_enabled: whether the host can update the title
```

### Macro state

The macro transitions from:

```text
UNCLASSIFIED -> LOCKED
```

It does not transition again unless the user explicitly overrides the classification.

This prevents category drift during long conversations.

### Suffix state

The suffix may change when the dominant subject materially evolves.

It should not change for:

- a single minor detour;
- translation or formatting inside the same topic;
- a temporary implementation detail;
- a small follow-up question.

## Decision boundary

The skill is responsible for answering:

> What should this conversation be called?

It is not automatically responsible for:

> Can this host modify the current conversation title?

Keeping those questions separate gives the project three advantages:

1. the classification logic is portable;
2. unsupported hosts can still use the naming recommendation;
3. future executor integrations can be added without rewriting the taxonomy.

## Taxonomy design

The taxonomy is intentionally controlled rather than generative.

A finite allowlist improves:

- long-term sidebar consistency;
- searchability;
- predictable classification;
- easier regression testing.

`Other` exists as a safety valve, not as a default category.

## Update policy

The suffix is re-evaluated after substantive turns, but a new title is produced only when the information architecture would improve.

A rename is justified when:

- the main objective changes;
- a new same-macro subject becomes dominant;
- the conversation broadens beyond the current suffix;
- a named project or entity becomes central enough to improve recognition.

## Failure behavior

When the host cannot rename the conversation:

- do not fabricate success;
- do not imply the sidebar changed;
- retain or return the recommended title only when useful.

This is a functional requirement, not merely a messaging preference.
