<p align="right">Language:&emsp;<img alt="English" src="https://raw.githubusercontent.com/ADRenaline-Suite/.github/main/profile/lang-en-on.svg" align="middle" style="vertical-align:middle"> <a href="interaction-overview-v2.es.md" style="vertical-align:middle"><img alt="Español" src="https://raw.githubusercontent.com/ADRenaline-Suite/.github/main/profile/lang-es-off.svg" align="middle" style="vertical-align:middle"></a></p>

[🏠 UML Diagrams](../../../README.md) / [Generate a UML diagram](../SKILL.md)

# UML 2 interaction overview diagram

Source: OMG UML 2.5.1, Annex A. Interaction is the family: sequence, communication, timing, and this overview. It is not a fifteenth diagram.

## Question it answers

In what order several already defined scenarios follow one another.

## Diagram that is easy to read

A guide for choosing what to draw when the user leaves it open. It never removes what the user asked for or approved (see Fidelity in the skill).

The shape of an activity: a start, nodes that name an interaction (`sd Name`), one decision, and a stop. Each node is a scenario, not a loose business step.

## Notation for this version

- Control nodes as in an activity, with interaction uses (`ref`) in the nodes.
- The message detail lives in the sequence diagram of that `sd`.
- The full sequence is not expanded inside each node.

## Render

PlantUML has no interaction-overview frame. The delivery uses an activity whose labels start with `sd` and declares that. Those labels are scenarios, not actions of an activity diagram.

## Template

`../assets/interaction-overview-v2.puml`. Replace the domain names and keep the shape.

## Example

```plantuml
@startuml
title In what order the purchase scenarios happen

start
:sd Select products;
:sd Confirm order;
if (Payment accepted?) then (yes)
  :sd Charge;
  :sd Issue receipt;
else (no)
  :sd Decline payment;
endif
stop
@enduml
```

![interaction-overview-v2](../assets/interaction-overview-v2.svg)

## Examples

Short command. The command already fixes the diagram, so a few words of domain are enough. The agent fills in what you leave open.

```text
/uml-interaction-overview-v2 A purchase.
```

Command. It fixes the diagram. The rest is the domain.

```text
/uml-interaction-overview-v2 Select products, confirm the order, and, if the payment is accepted, charge and issue a receipt; otherwise decline the payment. Each node is an sd scenario.
```

Prompt. The sentence names the diagram, and the skill chooses this reference.

```text
Draw the UML 2 interaction overview of a purchase: select products, confirm the order, and, if the payment is accepted, charge and issue a receipt; otherwise decline the payment. Each node is an sd scenario.
```

## Done

- The drawing answers in what order several already defined scenarios follow one another. The title states that question.
- Nodes are interaction uses whose labels start with `sd`. The message detail of each scenario is not expanded inside the node.
- Every scenario the user asked for or approved is in the source. The guide added something only where the user left it open, and the Guide line says so.
- The Render line says approximation: an activity whose labels start with `sd`, and those labels are scenarios, not actions.
