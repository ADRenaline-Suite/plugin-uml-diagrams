---
name: generate-diagram
description: Dibuja un diagrama UML 1 o UML 2 del catálogo, en la notación de la versión pedida, como un diagrama fácil de leer. Úsalo cuando alguien pida un diagrama UML de clases, objetos, paquetes, estructura compuesta, componentes, despliegue, perfiles, casos de uso, actividades, estados, una máquina de estados, secuencia, colaboración, comunicación, tiempos o una vista general de interacción, o pida guardar un diagrama UML ya mostrado en la conversación.
---

<p align="right">Idioma:&emsp;<a href="SKILL.md" style="vertical-align:middle"><img alt="English" src="https://raw.githubusercontent.com/ADRenaline-Suite/.github/main/profile/lang-en-off.svg" align="middle" style="vertical-align:middle"></a> <img alt="Español" src="https://raw.githubusercontent.com/ADRenaline-Suite/.github/main/profile/lang-es-on.svg" align="middle" style="vertical-align:middle"></p>

[🏠 UML Diagrams](../../README.es.md)

# Generar un diagrama UML

Dibuja una vista. La evaluación de arquitectura se queda en `plugin-software-architect`. El texto del caso de uso se queda en `plugin-project-manager`.

Fuente de v2: OMG UML 2.5.1, anexo A (14 diagramas). Fuente de v1: OMG UML 1.4 y 1.5 (9 diagramas). No hay un decimoquinto diagrama. Render: PlantUML. Si la referencia dice que PlantUML solo aproxima el diagrama, la entrega lo dice.

## Antes de dibujar

1. Versión y tipo. Si este turno viene de un comando, los dos ya están fijos. Si el diagrama ya está en la conversación, toma los dos de él (ver «Guardar un diagrama de la conversación»). Si el pedido usa un constructo que existe en una sola versión (`alt`, `opt`, `loop`, `par`, puertos, pins, flujo de tokens), esa es la versión. Si no, si falta el tipo, pídelo y no dibujes todavía; si solo falta la versión, propone UML 2 y espera la confirmación.
2. Lee solo `references/<id>.md` de esa versión y ese tipo, y empieza desde `assets/<id>.puml`. Para clases, secuencia y estados, lee también [references/mermaid.es.md](references/mermaid.es.md).
3. El diagrama responde una pregunta, con nombres del dominio de la persona y un título que enuncia la pregunta. Contiene lo que la persona pidió: ni más elementos, ni menos.

## Qué diagrama corresponde a la pregunta

| Pregunta | Tipo en claro | Versión a proponer |
| --- | --- | --- |
| Quién usa el sistema y para qué | casos de uso | v2 |
| Qué conceptos existen y cómo se relacionan | clases | v2 |
| Qué valores existen en un instante | objetos | v2 |
| Qué mensajes viajan a lo largo del tiempo | secuencia | v2 |
| Quién está enlazado, y en qué orden numerado | comunicación, o colaboración si piden v1 | v2 |
| Cómo avanza un procedimiento | actividades | v2 |
| Qué vida recorre un objeto | máquina de estados, o estados si piden v1 | v2 |
| Cómo se agrupa el modelo | paquetes | solo v2 |
| Qué software se ensambla | componentes | v2 |
| Qué partes tiene una pieza por dentro | estructura compuesta | solo v2 |
| Dónde está instalado | despliegue | v2 |
| Cuándo cambia un estado | tiempos | solo v2 |
| En qué orden corren varios escenarios | vista general de interacción | solo v2 |
| Cómo se extiende el propio UML | perfiles | solo v2 |

Paquetes, estructura compuesta, perfiles, tiempos y vista general de interacción existen solo en v2. Colaboración es el nombre de v1; comunicación es el nombre de v2. Estados (statechart) es v1; máquina de estados es v2.

## No mezcles las versiones

Un pedido v1 usa solo la referencia `*-v1` y la notación v1. Un pedido v2 usa solo la referencia `*-v2`.

- La secuencia v1 no tiene fragmentos combinados (`alt`, `opt`, `loop`, `par`). Parte las alternativas en escenarios separados.
- La actividad v1 es un grafo de actividades, sin flujo de tokens y sin pins.
- El componente v1 no tiene puertos ni conectores.

Si la notación o PlantUML carece de un constructo, dilo en la entrega. No inventes un símbolo.

## Fidelidad

Lo que la persona pidió o aprobó gana a la guía «Diagrama fácil de leer» de cada referencia. La guía decide qué incluir solo cuando la persona lo deja abierto.

