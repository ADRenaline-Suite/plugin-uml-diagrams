# UML 2 sequence diagram

Source: OMG UML 2.5.1, Annex A, sequence diagram. Combined fragments are specified under Interactions.

## Question it answers

What messages are exchanged over time, including the branches that actually matter.

## Diagram that is easy to read

An actor on the left, two or three lifelines, read top to bottom. At most one alt, opt, or loop fragment. The title names the scenario.

## Notation for this version

- Lifelines, synchronous messages, and returns.
- Combined fragments: alt, opt, and loop cover almost every request. par only when there is real parallelism.
- Each alt operand has a guard.
- A v1 sequence diagram of the same name does not use these fragments.

## Render

PlantUML draws this diagram natively, including alt, opt, and loop.

## Template

`../assets/sequence-v2.puml`. Replace the domain names and keep the shape.

## Example

```plantuml
@startuml
title What happens when paying if the bank authorizes or declines

actor Buyer
participant Checkout
participant Bank

Buyer -> Checkout : pay(amount)
alt authorized
  Checkout -> Bank : charge(amount)
  Bank --> Checkout : ok
  Checkout --> Buyer : receipt
else declined
  Checkout --> Buyer : payment declined
end
@enduml
```

![sequence-v2](../assets/sequence-v2.svg)

## Example prompt

> Draw a UML 2 sequence diagram of paying an order, with one alt: if the bank authorizes, checkout returns the receipt; if it declines, checkout tells the buyer.
