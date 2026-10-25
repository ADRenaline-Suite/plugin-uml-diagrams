# UML 2 object diagram

Source: OMG UML 2.5.1, Annex A, object diagram.

## Question it answers

What concrete values the instances have at one instant.

## Diagram that is easy to read

A guide for choosing what to draw when the user leaves it open. It never removes what the user asked for or approved (see Fidelity in the skill).

A few underlined instances, slots, and links. One moment.

## Notation for this version

- Instance specification: underlined name and classifier.
- Slots with values.
- Links, which are instances of associations.
- If the type is needed and the value is not, the diagram to draw is the class diagram.

## Render

PlantUML draws this diagram natively with `object`.

## Template

`../assets/objects-v2.puml`. Replace the domain names and keep the shape.

## Example

```plantuml
@startuml
title Snapshot: order 1042 already has an authorized payment

object "order1042 : Order" as order {
  number = "1042"
}
object "line1 : OrderLine" as line {
  quantity = 2
}
object "payment9 : Payment" as payment {
  amount = 320.00
}

order --> line
order --> payment
@enduml
```

![objects-v2](../assets/objects-v2.svg)

## Examples

Short command. The command already fixes the diagram, so a few words of domain are enough. The agent fills in what you leave open.

```text
/uml-objects-v2 One paid order.
```

Command. It fixes the diagram. The rest is the domain.

```text
/uml-objects-v2 The instant when order 1042 is linked to its line and to a payment of 320.00.
```

Prompt. The sentence names the diagram, and the skill chooses this reference.

```text
Draw a UML 2 object diagram of the instant when order 1042 is linked to its line and to a payment of 320.00.
```
