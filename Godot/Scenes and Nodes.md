In Godot, the concepts of nodes and scenes are fundamental to the engine's architecture and workflow.

### Nodes
- **Definition**: Nodes are the basic building blocks in Godot. Each node performs a specific function, such as displaying graphics, playing sounds, handling physics, or managing user input.
- **Hierarchy**: Nodes are organised in a tree structure. Each node can have multiple child nodes, creating a parent-child relationship. This hierarchy allows for complex scene structures and inheritance of transformations and properties.
- **Types**: There are various types of nodes, such as `Node2D` for 2D games, `Spatial` for 3D games, `Control` for UI elements, and many more.

### Scenes
- **Definition**: A scene is a collection of nodes organized in a tree structure. It represents a distinct part of the game, such as a level, a character, or a UI element.
- **Reusable**: Scenes can be saved as separate files and reused across the project. This modularity allows for efficient management and reuse of game components.
- **Instancing**: Scenes can be instantiated multiple times, allowing for the creation of multiple copies of the same structure with different properties or states.

### Example
Consider a simple game where you have a player character and enemies:

- **Player Scene**: This scene might include nodes for the player's sprite, collision shape, and scripts for movement and actions.
- **Enemy Scene**: This scene might include nodes for the enemy's sprite, collision shape, and scripts for AI behavior.
- **Main Scene**: This scene might include instances of the player and enemy scenes, along with other nodes for the game world, UI, and game logic.

### Code Example
In the provided code excerpt, nodes and scenes are being manipulated:

- [`ui.add_child(game_over)`](command:_github.copilot.openSymbolFromReferences?%5B%22%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22path%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A35%2C%22character%22%3A2%7D%7D%5D%5D "Go to definition"): Adds the [`game_over`](command:_github.copilot.openSymbolFromReferences?%5B%22%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22path%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A35%2C%22character%22%3A15%7D%7D%5D%5D "Go to definition") node as a child to the [`ui`](command:_github.copilot.openSymbolFromReferences?%5B%22%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22path%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A35%2C%22character%22%3A2%7D%7D%5D%5D "Go to definition") node.
- [`enemy.connect("died", on_enemy_died)`](command:_github.copilot.openSymbolFromReferences?%5B%22%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22path%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A38%2C%22character%22%3A37%7D%7D%5D%5D "Go to definition"): Connects the [`died`](command:_github.copilot.openSymbolFromReferences?%5B%22%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22path%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A39%2C%22character%22%3A16%7D%7D%5D%5D "Go to definition") signal of the [`enemy`](command:_github.copilot.openSymbolFromReferences?%5B%22%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22path%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A38%2C%22character%22%3A37%7D%7D%5D%5D "Go to definition") node to the [`on_enemy_died`](command:_github.copilot.openSymbolFromReferences?%5B%22%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22path%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A39%2C%22character%22%3A23%7D%7D%5D%5D "Go to definition") function.
- [`path_enemy.enemy.connect("died", on_enemy_died)`](command:_github.copilot.openSymbolFromReferences?%5B%22%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22path%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A49%2C%22character%22%3A42%7D%7D%5D%5D "Go to definition"): Connects the [`died`](command:_github.copilot.openSymbolFromReferences?%5B%22%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22path%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A39%2C%22character%22%3A16%7D%7D%5D%5D "Go to definition") signal of the [`path_enemy.enemy`](command:_github.copilot.openSymbolFromReferences?%5B%22%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22path%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A49%2C%22character%22%3A42%7D%7D%5D%5D "Go to definition") node to the [`on_enemy_died`](command:_github.copilot.openSymbolFromReferences?%5B%22%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22path%22%3A%22%2FUsers%2Fsimon%2FGodot_Projects%2Fgodot_2d_course_projects%2FAlien_Attack%2Fscripts%2Fgame.gd%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A39%2C%22character%22%3A23%7D%7D%5D%5D "Go to definition") function.

These operations demonstrate how nodes are added to the scene tree and how signals are used to handle events within the node hierarchy.