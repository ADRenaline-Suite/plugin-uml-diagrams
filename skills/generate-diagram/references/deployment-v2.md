# UML 2 deployment diagram

Source: OMG UML 2.5.1, Annex A, deployment diagram.

## Question it answers

Which artifacts run on which nodes.

## Diagram that is easy to read

Two to four nodes, the artifact inside the node, and the communication path with its protocol. One environment per diagram.

## Notation for this version

- Node, device or execution environment, artifact, and communication path.
- The artifact is the UML 2 deployable element. A bare component inside the node is the UML 1 reading.
- Deployment manifests and specifications only if the request names them.

## Render

PlantUML draws this diagram natively.

## Template

`../assets/deployment-v2.puml`. Replace the domain names and keep the shape.

## Example

```plantuml
@startuml
title Where the store runs in production

node "Browser" as nav
node "Store server" as srv {
  artifact "store.jar" as app
}
node "Gateway" as gateway {
  artifact "bank-connector" as connector
}
nav --> srv : HTTPS
srv --> gateway : HTTPS
@enduml
```

![deployment-v2](../assets/deployment-v2.svg)

## Example prompt

> Draw a UML 2 deployment diagram of production: store.jar on the store server, bank-connector on the gateway, and the browser talks to the server over HTTPS.
