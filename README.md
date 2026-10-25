# UML Diagrams (`adrenaline-uml-diagrams`)

Draws UML 1.5 and UML 2.5.1 diagrams for any role. Each request uses the notation of the version that was asked for.

Each diagram is documented in `skills/generate-diagram/references/`. Each page has the easy-to-read diagram, the notation, the template, a PlantUML example, and three ways to ask: a short command, a command that pins the content, and a sentence. The templates live in `skills/generate-diagram/assets/`.

## Who it is for

Anyone who needs a UML view inside a conversation with the agent: architecture, use cases, testing, or interface. Those roles ask this plugin for the drawing. They do not copy its skills.

## What it includes

Portable, for any agent that follows [Agent Skills](https://agentskills.io/specification):

- Skill `generate-diagram`, with one reference and one PlantUML template for each diagram in the catalog (9 from UML 1 and 14 from UML 2). The skill also carries the notation limits and the output folder, so an agent without rules keeps them.

Cursor and Claude Code:

- 24 commands: `/uml-help` (one-line catalog of skills, rules, and commands) and one command per diagram. In Cursor, `/uml-help` or `/uml-sequence-v2`. In Claude Code, `/adrenaline-uml-diagrams:uml-help`.

Cursor only:

- Rule `uml-notation`, which stops the two notations from being mixed.
- Rule `output-folder`, which keeps every diagram inside the output folder.

## Installation

In Cursor, install the plugin from this repository in Customize.

In Claude Code, this repository is also a marketplace:

```text
claude plugin marketplace add d-mente/adrenaline-uml-diagrams
claude plugin install adrenaline-uml-diagrams@adrenaline-uml-diagrams
```

To try a local copy without installing it, start Claude Code with `claude --plugin-dir <path to this repository>`.

On another agent, install the skill with that agent's mechanism. For example:

```text
gh skill install d-mente/adrenaline-uml-diagrams
```

## Configuration

It uses no variables and no services. The render is PlantUML.

Each diagram is saved at the project root as two files: the source `uml-diagrams/<NNN>-<id>-<topic>.puml` and the image `uml-diagrams/<NNN>-<id>-<topic>.svg`, with a monotonic `<NNN>` that is never reused. The folder also keeps `STATUS.md` (`proposed` | `accepted` | `deprecated` | `superseded`); prefer `accepted` when several versions exist. The SVG needs one of `plantuml` on the PATH, `java -jar plantuml.jar`, or Docker with the `plantuml/plantuml` image. Without any of them, only the `.puml` is saved and the delivery gives the command to render it.

Class, sequence, and state diagrams also get `uml-diagrams/<NNN>-<id>-<topic>.md` with the same diagram in Mermaid, which GitHub, GitLab, and Azure DevOps render without tools. The other types have no native Mermaid equivalent, so they get no Mermaid file. The rules are in [references/mermaid.md](skills/generate-diagram/references/mermaid.md).

To use another folder, add `.cursor/adrenaline.json` to the project:

```json
{
  "outputDirs": {
    "adrenaline-uml-diagrams": "docs/uml"
  }
}
```

The path is relative to the project root and cannot contain `..`. Claude Code and other agents read the same file.

## How to ask

In Cursor, `/uml-sequence-v2` or the name of another command. In Claude Code, the same name with the plugin prefix: `/adrenaline-uml-diagrams:uml-sequence-v2`. Asking for the diagram in plain language is enough: the skill chooses the reference.

To save a diagram the agent already showed in the conversation, ask to save it. It is saved as it was shown, with the same participants and branches. Each reference's readability guide only applies when you leave the content open; if the diagram goes beyond it, the delivery says so and suggests a split, but does not cut anything unless you ask.

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
