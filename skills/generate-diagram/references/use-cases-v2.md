# UML 2 use case diagram

Source: OMG UML 2.5.1, Annex A, use case diagram. The frame may carry the uc heading.

## Question it answers

Who uses the system and for which goals.

## Diagram that is easy to read

A guide for choosing what to draw when the user leaves it open. It never removes what the user asked for or approved (see Fidelity in the skill).

Actors outside the subject. Three to six ellipses. «include» for mandatory reuse and «extend» for an optional variation. No flow steps inside the ellipse.

## Notation for this version

- Actor, use case, and subject (the boundary).
- Association, «include», «extend», and generalization.
- The `uc` frame heading belongs to UML 2. PlantUML does not draw that frame; the title takes its place and the delivery says so.
- The use-case text belongs to adrenaline-project-manager.

## Render

PlantUML draws actors, cases, and relationships natively. The frame with a uc heading is not drawn; the title replaces it and that must be said.

## Template

`../assets/use-cases-v2.puml`. Replace the domain names and keep the shape.

## Example

```plantuml
@startuml
left to right direction
title What the buyer can do in the store

actor Buyer
rectangle "Store" {
  usecase "Pay order" as pay
  usecase "Choose payment method" as method
  usecase "Apply coupon" as coupon
  pay .> method : <<include>>
  pay .> coupon : <<extend>>
}
Buyer --> pay
@enduml
```

![use-cases-v2](../assets/use-cases-v2.svg)

## Examples

Short command. The command already fixes the diagram, so a few words of domain are enough. The agent fills in what you leave open.

```text
/uml-use-cases-v2 A buyer paying an order.
```

Command. It fixes the diagram. The rest is the domain.

```text
/uml-use-cases-v2 The buyer pays an order, always chooses the payment method, and may extend the payment with a coupon.
```

Prompt. The sentence names the diagram, and the skill chooses this reference.

```text
Draw a UML 2 use case diagram of the store: the buyer pays an order, always chooses the payment method, and may extend the payment with a coupon.
```