- No quites un participante, mensaje, elemento, relación o fragmento que la persona pidió o aprobó. Si el resultado se pasa de la guía, entrégalo entero y dilo en la línea `Guide`, con cómo podría partirse.
- Simplifica, parte o une solo cuando la persona lo pide. Eso es una decisión nueva: el `<NNN>` siguiente, y la fila anterior en `superseded`.
- Las reglas de versión son la única excepción: un pedido v1 con un `alt` se parte en escenarios. Cada diferencia de ese tipo va en la línea `Fidelity`. Un cambio que la entrega no lista es un defecto.

## Guardar un diagrama de la conversación

Cuando la persona pide guardar un diagrama ya mostrado en esta conversación, o pega uno en Mermaid, PlantUML o como una descripción acordada:

1. Tradúcelo uno a uno: los mismos participantes, elementos, mensajes, nombres, orden y fragmentos. No lo redibujes con la guía.
2. Toma el tipo y la versión del propio diagrama. No vuelvas a preguntar.
3. Si no es un tipo del catálogo (un diagrama de flujo, C4, un diagrama entidad-relación), di que está fuera del catálogo y pregunta dónde guardarlo. No lo fuerces a un tipo UML.
4. Si mezcla versiones, nombra el elemento y pregunta antes de cambiarlo.

Después sigue Entrega.

## Entrega

Guarda la fuente PlantUML como `<folder>/<NNN>-<id>-<topic>.puml` y la imagen renderizada junto a ella como `<folder>/<NNN>-<id>-<topic>.svg`. `<folder>` es `uml-diagrams/` en la raíz del proyecto, salvo que `.cursor/adrenaline.json` fije `outputDirs["plugin-uml-diagrams"]` en una ruta relativa sin `..`. `<topic>` es el título en kebab-case. `<NNN>` es un entero monótono en esa carpeta (001, 002, …); nunca reutilices un número para un diagrama distinto. Crea la carpeta si falta.

Escribe el título del diagrama y las etiquetas en el idioma del pedido. Si el pedido nombra un idioma, usa ese. Si no, usa el idioma en el que está escrito el pedido. Conserva los nombres que la persona ya usó. Las columnas de `STATUS.md` siguen `N`, `archivo`, `estado`, `sustituye`, `notas`. La respuesta usa ese mismo idioma.

Mantén `<folder>/STATUS.md` con las columnas `N`, `archivo`, `estado`, `sustituye`, `notas`. Estados: `proposed`, `accepted`, `deprecated`, `superseded`. Al elegir qué diagrama creer, prefiere `accepted` sobre borradores más nuevos o archivos `deprecated`.

Si ya existe un archivo de ese tema, no preguntes. Decide a partir del texto de la persona:

- El texto pide cambiar **ese** diagrama (actualizar, extender, enmendar la misma vista): edita los archivos existentes; conserva el mismo `<NNN>` y `accepted` en `STATUS.md`.
- El texto pide un reemplazo o una decisión nueva sobre el mismo tema: asigna el siguiente `<NNN>` libre, marca la fila anterior `superseded` (`sustituye` apunta al `N` nuevo), pon la fila nueva en `accepted` y dilo en la entrega.
- En otro caso (tema nuevo): el siguiente `<NNN>` libre, fila `accepted`.

Dibuja solo lo que pide el texto de la persona. No ofrezcas extender el modelo.

Renderiza el SVG con el primer PlantUML que esté disponible:

```text
plantuml -tsvg -charset UTF-8 <file>.puml
java -jar plantuml.jar -tsvg -charset UTF-8 <file>.puml
docker run --rm -v "<absolute folder>:/data" plantuml/plantuml -tsvg -charset UTF-8 /data/<file>.puml
```

Si el comando falla o el SVG contiene `Syntax Error`, corrige la fuente y vuelve a renderizar. Si no hay PlantUML disponible, conserva el `.puml`, di que el SVG no se generó y da el comando para generarlo.

Formato secundario: para clases, secuencia y estados, escribe también `<folder>/<NNN>-<id>-<topic>.md` con el mismo diagrama en un bloque `mermaid`, siguiendo `references/mermaid.md`. Los demás tipos no reciben archivo Mermaid. El archivo Mermaid comparte `<NNN>` con el par PlantUML.

```text
Notation: <version>, <type>. Source: <the one in the reference>.
Render: native PlantUML | approximation, <reason from the reference>.
Fidelity: as asked or approved | changes: <each difference and its reason>
Guide: within | beyond, <what exceeds it>; could be split into <N> diagrams
Files: <folder>/<NNN>-<id>-<topic>.puml, <folder>/<NNN>-<id>-<topic>.svg
Status: <accepted|proposed|…> (see STATUS.md)
Mermaid: <folder>/<NNN>-<id>-<topic>.md | not generated, <reason>

<plantuml block>

Reading: <one sentence with the question the drawing answers>.
```

