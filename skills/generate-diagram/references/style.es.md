<p align="right">Idioma:&emsp;<a href="style.md" style="vertical-align:middle"><img alt="English" src="https://raw.githubusercontent.com/ADRenaline-Suite/.github/main/profile/lang-en-off.svg" align="middle" style="vertical-align:middle"></a> <img alt="Español" src="https://raw.githubusercontent.com/ADRenaline-Suite/.github/main/profile/lang-es-on.svg" align="middle" style="vertical-align:middle"></p>

[🏠 UML Diagrams](../../../README.es.md) / [Generar un diagrama UML](../SKILL.es.md)

# Presentación

Fuente: OMG UML 2.5.1, cláusula 6.4.1. La misma cláusula cubre los dibujos UML 1 de este plugin: una presentación, las dos versiones.

## Lo que fija la especificación

La notación se lee en negro sobre fondo blanco. Una herramienta conforme puede usar otro esquema. En ese esquema, negro significa sólido, blanco significa hueco y gris significa un tono que se distinga de los dos. La fuente, el grosor de línea y el tamaño de la punta pueden variar. Esas diferencias no cambian el modelo.

Un relleno que no lleva una marca escrita no es notación. El diagrama sigue leyéndose en gris.

## Lo que usa cada diagrama

Pega el cuerpo de [../assets/style.puml](../assets/style.puml) en el `.puml`, en la línea siguiente a `@startuml`. Las plantillas de `assets/` usan `!include style.puml` porque ese archivo está a su lado. Un archivo guardado en la carpeta de salida no: el include apuntaría fuera de esa carpeta. Expándelo.

El bloque fija un lienzo blanco, rellenos blancos, trazo y texto negros, sin sombra y con esquinas rectas. La fuente es SansSerif, el cuerpo es 13, el título es 14, la flecha tiene grosor 1 y el aire es padding 8 con nodesep 40 y ranksep 40. Esos números son elecciones de este plugin. No son valores de la especificación. `classAttributeIconSize 0` deja la visibilidad como `+`, `-`, `#` y `~`.

`skinparam componentStyle uml2` se queda en la plantilla de componentes UML 2. Elige el símbolo. No forma parte de este bloque.

`hide circle` quita la letra dentro de un círculo que PlantUML pone en la cabecera de una clase. Esa letra no es notación UML.

Un diagrama de tiempos añade `skinparam monochrome true` después del bloque. Este PlantUML pinta cada trazo con una paleta, y esa línea no tiene marca escrita propia. El monocromo deja el trazo en un gris oscuro. El nombre del estado sigue siendo la marca.

Una partición se nombra. Su relleno es blanco. En una actividad, la calle se escribe `|#FFFFFF|Nombre|`.

## El único gris

`#8A8A8A` es el tono distinguible de este plugin. No es un valor de la especificación. Úsalo solo en los tres casos que la especificación ya permite, y solo junto a la marca escrita:

- Un miembro heredado conserva el acento `^`. La línea puede ir también en `#8A8A8A`. La caja sigue blanca.
- Un elemento disponible por una importación de paquete, y que no es un elemento empaquetado, puede atenuarse con `#8A8A8A`. Sigue fuera del paquete, o la importación está escrita.
- La visibilidad puede mostrarse con ese tono o con la fuente. La marca `+`, `-`, `#` o `~` se queda.

Cualquier otro relleno, incluida una clase amarilla, un participante azul o una calle de color, se quita.

## Mermaid

El bloque del chat, y el `.md` cuando se escribe uno, abre con esta línea para que la vista secundaria coincida con el PlantUML. La tinta sigue negra. `themeCSS` pinta la hoja de blanco dentro de la figura, para que un editor oscuro no se vea detrás de las líneas y del texto.

```text
%%{init: {'theme': 'base', 'themeVariables': {'background': '#ffffff', 'primaryColor': '#ffffff', 'primaryTextColor': '#000000', 'primaryBorderColor': '#000000', 'lineColor': '#000000', 'textColor': '#000000', 'actorBkg': '#ffffff', 'actorBorder': '#000000', 'actorTextColor': '#000000', 'signalColor': '#000000', 'signalTextColor': '#000000', 'labelTextColor': '#000000', 'loopTextColor': '#000000', 'noteBkgColor': '#ffffff', 'noteTextColor': '#000000', 'noteBorderColor': '#000000', 'activationBkgColor': '#ffffff', 'activationBorderColor': '#000000'}, 'themeCSS': 'svg { background-color: #ffffff !important; }'}}%%
```

## Terminado

Evalúa esta lista en cada diagrama, junto con la lista del skill y la de la referencia del diagrama.

- El `.puml` guardado contiene el cuerpo de `assets/style.puml` después de `@startuml`. No tiene `!include`.
- Los rellenos son `#FFFFFF`. El trazo y el texto son `#000000`. `shadowing` es false. `roundCorner` es 0.
- `#8A8A8A` aparece solo junto a un acento, una importación escrita como tal, o una marca de visibilidad. No aparece ningún otro relleno.
- Una calle de actividad es `|#FFFFFF|Nombre|`.
- Un diagrama de tiempos contiene también `skinparam monochrome true`. Su trazo es un gris oscuro. No es un tono de color.
- El bloque mermaid de la respuesta, y el `.md` cuando existe, empieza con la línea init de arriba.
