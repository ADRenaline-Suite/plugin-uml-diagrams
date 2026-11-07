<p align="right">Language:&emsp;<img alt="English" src="https://raw.githubusercontent.com/ADRenaline-Suite/.github/main/profile/lang-en-on.svg" align="middle" style="vertical-align:middle"> <a href="style.es.md" style="vertical-align:middle"><img alt="Español" src="https://raw.githubusercontent.com/ADRenaline-Suite/.github/main/profile/lang-es-off.svg" align="middle" style="vertical-align:middle"></a></p>

[🏠 UML Diagrams](../../../README.md) / [Generate a UML diagram](../SKILL.md)

# Presentation

Source: OMG UML 2.5.1, clause 6.4.1. The same clause covers UML 1 drawings in this plugin: one presentation, both versions.

## What the specification fixes

Notation is read as black on a white background. A conforming tool may use another scheme. In that scheme, black means solid, white means unfilled, and gray means a tone that can be told apart from both. Font, line thickness, and arrowhead size may differ. Those differences do not change the model.

A fill that carries no written mark is not notation. The diagram stays readable in gray.

## What every diagram uses

Paste the body of [../assets/style.puml](../assets/style.puml) into the `.puml`, on the line after `@startuml`. The templates in `assets/` use `!include style.puml` because that file sits beside them. A file saved in the output folder does not: the include would point outside that folder. Expand it.

The block sets a white canvas, white fills, black strokes and text, no shadow, and square corners. The face is SansSerif, the body is 13, the title is 14, the arrow is 1 thick, and the gap is padding 8 with nodesep 40 and ranksep 40. Those numbers are choices of this plugin. They are not values in the specification. `classAttributeIconSize 0` keeps visibility as `+`, `-`, `#`, and `~`.

`skinparam componentStyle uml2` stays in the UML 2 component template. It chooses the symbol. It is not part of this block.

`hide circle` drops the circled letter PlantUML puts in a class header. That letter is not UML notation.

A timing diagram adds `skinparam monochrome true` after the block. This PlantUML paints each trace from a palette, and that line has no written mark of its own. Monochrome keeps the trace a dark stroke. The state name stays the mark.

A partition is named. Its fill is white. In an activity, write the lane as `|#FFFFFF|Name|`.

## The only gray

`#8A8A8A` is this plugin's distinguishable tone. It is not a value in the specification. Use it only in the three cases the specification already allows, and only together with the written mark:

- An inherited member keeps the caret `^`. The line may also be `#8A8A8A`. The box stays white.
- An element available through a package import, and not a packaged element, may be dimmed with `#8A8A8A`. It stays outside the package, or the import is written.
- Visibility may be shown with that tone or with the face. The mark `+`, `-`, `#`, or `~` stays.

Any other fill, including a yellow class, a blue participant, or a colored lane, is removed.

## Mermaid

The chat block, and the `.md` when one is written, opens with this line so the secondary view matches the PlantUML. The ink stays black. `themeCSS` paints the sheet white inside the figure, so a dark editor does not show through behind the lines and the text.

```text
%%{init: {'theme': 'base', 'themeVariables': {'background': '#ffffff', 'primaryColor': '#ffffff', 'primaryTextColor': '#000000', 'primaryBorderColor': '#000000', 'lineColor': '#000000', 'textColor': '#000000', 'actorBkg': '#ffffff', 'actorBorder': '#000000', 'actorTextColor': '#000000', 'signalColor': '#000000', 'signalTextColor': '#000000', 'labelTextColor': '#000000', 'loopTextColor': '#000000', 'noteBkgColor': '#ffffff', 'noteTextColor': '#000000', 'noteBorderColor': '#000000', 'activationBkgColor': '#ffffff', 'activationBorderColor': '#000000'}, 'themeCSS': 'svg { background-color: #ffffff !important; }'}}%%
```

## Done

Evaluate this list for every diagram, together with the skill list and the list of the diagram reference.

- The saved `.puml` contains the body of `assets/style.puml` after `@startuml`. It has no `!include`.
- Fills are `#FFFFFF`. Strokes and text are `#000000`. `shadowing` is false. `roundCorner` is 0.
- `#8A8A8A` appears only beside a caret, an import written as such, or a visibility mark. No other fill appears.
- An activity lane is `|#FFFFFF|Name|`.
- A timing diagram also contains `skinparam monochrome true`. Its trace is a dark stroke. It is not a hue.
- The mermaid block in the reply, and the `.md` when it exists, starts with the init line above.