## Terminado

Antes de cerrar, evalúa esta lista y la lista `## Done` de `references/<id>.md` para este diagrama. Si el id es un diagrama de clases, de secuencia o de estados, evalúa también `## Done` en `references/mermaid.md`. Un comando fija el id. Cada ítem es verdadero, o corriges el diagrama en este turno. No dejes un archivo que falle un ítem. No lo marques `accepted` mientras un ítem falle. Si el tipo sigue faltando, o un diagrama fuera del catálogo no tiene dónde guardarse, pregunta y no escribas archivos.

- Un diagrama, una pregunta, una versión. El archivo usa solo la referencia de esa versión. Un archivo v1 no tiene un constructo que este skill lista como exclusivo de v2. Una partición exigida por las reglas de versión se nombra en la línea `Fidelity`.
- Los archivos están solo en la carpeta de salida: `.puml` y `.svg` con el mismo `<NNN>`, `<id>` y `<topic>`. `<NNN>` no se reutiliza. `STATUS.md` coincide con ellos.
- El título y las etiquetas siguen el idioma del pedido. Los nombres que la persona ya usó se conservan. Las columnas de `STATUS.md` siguen `N`, `archivo`, `estado`, `sustituye`, `notas`.
- Cada elemento que la persona pidió o aprobó está en la fuente. No se quitó nada. Lo añadido porque la persona lo dejó abierto se nombra en la línea `Guide`.
- Un diagrama guardado desde la conversación coincide uno a uno: los mismos participantes, elementos, mensajes, nombres, orden y fragmentos. La guía no lo redibujó. Un diagrama fuera del catálogo no se forzó a un tipo UML.
- La respuesta tiene las líneas `Notation`, `Render`, `Fidelity`, `Guide`, `Files`, `Status` y `Mermaid`, y coinciden con los archivos. Una diferencia que no está en `Fidelity` es un defecto: corrige el archivo o la línea antes de cerrar.
- El SVG no tiene `Syntax Error`. Si no hay PlantUML disponible, el `.puml` se queda, la respuesta dice que el SVG no se generó y da el comando.
- Mermaid existe solo para clases, secuencia y estados, y solo cuando `mermaid.md` dice que se escriba. Cualquier otro id no tiene archivo Mermaid.

## Catálogo

| Id | Diagrama | Versión |
| --- | --- | --- |
| `classes-v1` | Diagrama de clases UML 1 | UML 1.5 |
| `classes-v2` | Diagrama de clases UML 2 | UML 2.5.1 |
| `objects-v1` | Diagrama de objetos UML 1 | UML 1.5 |
| `objects-v2` | Diagrama de objetos UML 2 | UML 2.5.1 |
| `use-cases-v1` | Diagrama de casos de uso UML 1 | UML 1.5 |
| `use-cases-v2` | Diagrama de casos de uso UML 2 | UML 2.5.1 |
| `sequence-v1` | Diagrama de secuencia UML 1 | UML 1.5 |
| `sequence-v2` | Diagrama de secuencia UML 2 | UML 2.5.1 |
| `collaboration-v1` | Diagrama de colaboración UML 1 | UML 1.5 |
| `states-v1` | Diagrama statechart UML 1 | UML 1.5 |
| `activities-v1` | Grafo de actividades UML 1 | UML 1.5 |
| `components-v1` | Diagrama de componentes UML 1 | UML 1.5 |
| `deployment-v1` | Diagrama de despliegue UML 1 | UML 1.5 |
| `packages-v2` | Diagrama de paquetes UML 2 | UML 2.5.1 |
| `composite-v2` | Diagrama de estructura compuesta UML 2 | UML 2.5.1 |
| `components-v2` | Diagrama de componentes UML 2 | UML 2.5.1 |
| `deployment-v2` | Diagrama de despliegue UML 2 | UML 2.5.1 |
| `profiles-v2` | Diagrama de perfiles UML 2 | UML 2.5.1 |
| `activities-v2` | Diagrama de actividades UML 2 | UML 2.5.1 |
| `state-machine-v2` | Diagrama de máquina de estados UML 2 | UML 2.5.1 |
| `communication-v2` | Diagrama de comunicación UML 2 | UML 2.5.1 |
| `timing-v2` | Diagrama de tiempos UML 2 | UML 2.5.1 |
| `interaction-overview-v2` | Diagrama de vista general de interacción UML 2 | UML 2.5.1 |
