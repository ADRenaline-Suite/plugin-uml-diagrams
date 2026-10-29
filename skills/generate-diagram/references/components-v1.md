<p align="right">Language:&emsp;<img alt="English" src="https://raw.githubusercontent.com/ADRenaline-Suite/.github/main/profile/lang-en-on.svg" align="middle" style="vertical-align:middle"> <a href="components-v1.es.md" style="vertical-align:middle"><img alt="Español" src="https://raw.githubusercontent.com/ADRenaline-Suite/.github/main/profile/lang-es-off.svg" align="middle" style="vertical-align:middle"></a></p>

[🏠 UML Diagrams](../../../README.md) / [Generate a UML diagram](../SKILL.md)

# UML 1 component diagram

Source: OMG UML 1.5, component diagram.

## Question it answers

What components exist and which ones they depend on.

## Diagram that is easy to read

A guide for choosing what to draw when the user leaves it open. It never removes what the user asked for or approved (see Fidelity in the skill).

Three to five components and dashed dependencies with a readable stereotype. Interfaces only if the question is what is fulfilled, not how it is deployed.

## Notation for this version

- Component, interface, dependency, and realization.
- No ports and no assembly connectors. Those are UML 2.
- The node where it is installed belongs on the deployment diagram.

## Render

PlantUML draws components and dependencies natively. A v1 request does not use portin, portout, or composite-structure connectors.

## Template

`../assets/components-v1.puml`. Replace the domain names and keep the shape.

## Example

```plantuml
@startuml
title What checkout depends on in order to charge

component Checkout
component BankGateway
component Orders

Checkout ..> BankGateway : <<use>>
Checkout ..> Orders : <<use>>
@enduml
```

![components-v1](../assets/components-v1.svg)

## Examples

Short command. The command already fixes the diagram, so a few words of domain are enough. The agent fills in what you leave open.

```text
/uml-components-v1 Checkout and the bank.
```

Command. It fixes the diagram. The rest is the domain.

```text
/uml-components-v1 Checkout depends on the bank gateway and on orders. No ports.
```

Prompt. The sentence names the diagram, and the skill chooses this reference.

```text
Draw a UML 1 component diagram: checkout depends on the bank gateway and on orders. No ports.
```

## Done

- The drawing answers what components exist and which ones they depend on. The title states that question.
- Components, interfaces, dependencies, and realizations are present. Ports and assembly connectors are absent. The node where it is installed is absent.
- Every element the user asked for or approved is in the source. The guide added something only where the user left it open, and the Guide line says so.
- Render is native PlantUML. The delivery does not call it an approximation and does not use `portin` or `portout`.
