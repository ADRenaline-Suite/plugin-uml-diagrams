# UML 1 class diagram

Source: OMG UML 1.5, class diagram.

## Question it answers

What concepts exist and how they relate, in UML 1 class notation.

## Diagram that is easy to read

Three to six boxes with three compartments. Associations with multiplicity and a verb as the name. At most one generalization. Aggregation or composition only when the whole and the part are the question.

## Notation for this version

- A box with a name, attributes, and operations.
- Association, aggregation (hollow diamond), composition (filled diamond), dependency, and generalization.
- Multiplicity on the ends.
- This version does not put ports or internal parts on the class. That is UML 2 composite structure.

## Render

PlantUML draws this diagram natively.

## Template

`../assets/classes-v1.puml`. Replace the domain names and keep the shape.

## Example

```plantuml
@startuml
skinparam shadowing false
hide empty members
title What data an order has and how it relates to its payment

class Order {
  +number : String
  +total() : Decimal
  +confirm()
}
class OrderLine {
  +quantity : Integer
  +subtotal() : Decimal
}
class Payment {
  +amount : Decimal
  +authorize()
}

Order "1" *-- "1..*" OrderLine : contains
Order "1" --> "0..1" Payment : settled with
@enduml
```

![classes-v1](../assets/classes-v1.svg)

## Example prompt

> Draw a UML 1 class diagram of an order: an order contains one or more lines and is settled with an optional payment. Show only number, total, quantity, subtotal, and amount, and the operations confirm, subtotal, and authorize.
