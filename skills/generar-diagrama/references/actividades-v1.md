# Diagrama de actividades UML 1 (activity graph)

Fuente: OMG UML 1.4 y 1.5. En los puntos de cumplimiento de UML 1.4 figura como activity graph.

## Pregunta que responde

En qué orden ocurren los pasos de un procedimiento y dónde se bifurca.

## Gráfico fácil de leer

Estado inicial, acciones como estados, una decisión con ambas salidas etiquetadas y estado final. Carriles solo si hay dos responsables claros.

## Notación de esta versión

- Estados de acción y transiciones, porque en UML 1 la actividad es una forma de máquina de estados.
- Decisión por transiciones con guarda, no por un nodo de control suelto.
- Sin pines, nodos objeto ni flujo de tokens. Eso es UML 2.
- La concurrencia de UML 1, si hace falta, es un par fork/join, no varios flujos de tokens.

## Render

PlantUML dibuja el grafo con la sintaxis antigua `(*)` y acciones entre comillas. Esa es la que corresponde a este pedido, no `start` / `if` / `stop`.

## Plantilla

`../assets/actividades-v1.puml`. Sustituye los nombres del dominio y conserva la forma.

## Ejemplo

```plantuml
@startuml
title Cómo se confirma y cobra un pedido

(*) --> "Confirmar pedido"
"Confirmar pedido" --> "¿Hay cupón?"
"¿Hay cupón?" --> "Aplicar descuento" : sí
"¿Hay cupón?" --> "Cobrar" : no
"Aplicar descuento" --> "Cobrar"
"Cobrar" --> (*)
@enduml
```

## Prompt de ejemplo

> Dibuja un activity graph UML 1 para confirmar y cobrar: si hay cupón se aplica el descuento y en ambos casos se cobra. Usa la sintaxis de estados de acción, no la de tokens de UML 2.
