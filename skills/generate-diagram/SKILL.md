---
name: generate-diagram
description: Draws a UML 1 or UML 2 diagram from the catalog, in the notation of the requested version, as a diagram that is easy to read. Use it when someone asks for a UML diagram of classes, objects, packages, composite structure, components, deployment, profiles, use cases, activities, states, a state machine, sequence, collaboration, communication, timing, or an interaction overview, or asks to save a UML diagram already shown in the conversation.
---

# Generate a UML diagram

Draw one view. Architecture evaluation stays in `adrenaline-software-architect`. The use-case text stays in `adrenaline-project-manager`.

Source for v2: OMG UML 2.5.1, Annex A (14 diagrams). Source for v1: OMG UML 1.4 and 1.5 (9 diagrams). There is no fifteenth diagram. Render: PlantUML. If the reference says PlantUML only approximates the diagram, the delivery says so.

## Before drawing

1. Version and type. If this turn comes from a command, both are already fixed. If the diagram is already in the conversation, take both from it (see "Save a diagram from the conversation"). If the request uses a construct that exists in only one version (`alt`, `opt`, `loop`, `par`, ports, pins, token flow), that is the version. Otherwise, if the type is missing, ask for it and do not draw yet; if only the version is missing, propose UML 2 and wait for confirmation.
2. Read only `references/<id>.md` for that version and type, and start from `assets/<id>.puml`. For classes, sequence, and states, also read `references/mermaid.md`.
3. The diagram answers one question, with names from the user's domain and a title that states the question. It holds what the user asked for: no more elements, and no fewer.

## Which diagram matches the question

| Question | Plain type | Version to propose |
| --- | --- | --- |
| Who uses the system and for what | use cases | v2 |
| What concepts exist and how they relate | classes | v2 |
| What values exist at one instant | objects | v2 |
| What messages travel over time | sequence | v2 |
| Who is linked, and in what numbered order | communication, or collaboration if they ask for v1 | v2 |
| How a procedure moves forward | activities | v2 |
| What life one object goes through | state machine, or states if they ask for v1 | v2 |
| How the model is grouped | packages | v2 only |
| What software is assembled | components | v2 |
| What parts one piece has inside | composite structure | v2 only |
| Where it is installed | deployment | v2 |
| When a state changes | timing | v2 only |
| In what order several scenarios run | interaction overview | v2 only |
| How UML itself is extended | profiles | v2 only |

Packages, composite structure, profiles, timing, and interaction overview exist only in v2. Collaboration is the v1 name; communication is the v2 name. States (statechart) is v1; state machine is v2.

## Do not mix the versions

A v1 request uses only the `*-v1` reference and v1 notation. A v2 request uses only the `*-v2` reference.

- Sequence v1 has no combined fragments (`alt`, `opt`, `loop`, `par`). Split the alternatives into separate scenarios.
- Activity v1 is an activity graph, with no token flow and no pins.
- Component v1 has no ports and no connectors.

If the notation or PlantUML lacks a construct, say so in the delivery. Do not invent a symbol.

## Fidelity

What the user asked for or approved wins over the "Diagram that is easy to read" guide of each reference. The guide decides what to include only when the user leaves it open.

- Do not drop a participant, message, element, relation, or fragment that the user asked for or approved. If the result goes beyond the guide, deliver it whole and say so in the `Guide` line, with how it could be split.
- Simplify, split, or merge only when the user asks. That is a new decision: next `<NNN>`, previous row `superseded`.
- The version rules are the only exception: a v1 request with an `alt` is split into scenarios. Every such difference goes in the `Fidelity` line. A change the delivery does not list is a defect.

## Save a diagram from the conversation

When the user asks to save a diagram already shown in this conversation, or pastes one in Mermaid, PlantUML, or as an agreed description:

1. Translate it one to one: the same participants, elements, messages, names, order, and fragments. Do not redraw it with the guide.
2. Take the type and version from the diagram itself. Do not ask again.
3. If it is not a catalog type (a flowchart, C4, an entity-relationship diagram), say that it is outside the catalog and ask where to save it. Do not force it into a UML type.
4. If it mixes versions, name the element and ask before changing it.

Then follow Delivery.

## Delivery

Save the PlantUML source as `<folder>/<NNN>-<id>-<topic>.puml` and the rendered image next to it as `<folder>/<NNN>-<id>-<topic>.svg`. `<folder>` is `uml-diagrams/` at the project root, unless `.cursor/adrenaline.json` sets `outputDirs["adrenaline-uml-diagrams"]` to a relative path without `..`. `<topic>` is the title in kebab-case. `<NNN>` is a monotonic integer in that folder (001, 002, …); never reuse a number for a different diagram. Create the folder if it is missing.

