# UML Diagrams (`adrenaline-uml-diagrams`)

Genera diagramas UML 1.5 y UML 2.5.1 para cualquier rol. Cada pedido usa la notación de la versión pedida.

La documentación de cada diagrama está en `skills/generar-diagrama/references/`. Cada página trae el gráfico fácil de leer, la notación, la plantilla, un ejemplo PlantUML y un prompt de ejemplo. Las plantillas viven en `skills/generar-diagrama/assets/`.

## Para quién

Para quien necesite una vista UML dentro de una conversación con el agente: arquitectura, casos de uso, pruebas o interfaz. Esos roles piden este plugin. No copian sus skills.

## Qué incluye

Portable, para cualquier agente que siga [Agent Skills](https://agentskills.io/specification):

- Skill `generar-diagrama`, con una referencia y una plantilla PlantUML por cada diagrama del catálogo (9 de UML 1 y 14 de UML 2).

Solo Cursor:

- 23 commands, uno por diagrama. En el chat, `/uml-sequence-v2` o el nombre de otro command.
- Rule `notacion-uml`, que impide mezclar las dos notaciones.

## Instalación

En Cursor, instala el plugin desde este repositorio en Customize.

En otro agente, instala la skill con el mecanismo de ese agente. Por ejemplo:

```text
gh skill install d-mente/adrenaline-uml-diagrams
```

## Configuración

No usa variables ni servicios. El render es PlantUML.

## Cómo se pide

En el chat, `/uml-sequence-v2` o el nombre de otro command. También basta pedir el diagrama en lenguaje natural: el skill elige la referencia.

PlantUML es el render. Comunicación, colaboración, estructura compuesta, perfiles y visión general de la interacción no tienen tipo nativo en PlantUML: la referencia dice la aproximación y la entrega también.

## Catálogo

| Diagrama | Acción | Documentación |
| --- | --- | --- |
| Diagrama de clases UML 1 | `/uml-classes-v1` | [referencia](skills/generar-diagrama/references/clases-v1.md) |
| Diagrama de clases UML 2 | `/uml-classes-v2` | [referencia](skills/generar-diagrama/references/clases-v2.md) |
| Diagrama de objetos UML 1 | `/uml-objects-v1` | [referencia](skills/generar-diagrama/references/objetos-v1.md) |
| Diagrama de objetos UML 2 | `/uml-objects-v2` | [referencia](skills/generar-diagrama/references/objetos-v2.md) |
| Diagrama de casos de uso UML 1 | `/uml-use-cases-v1` | [referencia](skills/generar-diagrama/references/casos-de-uso-v1.md) |
| Diagrama de casos de uso UML 2 | `/uml-use-cases-v2` | [referencia](skills/generar-diagrama/references/casos-de-uso-v2.md) |
| Diagrama de secuencia UML 1 | `/uml-sequence-v1` | [referencia](skills/generar-diagrama/references/secuencia-v1.md) |
| Diagrama de secuencia UML 2 | `/uml-sequence-v2` | [referencia](skills/generar-diagrama/references/secuencia-v2.md) |
| Diagrama de colaboración UML 1 | `/uml-collaboration-v1` | [referencia](skills/generar-diagrama/references/colaboracion-v1.md) |
| Diagrama de estados UML 1 (statechart) | `/uml-states-v1` | [referencia](skills/generar-diagrama/references/estados-v1.md) |
| Diagrama de actividades UML 1 (activity graph) | `/uml-activities-v1` | [referencia](skills/generar-diagrama/references/actividades-v1.md) |
| Diagrama de componentes UML 1 | `/uml-components-v1` | [referencia](skills/generar-diagrama/references/componentes-v1.md) |
| Diagrama de despliegue UML 1 | `/uml-deployment-v1` | [referencia](skills/generar-diagrama/references/despliegue-v1.md) |
| Diagrama de paquetes UML 2 | `/uml-packages-v2` | [referencia](skills/generar-diagrama/references/paquetes-v2.md) |
| Diagrama de estructura compuesta UML 2 | `/uml-composite-v2` | [referencia](skills/generar-diagrama/references/estructura-compuesta-v2.md) |
| Diagrama de componentes UML 2 | `/uml-components-v2` | [referencia](skills/generar-diagrama/references/componentes-v2.md) |
| Diagrama de despliegue UML 2 | `/uml-deployment-v2` | [referencia](skills/generar-diagrama/references/despliegue-v2.md) |
| Diagrama de perfiles UML 2 | `/uml-profiles-v2` | [referencia](skills/generar-diagrama/references/perfiles-v2.md) |
| Diagrama de actividades UML 2 | `/uml-activities-v2` | [referencia](skills/generar-diagrama/references/actividades-v2.md) |
| Diagrama de máquina de estados UML 2 | `/uml-state-machine-v2` | [referencia](skills/generar-diagrama/references/maquina-de-estados-v2.md) |
| Diagrama de comunicación UML 2 | `/uml-communication-v2` | [referencia](skills/generar-diagrama/references/comunicacion-v2.md) |
| Diagrama de tiempos UML 2 | `/uml-timing-v2` | [referencia](skills/generar-diagrama/references/tiempos-v2.md) |
| Diagrama de visión general de la interacción UML 2 | `/uml-interaction-overview-v2` | [referencia](skills/generar-diagrama/references/vision-general-interaccion-v2.md) |

## Licencia

MIT. Ver [LICENSE](LICENSE).
