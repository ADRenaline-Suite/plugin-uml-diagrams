# adrenaline-uml-diagrams

Draws UML 1.5 and UML 2.5.1 diagrams. The procedure is in `skills/generate-diagram/SKILL.md`. Each type and version has its manual in `skills/generate-diagram/references/`.

Each diagram is saved as a `.puml` source and its rendered `.svg` in `uml-diagrams/` at the project root, or in the path that `.cursor/adrenaline.json` sets under `outputDirs["adrenaline-uml-diagrams"]`. Classes, sequence, and states also get a Mermaid `.md`, following `skills/generate-diagram/references/mermaid.md`.

The two versions of the notation are not mixed. If PlantUML does not draw the type natively, the manual says so and the delivery does too.
