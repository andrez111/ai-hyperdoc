# Conversation Title Organizer

A small, portable Agent Skill for keeping AI conversation history consistently named.

It applies a simple convention:

```text
MACRO_Descriptive title
```

The **macro category is selected once and remains stable** for the conversation.  
The **descriptive title can evolve** when the dominant topic materially changes.

> Status: experimental. The classification and naming logic is implemented. Automatic renaming of a ChatGPT sidebar conversation still depends on the host exposing a supported conversation-title update action.

## Why this exists

Long-running AI conversations become difficult to scan when titles are generic, stale, or based only on the first message.

This skill treats conversation naming as a lightweight information-architecture problem:

- stable top-level categories;
- concise, searchable titles;
- controlled taxonomy;
- no title churn for minor detours;
- explicit handling of ambiguous categories;
- no false claim that a sidebar title was changed when the host cannot perform that action.

## Example

```text
Career_LinkedIn e posizionamento AI Adoption
Investments_Portafoglio ETF a 10 anni
Politics_Accountability dei rappresentanti eletti
Jobs_Top aziende Emilia-Romagna
AI_Copilot Governance e Adoption Enterprise
Images_Action Figure Zanna
```

A conversation may start as:

```text
Career_LinkedIn About section
```

and later evolve into:

```text
Career_CV LinkedIn e posizionamento professionale
```

The `Career` macro remains locked.

## Repository structure

```text
.
├── README.md
├── LICENSE
├── CHANGELOG.md
├── ROADMAP.md
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── SECURITY.md
├── docs/
│   └── ARCHITECTURE.md
└── skills/
    └── conversation-title-organizer/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        └── references/
            ├── taxonomy.md
            └── examples.md
```

The repository documentation is intentionally kept outside the installable skill folder. The skill folder contains only resources needed by an AI agent at runtime.

## Install the skill

The installable skill is:

```text
skills/conversation-title-organizer/
```

If your Agent Skills-compatible host accepts skill folders, install that folder.

For ChatGPT surfaces that support personal skills, use the product's Skill creation/upload flow and provide the skill folder according to the current product UI.

## How it works

The skill follows four stages:

1. Ignore non-substantive openings.
2. Classify the conversation into one approved macro.
3. Lock that macro for the rest of the conversation unless the user explicitly overrides it.
4. Re-evaluate only the descriptive suffix as the dominant subject evolves.

Detailed classification boundaries are documented in:

```text
skills/conversation-title-organizer/references/taxonomy.md
```

## Current limitation

This project deliberately separates two responsibilities:

### 1. Naming engine

Implemented by this repository.

It can determine the correct title and decide whether the suffix should change.

### 2. Rename executor

Host-dependent.

A host must expose a supported action for changing the current conversation title. If that action is unavailable, the skill must not claim that the sidebar has been changed.

This boundary keeps the naming logic reusable and avoids coupling the project to brittle UI automation.

## Design principles

- **Consistency over novelty** — categories come from a controlled allowlist.
- **Stable information architecture** — the macro does not drift.
- **Low title churn** — minor detours do not trigger renames.
- **Searchability** — titles should remain recognizable out of context.
- **Honest execution** — never report a rename that did not occur.
- **Portability** — the core is plain Markdown following the Agent Skills format.

## Why there is no application code

There is currently no deterministic local operation to execute. The project is procedural knowledge, not an application.

Adding a runtime, dependency tree, CI matrix, or framework would create maintenance cost without improving the skill. Code should be introduced only when a real rename API or other deterministic execution layer exists.

## Roadmap

See [ROADMAP.md](ROADMAP.md).

The main future milestone is a supported rename executor that can consume the naming decision produced by the skill.

## Contributing

Small, evidence-based improvements are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

## Security

See [SECURITY.md](SECURITY.md) for responsible reporting and instruction-integrity concerns.

## License

MIT. See [LICENSE](LICENSE).