Write the diagram title and the labels in the language of the request. If the request names a language, use that one. Otherwise use the language the request is written in. Keep names the person already used. `STATUS.md` columns stay `N`, `archivo`, `estado`, `sustituye`, `notas`. The reply uses that same language.

Keep `<folder>/STATUS.md` with columns `N`, `archivo`, `estado`, `sustituye`, `notas`. States: `proposed`, `accepted`, `deprecated`, `superseded`. When choosing which diagram to trust, prefer `accepted` over newer drafts or deprecated files.

If a file for that topic already exists, do not ask. Decide from the user's text:

- The text asks to change **that** diagram (update, extend, amend the same view): edit the existing files; keep the same `<NNN>` and `accepted` in `STATUS.md`.
- The text asks for a replacement or a new decision on the same topic: allocate the next free `<NNN>`, mark the previous row `superseded` (point `sustituye` at the new `N`), set the new row `accepted`, and say so in the delivery.
- Otherwise (new topic): next free `<NNN>`, row `accepted`.

Draw only what the user's text asks. Do not offer to extend the model.

Render the SVG with the first PlantUML that is available:

```text
plantuml -tsvg -charset UTF-8 <file>.puml
java -jar plantuml.jar -tsvg -charset UTF-8 <file>.puml
docker run --rm -v "<absolute folder>:/data" plantuml/plantuml -tsvg -charset UTF-8 /data/<file>.puml
```

If the command fails or the SVG contains `Syntax Error`, fix the source and render again. If no PlantUML is available, keep the `.puml`, say that the SVG was not generated, and give the command to generate it.

Secondary format: for classes, sequence, and states, also write `<folder>/<NNN>-<id>-<topic>.md` with the same diagram in a `mermaid` block, following `references/mermaid.md`. Other types get no Mermaid file. The Mermaid file shares `<NNN>` with the PlantUML pair.

```text
Notation: <version>, <type>. Source: <the one in the reference>.
Render: native PlantUML | approximation, <reason from the reference>.
Fidelity: as asked or approved | changes: <each difference and its reason>
Guide: within | beyond, <what exceeds it>; could be split into <N> diagrams
Files: <folder>/<NNN>-<id>-<topic>.puml, <folder>/<NNN>-<id>-<topic>.svg
Status: <accepted|proposed|…> (see STATUS.md)
Mermaid: <folder>/<NNN>-<id>-<topic>.md | not generated, <reason>

<plantuml block>

Reading: <one sentence with the question the drawing answers>.
```

## Catalog

| Id | Diagram | Version |
| --- | --- | --- |
| `classes-v1` | UML 1 class diagram | UML 1.5 |
| `classes-v2` | UML 2 class diagram | UML 2.5.1 |
| `objects-v1` | UML 1 object diagram | UML 1.5 |
| `objects-v2` | UML 2 object diagram | UML 2.5.1 |
| `use-cases-v1` | UML 1 use case diagram | UML 1.5 |
| `use-cases-v2` | UML 2 use case diagram | UML 2.5.1 |
| `sequence-v1` | UML 1 sequence diagram | UML 1.5 |
| `sequence-v2` | UML 2 sequence diagram | UML 2.5.1 |
| `collaboration-v1` | UML 1 collaboration diagram | UML 1.5 |
| `states-v1` | UML 1 statechart diagram | UML 1.5 |
| `activities-v1` | UML 1 activity graph | UML 1.5 |
| `components-v1` | UML 1 component diagram | UML 1.5 |
| `deployment-v1` | UML 1 deployment diagram | UML 1.5 |
| `packages-v2` | UML 2 package diagram | UML 2.5.1 |
| `composite-v2` | UML 2 composite structure diagram | UML 2.5.1 |
| `components-v2` | UML 2 component diagram | UML 2.5.1 |
| `deployment-v2` | UML 2 deployment diagram | UML 2.5.1 |
| `profiles-v2` | UML 2 profile diagram | UML 2.5.1 |
| `activities-v2` | UML 2 activity diagram | UML 2.5.1 |
| `state-machine-v2` | UML 2 state machine diagram | UML 2.5.1 |
| `communication-v2` | UML 2 communication diagram | UML 2.5.1 |
| `timing-v2` | UML 2 timing diagram | UML 2.5.1 |
| `interaction-overview-v2` | UML 2 interaction overview diagram | UML 2.5.1 |
