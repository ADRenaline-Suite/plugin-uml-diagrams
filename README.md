# UML Diagrams (`adrenaline-uml-diagrams`)

Draws UML 1.5 and UML 2.5.1 diagrams for any role. Each request uses the notation of the version that was asked for.

Each diagram is documented in `skills/generate-diagram/references/`. Each page has the easy-to-read diagram, the notation, the template, a PlantUML example, and an example prompt. The templates live in `skills/generate-diagram/assets/`.

## Who it is for

Anyone who needs a UML view inside a conversation with the agent: architecture, use cases, testing, or interface. Those roles ask this plugin for the drawing. They do not copy its skills.

## What it includes

Portable, for any agent that follows [Agent Skills](https://agentskills.io/specification):

- Skill `generate-diagram`, with one reference and one PlantUML template for each diagram in the catalog (9 from UML 1 and 14 from UML 2).

Cursor only:

- 23 commands, one per diagram. In chat, `/uml-sequence-v2` or the name of another command.
- Rule `uml-notation`, which stops the two notations from being mixed.

## Installation

In Cursor, install the plugin from this repository in Customize.

On another agent, install the skill with that agent's mechanism. For example:

```text
gh skill install d-mente/adrenaline-uml-diagrams
```

## Configuration

It uses no variables and no services. The render is PlantUML.

## How to ask

In chat, `/uml-sequence-v2` or the name of another command. Asking for the diagram in plain language is enough: the skill chooses the reference.

PlantUML is the render. Communication, collaboration, composite structure, profiles, and interaction overview have no native PlantUML type: the reference states the approximation, and the delivery states it too.

Each reference includes the rendered SVG next to its source. This is the UML 2 class diagram:

![UML 2 class diagram](skills/generate-diagram/assets/classes-v2.svg)

## Catalog

| Diagram | Action | Documentation |
| --- | --- | --- |
| UML 1 class diagram | `/uml-classes-v1` | [reference](skills/generate-diagram/references/classes-v1.md) |
| UML 2 class diagram | `/uml-classes-v2` | [reference](skills/generate-diagram/references/classes-v2.md) |
| UML 1 object diagram | `/uml-objects-v1` | [reference](skills/generate-diagram/references/objects-v1.md) |
| UML 2 object diagram | `/uml-objects-v2` | [reference](skills/generate-diagram/references/objects-v2.md) |
| UML 1 use case diagram | `/uml-use-cases-v1` | [reference](skills/generate-diagram/references/use-cases-v1.md) |
| UML 2 use case diagram | `/uml-use-cases-v2` | [reference](skills/generate-diagram/references/use-cases-v2.md) |
| UML 1 sequence diagram | `/uml-sequence-v1` | [reference](skills/generate-diagram/references/sequence-v1.md) |
| UML 2 sequence diagram | `/uml-sequence-v2` | [reference](skills/generate-diagram/references/sequence-v2.md) |
| UML 1 collaboration diagram | `/uml-collaboration-v1` | [reference](skills/generate-diagram/references/collaboration-v1.md) |
| UML 1 statechart diagram | `/uml-states-v1` | [reference](skills/generate-diagram/references/states-v1.md) |
| UML 1 activity graph | `/uml-activities-v1` | [reference](skills/generate-diagram/references/activities-v1.md) |
| UML 1 component diagram | `/uml-components-v1` | [reference](skills/generate-diagram/references/components-v1.md) |
| UML 1 deployment diagram | `/uml-deployment-v1` | [reference](skills/generate-diagram/references/deployment-v1.md) |
| UML 2 package diagram | `/uml-packages-v2` | [reference](skills/generate-diagram/references/packages-v2.md) |
| UML 2 composite structure diagram | `/uml-composite-v2` | [reference](skills/generate-diagram/references/composite-v2.md) |
| UML 2 component diagram | `/uml-components-v2` | [reference](skills/generate-diagram/references/components-v2.md) |
| UML 2 deployment diagram | `/uml-deployment-v2` | [reference](skills/generate-diagram/references/deployment-v2.md) |
| UML 2 profile diagram | `/uml-profiles-v2` | [reference](skills/generate-diagram/references/profiles-v2.md) |
| UML 2 activity diagram | `/uml-activities-v2` | [reference](skills/generate-diagram/references/activities-v2.md) |
| UML 2 state machine diagram | `/uml-state-machine-v2` | [reference](skills/generate-diagram/references/state-machine-v2.md) |
| UML 2 communication diagram | `/uml-communication-v2` | [reference](skills/generate-diagram/references/communication-v2.md) |
| UML 2 timing diagram | `/uml-timing-v2` | [reference](skills/generate-diagram/references/timing-v2.md) |
| UML 2 interaction overview diagram | `/uml-interaction-overview-v2` | [reference](skills/generate-diagram/references/interaction-overview-v2.md) |

## License

MIT. See [LICENSE](LICENSE).
