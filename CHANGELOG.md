# Changelog

## [0.2.0] - 2026-10-25

### Changed

- The diagram title and the labels follow the language of the request. The skill and the commands stay in English. `STATUS.md` columns stay `N`, `archivo`, `estado`, `sustituye`, `notas`.
- `/uml-help` links each command to its manual on GitHub. The `description` is `ADRenaline. Help: catalog of adrenaline-uml-diagrams (skills, rules, commands).`
- Each command `description` names the diagram and the question it answers, so the command picker is readable without knowing the type. `/uml-help` repeats that sentence.
- Each diagram manual has three copyable examples. The first is the short command `/uml-<id>` with only the domain; then the command that fixes the content; then the sentence that names the diagram.

### Added

- Rule `output-folder`: diagrams are saved in `uml-diagrams/`, or in the path set by `.cursor/adrenaline.json` under `outputDirs["adrenaline-uml-diagrams"]`.
- Mermaid as a secondary format for class, sequence, and state diagrams: `<folder>/<NNN>-<id>-<topic>.md`, following the new reference `references/mermaid.md`.
- Claude Code support: manifest `.claude-plugin/plugin.json` and marketplace `.claude-plugin/marketplace.json`, so the repository installs with `claude plugin marketplace add d-mente/adrenaline-uml-diagrams`.
- `author` in both manifests.
- Delivery keeps `<folder>/STATUS.md` (`proposed` | `accepted` | `deprecated` | `superseded`) and prefers `accepted` over newer drafts.
- Command `/uml-help`: one-line catalog of the plugin (skills, rules, commands, output). The output lists each file format with a short description.
- Skill `generate-diagram`, section "Fidelity": what the user asked for or approved wins over the readability guide. Nothing is dropped without saying so; simplifying or splitting needs the user's request and a new `<NNN>`.
- Skill `generate-diagram`, section "Save a diagram from the conversation": a diagram already shown or pasted is saved one to one, with its type and version taken from the diagram itself.
- Delivery lines `Fidelity` (as asked, or the list of changes) and `Guide` (within, or beyond with how it could be split).

### Changed

- Skill `generate-diagram` saves files as `<folder>/<NNN>-<id>-<topic>.puml` (and `.svg`), with monotonic `<NNN>` that is never reused for another diagram.
- Skill `generate-diagram` no longer asks when the topic already exists: it edits the same `<NNN>` if the user amends that view; otherwise it allocates the next `<NNN>` and marks the previous row `superseded` in `STATUS.md`. It does not offer to extend the model.
- Skill `generate-diagram` states the notation limits of the `uml-notation` rule, because Claude Code and other agents do not load rules.
- Commands name the `generate-diagram` skill instead of a path from the plugin root, so they resolve in Cursor and in Claude Code.
- Every reference states that "Diagram that is easy to read" is a guide for when the user leaves the content open, not a limit on what the user asked for.
- Skill `generate-diagram` resolves the version without contradiction: a command fixes it; a diagram in the conversation or a construct of only one version (`alt`, ports, pins, token flow) sets it; otherwise UML 2 is proposed and confirmed. The catalog column is now "Version to propose".

### Fixed

- Command `/uml-help`: the `description` is quoted, so its frontmatter is valid YAML and the command loads.

## [0.1.0] - 2026-10-18

### Added

- Skill `generate-diagram` for UML 1.5 and UML 2.5.1.
- One reference, one PlantUML template, and one command for each diagram in the catalog.
- Rule `uml-notation`, so the two versions are not mixed.
