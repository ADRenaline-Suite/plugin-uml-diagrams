---
name: generar-diagrama
description: Genera un diagrama UML 1 o UML 2 del catálogo, con la notación de la versión pedida y un gráfico fácil de leer. Úsalo al pedir un diagrama UML, de clases, objetos, paquetes, estructura compuesta, componentes, despliegue, perfiles, casos de uso, actividades, estados, máquina de estados, secuencia, colaboración, comunicación, tiempos o visión general de la interacción.
---

# Generar un diagrama UML

Dibuja una vista. La evaluación de arquitectura queda en `adrenaline-software-architect`. El texto del caso de uso queda en `adrenaline-project-manager`.

Fuente v2: OMG UML 2.5.1, Anexo A (14 diagramas). Fuente v1: OMG UML 1.4 y 1.5 (9 diagramas). No hay un decimoquinto diagrama. Render: PlantUML. Si la referencia dice que PlantUML solo aproxima, la entrega lo dice.

## Antes de dibujar

1. Versión y tipo. Si este turno viene de un command, ya vienen fijados. Si faltan, pregunta las dos cosas y no dibujes todavía. Si no indican versión, propone UML 2 y espera confirmación.
2. Lee solo `references/<id>.md` de esa versión y ese tipo, y parte de `assets/<id>.puml`.
3. El diagrama responde una pregunta, con pocos elementos, nombres del dominio del usuario y un título que enuncia la pregunta.

## Qué diagrama corresponde a la pregunta

| Pregunta | Tipo fácil | Versión si no dicen otra |
| --- | --- | --- |
| Quién usa el sistema y para qué | casos de uso | v2 |
| Qué conceptos hay y cómo se relacionan | clases | v2 |
| Qué valores hay en un instante | objetos | v2 |
| Qué mensajes viajan en el tiempo | secuencia | v2 |
| Quién está enlazado y en qué orden numérico | comunicación, o colaboración si piden v1 | v2 |
| Cómo avanza un procedimiento | actividades | v2 |
| Qué vida recorre un objeto | máquina de estados, o estados si piden v1 | v2 |
| Cómo se agrupa el modelo | paquetes | solo v2 |
| Qué software se ensambla | componentes | v2 |
| Qué partes tiene una pieza por dentro | estructura compuesta | solo v2 |
| Dónde se instala | despliegue | v2 |
| Cuándo cambia un estado | tiempos | solo v2 |
| En qué orden van varios escenarios | visión general de la interacción | solo v2 |
| Cómo se extiende el propio UML | perfiles | solo v2 |

Paquetes, estructura compuesta, perfiles, tiempos y visión general solo existen en v2. Colaboración es el nombre v1; comunicación es el nombre v2. Estados (statechart) es v1; máquina de estados es v2.

## Entrega

```text
Notación: <versión>, <tipo>. Fuente: <la de la referencia>.
Render: PlantUML nativo | aproximación, <motivo de la referencia>.

<bloque plantuml>

Lectura: <una frase con la pregunta que el dibujo responde>.
```

## Catálogo

| Id | Diagrama | Versión |
| --- | --- | --- |
| `clases-v1` | Diagrama de clases UML 1 | UML 1.5 |
| `clases-v2` | Diagrama de clases UML 2 | UML 2.5.1 |
| `objetos-v1` | Diagrama de objetos UML 1 | UML 1.5 |
| `objetos-v2` | Diagrama de objetos UML 2 | UML 2.5.1 |
| `casos-de-uso-v1` | Diagrama de casos de uso UML 1 | UML 1.5 |
| `casos-de-uso-v2` | Diagrama de casos de uso UML 2 | UML 2.5.1 |
| `secuencia-v1` | Diagrama de secuencia UML 1 | UML 1.5 |
| `secuencia-v2` | Diagrama de secuencia UML 2 | UML 2.5.1 |
| `colaboracion-v1` | Diagrama de colaboración UML 1 | UML 1.5 |
| `estados-v1` | Diagrama de estados UML 1 (statechart) | UML 1.5 |
| `actividades-v1` | Diagrama de actividades UML 1 (activity graph) | UML 1.5 |
| `componentes-v1` | Diagrama de componentes UML 1 | UML 1.5 |
| `despliegue-v1` | Diagrama de despliegue UML 1 | UML 1.5 |
| `paquetes-v2` | Diagrama de paquetes UML 2 | UML 2.5.1 |
| `estructura-compuesta-v2` | Diagrama de estructura compuesta UML 2 | UML 2.5.1 |
| `componentes-v2` | Diagrama de componentes UML 2 | UML 2.5.1 |
| `despliegue-v2` | Diagrama de despliegue UML 2 | UML 2.5.1 |
| `perfiles-v2` | Diagrama de perfiles UML 2 | UML 2.5.1 |
| `actividades-v2` | Diagrama de actividades UML 2 | UML 2.5.1 |
| `maquina-de-estados-v2` | Diagrama de máquina de estados UML 2 | UML 2.5.1 |
| `comunicacion-v2` | Diagrama de comunicación UML 2 | UML 2.5.1 |
| `tiempos-v2` | Diagrama de tiempos UML 2 | UML 2.5.1 |
| `vision-general-interaccion-v2` | Diagrama de visión general de la interacción UML 2 | UML 2.5.1 |
