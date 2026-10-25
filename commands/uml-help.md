---
name: uml-help
description: "ADRenaline. Help: catalog of adrenaline-uml-diagrams (skills, rules, commands)."
---

# Help — adrenaline-uml-diagrams

Print this catalog as the reply. One line per item. Do not run any skill or command. Do not invent entries that are not listed. If a component was added to the plugin and is missing here, add one line from its frontmatter `description` and say the catalog was refreshed.

## Plugin

- [**adrenaline-uml-diagrams**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/README.md) — Draws the 9 UML 1.5 diagrams and the 14 UML 2.5.1 diagrams, each in its own notation, without mixing versions.

## Skills

- [**generate-diagram**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/SKILL.md) — Draws one UML 1 or UML 2 diagram from the catalog (PlantUML + optional Mermaid for classes, sequence, states), or saves one from the conversation as it was shown.

## Rules

- [**output-folder**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/rules/output-folder.mdc) — Every diagram goes in `uml-diagrams/` (or `outputDirs["adrenaline-uml-diagrams"]` in `.cursor/adrenaline.json`).
- [**uml-notation**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/rules/uml-notation.mdc) — Do not mix UML 1 and UML 2 notation; use only the matching reference.

## Commands

- [**/uml-help**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/README.md) — This help (one-line catalog of the plugin).
- [**/uml-classes-v1**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/classes-v1.md) — UML 1 class diagram: what concepts exist and how they relate, in UML 1.5 notation.
- [**/uml-classes-v2**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/classes-v2.md) — UML 2 class diagram: what concepts exist and how they relate, in UML 2.5.1 notation.
- [**/uml-objects-v1**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/objects-v1.md) — UML 1 object diagram: what values exist at one instant, in UML 1.5 notation.
- [**/uml-objects-v2**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/objects-v2.md) — UML 2 object diagram: what values exist at one instant, in UML 2.5.1 notation.
- [**/uml-use-cases-v1**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/use-cases-v1.md) — UML 1 use case diagram: who uses the system and for what, in UML 1.5 notation.
- [**/uml-use-cases-v2**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/use-cases-v2.md) — UML 2 use case diagram: who uses the system and for what, in UML 2.5.1 notation.
- [**/uml-sequence-v1**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/sequence-v1.md) — UML 1 sequence diagram: what messages travel over time, without combined fragments such as alt, opt, loop, or par.
- [**/uml-sequence-v2**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/sequence-v2.md) — UML 2 sequence diagram: what messages travel over time, including combined fragments such as alt, opt, loop, and par.
- [**/uml-collaboration-v1**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/collaboration-v1.md) — UML 1 collaboration diagram: who is linked and in what numbered order; in UML 2 this view is the communication diagram.
- [**/uml-communication-v2**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/communication-v2.md) — UML 2 communication diagram: who is linked and in what numbered order; in UML 1 this view is the collaboration diagram.
- [**/uml-states-v1**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/states-v1.md) — UML 1 statechart diagram: what life one object goes through; in UML 2 this view is the state machine.
- [**/uml-state-machine-v2**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/state-machine-v2.md) — UML 2 state machine diagram: what life one object goes through; in UML 1 this view is the statechart.
- [**/uml-activities-v1**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/activities-v1.md) — UML 1 activity graph: how a procedure moves forward, without token flow or pins.
- [**/uml-activities-v2**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/activities-v2.md) — UML 2 activity diagram: how a procedure moves forward, including token flow.
- [**/uml-components-v1**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/components-v1.md) — UML 1 component diagram: what software is assembled, without ports or connectors.
- [**/uml-components-v2**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/components-v2.md) — UML 2 component diagram: what software is assembled, including ports and connectors.
- [**/uml-deployment-v1**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/deployment-v1.md) — UML 1 deployment diagram: where the software is installed, in UML 1.5 notation.
- [**/uml-deployment-v2**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/deployment-v2.md) — UML 2 deployment diagram: where the software is installed, in UML 2.5.1 notation.
- [**/uml-packages-v2**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/packages-v2.md) — UML 2 package diagram: how the model is grouped; this view exists only in UML 2.
- [**/uml-composite-v2**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/composite-v2.md) — UML 2 composite structure diagram: what parts one piece has inside; this view exists only in UML 2.
- [**/uml-profiles-v2**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/profiles-v2.md) — UML 2 profile diagram: how UML itself is extended; this view exists only in UML 2.
- [**/uml-timing-v2**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/timing-v2.md) — UML 2 timing diagram: when a state changes over time; this view exists only in UML 2.
- [**/uml-interaction-overview-v2**](https://github.com/d-mente/adrenaline-uml-diagrams/blob/main/skills/generate-diagram/references/interaction-overview-v2.md) — UML 2 interaction overview diagram: in what order several scenarios run; this view exists only in UML 2.

## Output

- Folder: `uml-diagrams/` (override via `.cursor/adrenaline.json`).
- Name: `<NNN>-<id>-<topic>.<ext>`, with monotonic `<NNN>`.

| Format | Description |
| --- | --- |
| `.puml` | PlantUML source, editable |
| `.svg` | Rendered diagram image |
| `.md` | Mermaid version (classes, sequence, states) |
| `STATUS.md` | State of each diagram |

## Not in this plugin

- Architecture evaluation / ADR → `adrenaline-software-architect`.
- Use-case text → `adrenaline-project-manager`.

In Claude Code, commands use the prefix `/adrenaline-uml-diagrams:` (example: `/adrenaline-uml-diagrams:uml-help`).
