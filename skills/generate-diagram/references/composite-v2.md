<p align="right">Language:&emsp;<img alt="English" src="https://raw.githubusercontent.com/ADRenaline-Suite/.github/main/profile/lang-en-on.svg" align="middle" style="vertical-align:middle"> <a href="composite-v2.es.md" style="vertical-align:middle"><img alt="Español" src="https://raw.githubusercontent.com/ADRenaline-Suite/.github/main/profile/lang-es-off.svg" align="middle" style="vertical-align:middle"></a></p>

[🏠 UML Diagrams](../../../README.md) / [Generate a UML diagram](../SKILL.md)

# UML 2 composite structure diagram

Source: OMG UML 2.5.1, Annex A, composite structure diagram. It does not exist in the v1 catalog.

## Question it answers

What parts a classifier has inside, and how they are connected.

## Diagram that is easy to read

A guide for choosing what to draw when the user leaves it open. It never removes what the user asked for or approved (see Fidelity in the skill).

One outer classifier and two to four parts with a role `: Type`. Connectors between parts. Ports only on the boundary the outside shows.

## Notation for this version

- Part, port, and connector.
- A part is named `role : Type`.
- This is not a class diagram: it does not list the catalog of types. It shows the wiring of one classifier.

## Render

PlantUML has no first-class composite structure diagram. The delivery uses a container and inner rectangles as an approximation of parts and connectors, and it declares that.

## Template

`../assets/composite-v2.puml`. Replace the domain names and keep the shape.

## Example

```plantuml
@startuml
title Internal wiring of an Order

rectangle "Order" {
  rectangle "lines : OrderLine" as lines
  rectangle "payment : Payment" as payment
  lines --> payment : notify total
}
@enduml
```

![composite-v2](../assets/composite-v2.svg)

## Examples

Short command. The command already fixes the diagram, so a few words of domain are enough. The agent fills in what you leave open.

```text
/uml-composite-v2 The inside of an order.
```

Command. It fixes the diagram. The rest is the domain.

```text
/uml-composite-v2 Order has the parts lines and payment, and the lines notify the total to the payment.
```

Prompt. The sentence names the diagram, and the skill chooses this reference.

```text
Draw the UML 2 composite structure of Order: inside it has the parts lines and payment, and the lines notify the total to the payment.
```

## Done

- The drawing answers what parts a classifier has inside, and how they are connected. The title states that question.
- Parts are named `role : Type`, with ports and connectors. It is not a catalog of types and it does not list every attribute of a class diagram.
- Every element the user asked for or approved is in the source. The guide added something only where the user left it open, and the Guide line says so.
- The Render line says approximation: a container and inner rectangles, for the reason in this reference.
