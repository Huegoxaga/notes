# PlantUML

- It is a graphing tool for various diagram written in Java
- Graph are generated base on PlantUML syntax in files with extension like `.wsd`
- It provide a server to generate image links based

## Installation

- To use on VS Code `Ctrl + P`, `ext install plantuml`.
- Select a server to render the script to images:
  - Use official server - Select `PlantUMLServer` in the plugin setting
  - Use Local Server: Select `Local` in the plugin setting, Install `Java`, and `Graphviz` for local image rendering. `brew cask install java`(If java is not on the machine), `brew install graphviz`.
- Select the exported image URL hosting server
  - Use official server, enter `https://www.plantuml.com/plantuml` in the plugin setting for `plantuml.server`

## Usage

- `Alt + D` preview
- In VS Code `Ctrl + P` type `>PlantUML` then select Export as `png` or `url`.

## Syntax

- Use `'` for inline comments.
- Use `skinparam linetype ortho` select line style
- Use `hide circle` to hide circles in front of entity names
- `title Hello World` add title
- Define Entity
  ```
  entity "(auth_user_groups)" as e18 {
    *id : int <<generated>>
    --
    *user_id : int <<FK>>
    *group_id : int <<FK>>
  }
  ```
- Define Relationship
  - `e01 ||--|| e02` one-to-one
  - `e01 }|--|| e02` or `e02 ||--|{ e01` one-to-many
  - `e01 }|--|{} e02` many-to-many
  - See more [here](https://plantuml.com/class-diagram)
