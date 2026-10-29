<p align="right">Language:&emsp;<img alt="English" src="https://raw.githubusercontent.com/ADRenaline-Suite/.github/main/profile/lang-en-on.svg" align="middle" style="vertical-align:middle"> <a href="README.es.md" style="vertical-align:middle"><img alt="Español" src="https://raw.githubusercontent.com/ADRenaline-Suite/.github/main/profile/lang-es-off.svg" align="middle" style="vertical-align:middle"></a></p>

# UML Diagrams (`plugin-uml-diagrams`)

Draws UML 1.5 and UML 2.5.1 diagrams for any role. Each request uses the notation of the version that was asked for.

Each diagram is documented in `skills/generate-diagram/references/`. Each page has the easy-to-read diagram, the notation, the template, a PlantUML example, and three ways to ask: a short command, a command that pins the content, and a sentence. The templates live in `skills/generate-diagram/assets/`.

## Who it is for

Anyone who needs a UML view inside a conversation with the agent: architecture, use cases, testing, or interface. Those roles ask this plugin for the drawing. They do not copy its skills.

## What it includes

Portable, for any agent that follows [Agent Skills](https://agentskills.io/specification):

- Skill [generate-diagram](skills/generate-diagram/SKILL.md), with one reference and one PlantUML template for each diagram in the catalog (9 from UML 1 and 14 from UML 2). The skill also carries the notation limits and the output folder, so an agent without rules keeps them.

Cursor and Claude Code:

- 24 commands: `/uml-help` (one-line catalog of skills, rules, and commands) and one command per diagram. In Cursor, `/uml-help` or `/uml-sequence-v2`. In Claude Code, `/plugin-uml-diagrams:uml-help`.

Cursor only:

- Rule `uml-notation`, which stops the two notations from being mixed.
- Rule `output-folder`, which keeps every diagram inside the output folder.

## Installation

In Cursor, install the plugin from this repository in Customize.

In Claude Code, this repository is also a marketplace:

```text
claude plugin marketplace add ADRenaline-Suite/plugin-uml-diagrams
claude plugin install plugin-uml-diagrams@plugin-uml-diagrams
```

To try a local copy without installing it, start Claude Code with `claude --plugin-dir <path to this repository>`.

On another agent, install the skill with that agent's mechanism. For example:

```text
gh skill install ADRenaline-Suite/plugin-uml-diagrams
```

## Configuration

It uses no variables and no services. The render is PlantUML.

Each diagram is saved at the project root as two files: the source `uml-diagrams/<NNN>-<id>-<topic>.puml` and the image `uml-diagrams/<NNN>-<id>-<topic>.svg`, with a monotonic `<NNN>` that is never reused. The folder also keeps `STATUS.md` (`proposed` | `accepted` | `deprecated` | `superseded`); prefer `accepted` when several versions exist. The SVG needs one of `plantuml` on the PATH, `java -jar plantuml.jar`, or Docker with the `plantuml/plantuml` image. Without any of them, only the `.puml` is saved and the delivery gives the command to render it.

Class, sequence, and state diagrams also get `uml-diagrams/<NNN>-<id>-<topic>.md` with the same diagram in Mermaid, which GitHub, GitLab, and Azure DevOps render without tools. The other types have no native Mermaid equivalent, so they get no Mermaid file. The rules are in [references/mermaid.md](skills/generate-diagram/references/mermaid.md).

To use another folder, add `.cursor/adrenaline.json` to the project:

```json
{
  "outputDirs": {
    "plugin-uml-diagrams": "docs/uml"
  }
}
```

The path is relative to the project root and cannot contain `..`. Claude Code and other agents read the same file.

## How to ask

Before it closes, the command checks the done list of `generate-diagram` and of that diagram. A file that fails a check is corrected in the same turn, or it is not marked `accepted`.

If a command name is unfamiliar, read [What each command is for](#what-each-command-is-for) before the catalog.

In Cursor, `/uml-sequence-v2` or the name of another command. In Claude Code, the same name with the plugin prefix: `/plugin-uml-diagrams:uml-sequence-v2`. Asking for the diagram in plain language is enough: the skill chooses the reference.

To save a diagram the agent already showed in the conversation, ask to save it. It is saved as it was shown, with the same participants and branches. Each reference's readability guide only applies when you leave the content open; if the diagram goes beyond it, the delivery says so and suggests a split, but does not cut anything unless you ask.

PlantUML is the render. Communication, collaboration, composite structure, profiles, and interaction overview have no native PlantUML type: the reference states the approximation, and the delivery states it too.

Each reference includes the rendered SVG next to its source. This is the UML 2 class diagram:

![UML 2 class diagram](skills/generate-diagram/assets/classes-v2.svg)

## What each command is for

You do not need to know UML. Each command draws one picture that answers one question about a system. The name after `/uml-` is the kind of picture. `v1` means the older notation (UML 1.5). `v2` means the current one (UML 2.5.1). If nobody asked for the old notation, use `v2`.

There is one skill, [generate-diagram](skills/generate-diagram/SKILL.md). It is the part that draws. You do not have to name it: a command already chooses it. If you describe the picture in a sentence instead of using a command, that skill picks the matching manual.

### `/uml-help`

Prints this plugin's list: the skill, the rules, and every command, each in one sentence. It does not draw a diagram and it does not save a file. Use it when you want to see what you can ask for.

### `/uml-classes-v1`

Draws a class diagram in the older notation. A class diagram is a map of the ideas in a system — an order, a customer, a payment — and the lines that say how those ideas depend on each other. Each box can list the data it keeps and the actions it can do. Use it when the team needs to agree on those ideas before building, and an existing document already uses UML 1.

### `/uml-classes-v2`

Draws the same kind of map as `/uml-classes-v1`: the ideas and how they relate, in the current notation. Use this one unless someone asked for UML 1.

### `/uml-objects-v1`

Draws an object diagram in the older notation. Where a class diagram shows the ideas in general, this one shows a snapshot: the actual values at one moment (this order, this customer, this amount). Use it when a concrete example would explain the model better than the general map, and the document must stay in UML 1.

### `/uml-objects-v2`

Draws the same snapshot as `/uml-objects-v1`, in the current notation. Use it to show one concrete example of the ideas in a class diagram.

### `/uml-use-cases-v1`

Draws a use case diagram in the older notation. It shows who uses the system (a person or another system) and what they use it for, such as pay, cancel, or look up an order. It does not describe the steps inside each goal. Use it when you need the boundary of the system, and the file must use UML 1.

### `/uml-use-cases-v2`

Draws the same picture as `/uml-use-cases-v1` — who uses the system and for what — in the current notation. The written story of each goal is not this diagram. That text belongs to `plugin-project-manager`.

### `/uml-sequence-v1`

Draws a sequence diagram in the older notation. It shows who talks to whom, and in what order, over time: the customer asks to pay, the shop asks the bank, the bank answers. It cannot draw a branch such as "if the bank says no". If the story has alternatives, this command splits them into separate pictures. Use it for one straight conversation, in UML 1.

### `/uml-sequence-v2`

Draws the same conversation over time as `/uml-sequence-v1`, in the current notation. This one can also show branches and repetitions, such as the bank saying yes or no, or a step that repeats. Use it when the order of messages is the question.

### `/uml-collaboration-v1`

Draws a collaboration diagram, which exists only in UML 1. It shows the same conversation as a sequence diagram, drawn as a map of who is connected, with numbers on the messages for the order. Use it when those links matter and a UML 1 document is required. In UML 2 the same picture is `/uml-communication-v2`.

### `/uml-communication-v2`

Draws a communication diagram. It is the same idea as `/uml-collaboration-v1`: who is linked, and in what numbered order the messages go. This is the current name of that picture. Use it when the links matter more than a top-to-bottom timeline.

### `/uml-states-v1`

Draws a statechart, the UML 1 name for the life of one thing. Boxes are situations, such as an order that is new, paid, shipped, or cancelled, and arrows are what makes it change. Use it when you need that life in UML 1 notation. In UML 2 the same picture is `/uml-state-machine-v2`.

### `/uml-state-machine-v2`

Draws a state machine: the life of one thing, from start to end, and what moves it from one situation to the next. Use it when the question is what this thing can become, and when, in the current notation.

### `/uml-activities-v1`

Draws an activity graph, the UML 1 picture of a procedure: the steps, the decisions, and where the work splits or joins. It does not use the newer notation for tokens and pins. Use it for a procedure that must stay in UML 1.

### `/uml-activities-v2`

Draws an activity diagram: how a procedure moves forward, including the current notation for work that splits, waits, and joins. Use it when the question is the steps of a process. Who sends which message is a sequence diagram, not this one.

### `/uml-components-v1`

Draws a component diagram in the older notation. A component is a piece of software that can be swapped or shipped on its own, such as billing or login, and the lines show how those pieces plug together. This version does not draw ports. Use it when the question is which software pieces exist, in UML 1.

### `/uml-components-v2`

Draws the same assembly of software pieces as `/uml-components-v1`, in the current notation, which can also show the plugs (ports) and the wires between them. Use it when you need to see how the parts of the software connect.

### `/uml-deployment-v1`

Draws a deployment diagram in the older notation. It shows where the software sits: which program runs on which machine, server, or device. Use it when the question is the installation, and the file must use UML 1.

### `/uml-deployment-v2`

Draws the same picture as `/uml-deployment-v1` — where the software is installed — in the current notation. Use it to agree on servers, devices, and what runs on each.

### `/uml-packages-v2`

Draws a package diagram. A package is a folder of the model: a way to group classes or other pieces so a large model can be read in parts, and to show which group depends on which. This picture exists only in UML 2. Use it when the model is too big to look at as one flat list.

### `/uml-composite-v2`

Draws a composite structure diagram. It opens one piece and shows the parts inside it and how those inner parts connect, such as a checkout made of a cart, a price check, and a payment. This picture exists only in UML 2. Use it when the inside of one piece is the question. The map of every idea is a class diagram, not this one.

### `/uml-profiles-v2`

Draws a profile diagram. A profile is a way to extend UML itself with extra labels for a domain, for example marking a class as a service. This picture exists only in UML 2. Use it when you are defining that extension. It does not draw the system.

### `/uml-timing-v2`

Draws a timing diagram. It shows when a thing changes situation along a clock: how long it stays in each one, and what it is doing at a given moment. This picture exists only in UML 2. Use it when duration is the question. The list of situations, without the clock, is a state machine.

### `/uml-interaction-overview-v2`

Draws an interaction overview. It is a map of several scenarios and the order in which they run: first this conversation, then that one, and a decision between them. Each scenario is usually a sequence diagram. This picture exists only in UML 2. Use it when you already have several conversations and need to show how they fit together.

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
