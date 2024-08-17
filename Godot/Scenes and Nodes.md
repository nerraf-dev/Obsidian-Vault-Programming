In Godot, the concepts of nodes and scenes are fundamental to the engine's architecture and workflow.

### Nodes
- The basic building blocks in Godot.
	- Each node performs a specific function, such as displaying graphics, playing sounds, handling physics, or managing user input.
- Organised in a tree structure.
	- Each node can have multiple child nodes, creating a parent-child relationship. This hierarchy allows for complex scene structures and inheritance of transformations and properties.
- There are various types of nodes, such as `Node2D` for 2D games, `Spatial` for 3D games, `Control` for UI elements, and many more.

### Scenes
- A scene is a collection of nodes organised in a tree structure. It represents a distinct part of the game, such as a level, a character, or a UI element.
- Scenes can be saved as separate files and reused across the project. This modularity allows for efficient management and reuse of game components.
- Scenes can be instantiated multiple times, allowing for the creation of multiple copies of the same structure with different properties or states.

### Example
Consider a simple game where you have a player character and enemies:

- **Player Scene**: This scene might include nodes for the player's sprite, collision shape, and scripts for movement and actions.
- **Enemy Scene**: This scene might include nodes for the enemy's sprite, collision shape, and scripts for AI behaviour.
- **Main Scene**: This scene might include instances of the player and enemy scenes, along with other nodes for the game world, UI, and game logic.

