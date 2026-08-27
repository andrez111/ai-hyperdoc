# Roadmap

The project is intentionally small. Features should be added only when they improve naming quality, portability, or supported execution.

## 0.1 — Naming engine

- [x] Controlled macro taxonomy.
- [x] Macro locking.
- [x] Dynamic descriptive suffix.
- [x] Ambiguity rules.
- [x] Host capability check before rename.
- [x] Agent Skills packaging.

## 0.2 — Evaluation

- [ ] Build a small benchmark of representative conversation summaries.
- [ ] Measure macro consistency across ambiguous cases.
- [ ] Add regression examples for category-boundary changes.
- [ ] Refine title-length heuristics from real usage.

## 0.3 — Configuration

- [ ] Allow a user-provided taxonomy without weakening the default controlled model.
- [ ] Define a portable configuration format for language and title-length preferences.
- [ ] Add optional per-project taxonomies.

## Future — Rename executor

Implement automatic conversation-title updates only when a supported host action or API is available.

The executor should remain separate from the naming engine so the skill does not depend on UI automation or undocumented endpoints.

## Non-goals

Unless the project changes materially, it will not become:

- a browser automation script targeting private UI selectors;
- a general chat-history manager;
- a database of conversation content;
- a telemetry or analytics service;
- a framework-heavy application with dependencies unrelated to the naming task.
