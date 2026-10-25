# UML 1 activity graph

Source: OMG UML 1.4 and 1.5. In the UML 1.4 compliance points it is listed as an activity graph.

## Question it answers

In what order the steps of a procedure happen, and where it branches.

## Diagram that is easy to read

A guide for choosing what to draw when the user leaves it open. It never removes what the user asked for or approved (see Fidelity in the skill).

An initial state, actions as states, one decision with both exits labeled, and a final state. Swimlanes only when there are two clear owners.

## Notation for this version

- Action states and transitions, because in UML 1 an activity is a form of state machine.
- A decision is transitions with guards, not a free-standing control node.
- No pins, object nodes, or token flow. That is UML 2.
- UML 1 concurrency, when it is needed, is a fork/join pair, not several token flows.

## Render

PlantUML draws the graph with the old `(*)` syntax and quoted actions. That is the syntax for this request, not `start` / `if` / `stop`.

## Template

`../assets/activities-v1.puml`. Replace the domain names and keep the shape.

## Example

```plantuml
@startuml
title How an order is confirmed and charged

(*) --> "Confirm order"
"Confirm order" --> "Coupon?"
"Coupon?" --> [yes] "Apply discount"
"Coupon?" --> [no] "Charge"
"Apply discount" --> "Charge"
"Charge" --> (*)
@enduml
```

![activities-v1](../assets/activities-v1.svg)

## Examples

Short command. The command already fixes the diagram, so a few words of domain are enough. The agent fills in what you leave open.

```text
/uml-activities-v1 Confirm and charge an order.
```

Command. It fixes the diagram. The rest is the domain.

```text
/uml-activities-v1 Confirm and charge. If there is a coupon the discount is applied, and in both cases the order is charged. Use action-state syntax, not UML 2 token syntax.
```

Prompt. The sentence names the diagram, and the skill chooses this reference.

```text
Draw a UML 1 activity graph to confirm and charge: if there is a coupon the discount is applied, and in both cases the order is charged. Use action-state syntax, not UML 2 token syntax.
```
