# UML 2 component diagram

Source: OMG UML 2.5.1, Annex A, component diagram.

## Question it answers

What components are assembled, and which interfaces they offer or require.

## Diagram that is easy to read

A guide for choosing what to draw when the user leaves it open. It never removes what the user asked for or approved (see Fidelity in the skill).

Two to four components. A provided interface as a lollipop and an explicit required interface. One assembly per question, not a map of the whole system.

## Notation for this version

- Component, provided interface, required interface, and usage dependency.
- Port and assembly connector when the component boundary matters.
- Those pieces are not copied into a UML 1 component diagram.

## Render

PlantUML draws components and interfaces natively. The lollipop is approximated with the interface joined by a solid line to the component that provides it, and a dashed dependency from the one that requires it.

## Template

`../assets/components-v2.puml`. Replace the domain names and keep the shape.

## Example

```plantuml
@startuml
skinparam componentStyle uml2
title Which interface the gateway offers and which one checkout requires

interface Charge
interface Authorization

component Checkout
component BankGateway

Checkout - Charge
BankGateway - Authorization
Checkout ..> Authorization : <<use>>
@enduml
```

![components-v2](../assets/components-v2.svg)

## Examples

Short command. The command already fixes the diagram, so a few words of domain are enough. The agent fills in what you leave open.

```text
/uml-components-v2 Checkout and the bank.
```

Command. It fixes the diagram. The rest is the domain.

```text
/uml-components-v2 Checkout provides Charge and uses Authorization, which the bank gateway provides.
```

Prompt. The sentence names the diagram, and the skill chooses this reference.

```text
Draw a UML 2 component diagram: checkout provides Charge and uses Authorization, which the bank gateway provides.
```
