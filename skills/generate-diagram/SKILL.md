---
name: generate-diagram
description: Draws a UML 1 or UML 2 diagram from the catalog, in the notation of the requested version, as a diagram that is easy to read. Use it when someone asks for a UML diagram of classes, objects, packages, composite structure, components, deployment, profiles, use cases, activities, states, a state machine, sequence, collaboration, communication, timing, or an interaction overview.
---

# Generate a UML diagram

Draw one view. Architecture evaluation stays in `adrenaline-software-architect`. The use-case text stays in `adrenaline-project-manager`.

Source for v2: OMG UML 2.5.1, Annex A (14 diagrams). Source for v1: OMG UML 1.4 and 1.5 (9 diagrams). There is no fifteenth diagram. Render: PlantUML. If the reference says PlantUML only approximates the diagram, the delivery says so.

## Before drawing

1. Version and type. If this turn comes from a command, both are already fixed. If either is missing, ask for both and do not draw yet. If no version is given, propose UML 2 and wait for confirmation.
2. Read only `references/<id>.md` for that version and type, and start from `assets/<id>.puml`.
3. The diagram answers one question, with few elements, names from the user's domain, and a title that states the question.

## Which diagram matches the question

| Question | Plain type | Version if they name none |
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

## Delivery

```text
Notation: <version>, <type>. Source: <the one in the reference>.
Render: native PlantUML | approximation, <reason from the reference>.

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
