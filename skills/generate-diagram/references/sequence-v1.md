# UML 1 sequence diagram

Source: OMG UML 1.5, sequence diagram.

## Question it answers

What messages are exchanged in a single scenario, top to bottom.

## Diagram that is easy to read

An actor on the left and two or three participants. One scenario, the happy path or one alternative in a separate drawing. Synchronous messages with a dashed return.

## Notation for this version

- Lifelines and messages in time order, top to bottom.
- Synchronous message and return.
- No combined fragments. alt, opt, loop, par, break, and ref are UML 2.
- A rejection or another branch is another sequence diagram, with its own title.

## Render

PlantUML draws sequence natively. Even if it accepts alt, a v1 request does not use it.

## Template

`../assets/sequence-v1.puml`. Replace the domain names and keep the shape.

## Example

```plantuml
@startuml
title Happy path: the buyer pays and receives the receipt

actor Buyer
participant Checkout
participant Bank

Buyer -> Checkout : pay(amount)
Checkout -> Bank : charge(amount)
Bank --> Checkout : ok
Checkout --> Buyer : receipt
@enduml
```

![sequence-v1](../assets/sequence-v1.svg)

## Example prompt

> Draw the UML 1 sequence diagram of the happy path for paying: the buyer asks checkout to charge, checkout asks the bank, and if the bank answers ok, checkout returns the receipt. No alt fragments.
