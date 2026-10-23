# Diagrams

Editable PlantUML sources are in source/. Exported PNG and SVG files belong in exports/.

## Sources

- source/system-context.puml
- source/use-case.puml
- source/component.puml

These are draft diagrams based on the stated project scope. They do not settle technology, storage, or model-deployment choices.

## Export

Install a Java runtime and the PlantUML command-line tool, then run this from the repository root:

    make -C diagrams export

The Makefile renders both PNG and SVG outputs into exports/. To choose a different PlantUML executable, pass PLANTUML=/path/to/plantuml to make. Do not edit exported files as the only source; update the PlantUML files and regenerate the exports.
