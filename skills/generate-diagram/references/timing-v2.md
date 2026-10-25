# UML 2 timing diagram

Source: OMG UML 2.5.1, Annex A, timing diagram. It does not exist in the v1 catalog.

## Question it answers

When the state or the value of a few lifelines changes.

## Diagram that is easy to read

A guide for choosing what to draw when the user leaves it open. It never removes what the user asked for or approved (see Fidelity in the skill).

Two or three lines, time from left to right, named states. Few changes. Use it when the question is the instant of the change, not the list of messages.

## Notation for this version

- Lifeline and state or value along the time axis.
- Messages between lines only if they explain a change.
- Duration constraints only if the request gives numbers.
- If the question is who calls whom, the diagram is the sequence diagram.

## Render

PlantUML draws this diagram natively with `robust` and `@` time marks.

## Template

`../assets/timing-v2.puml`. Replace the domain names and keep the shape.

## Example

```plantuml
@startuml
title When the order and the payment change during the charge

robust "Order" as order
robust "Payment" as payment

@0
order is Draft
payment is Absent
@100
order is Confirmed
@200
payment is Authorizing
@300
payment is Authorized
order is Paid
@enduml
```

![timing-v2](../assets/timing-v2.svg)

## Examples

Short command. The command already fixes the diagram, so a few words of domain are enough. The agent fills in what you leave open.

```text
/uml-timing-v2 An order being paid.
```

Command. It fixes the diagram. The rest is the domain.

```text
/uml-timing-v2 The order moves from draft to confirmed and then to paid, and the payment moves from absent to authorizing and to authorized on that last stretch.
```

Prompt. The sentence names the diagram, and the skill chooses this reference.

```text
Draw a UML 2 timing diagram: the order moves from draft to confirmed and then to paid, and the payment moves from absent to authorizing and to authorized on that last stretch.
```
