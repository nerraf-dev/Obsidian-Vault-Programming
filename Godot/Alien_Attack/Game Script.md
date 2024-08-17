## The Script
Here is the game script and following that is a breakdown and explanation. 
```GDscript
extends Node2D

# Create references to scene nodes as variables for easier use later
@onready var player = $Player
@onready var hud = $UI/HUD
@onready var ui = $UI
@onready var enemy_hit = $EnemyHit
@onready var explode = $Explode

# Load the game over screen at compile time for use later on.
var game_over_screen = preload("res://scenes/game_over_screen.tscn")
var player_lives = 3
var score = 0

func _ready():
	hud.set_score(score)
	hud.set_lives(player_lives)

# Enemy off-screen deathzone
func _on_death_zone_area_entered(area:Area2D):
	area.queue_free()

# Player took damage
func _on_player_took_damage():
	explode.play()
	player_lives -= 1
	hud.set_lives(player_lives)
	if player_lives == 0:
		player.die()
		print("Game Over!!")
		await(get_tree().create_timer(0.5).timeout)
		var game_over = game_over_screen.instantiate()
		print("score: ", score)
		game_over.set_score(score)
		ui.add_child(game_over)


func _on_enemy_spawner_enemy_spawned(enemy:Variant):
	enemy.connect("died", on_enemy_died)
	# add_child(enemy)

func on_enemy_died():
	score += 100
	hud.set_score(score)
	enemy_hit.play()
	print("Score: ", score)


func _on_enemy_spawner_path_enemy_spawned(path_enemy:Variant):
	# Add child first before connecting signals
	# This is because the path_enemy will emit a signal when it dies
	# and we want to connect to that signal before it is emitted
	add_child(path_enemy)
	path_enemy.enemy.connect("died", on_enemy_died)

```

### Making References to Nodes
```GDscript
extends Node2D

# Create references to scene nodes as variables for easier use later
@onready var player = $Player
@onready var hud = $UI/HUD
@onready var ui = $UI
@onready var enemy_hit = $EnemyHit
@onready var explode = $Explode

```

The script opens with a series of variables called using the `@onready` keyword. These lines of code are commonly used in Godot game development to reference nodes in the scene hierarchy and store them in variables for easier access and manipulation. By using these variables, you can interact with the nodes and their properties, call their methods, or access their child nodes.

1. `@onready var player = $Player`: This line declares a variable named `player` and assigns it the value of `$Player`. The `$` symbol is used in Godot to reference nodes in the scene hierarchy. In this case, it is referencing a node named "Player". The `@onready` keyword ensures that the assignment is done when the script is loaded, so the variable is ready to use.

2. `@onready var hud = $UI/HUD`: Similar to the previous line, this line declares a variable named `hud` and assigns it the value of `$UI/HUD`. It is referencing a node named "HUD" that is a child of a node named "UI".

3. `@onready var ui = $UI`: This line declares a variable named `ui` and assigns it the value of `$UI`. It is referencing a node named "UI".

4. `@onready var enemy_hit = $EnemyHit`: This line declares a variable named `enemy_hit` and assigns it the value of `$EnemyHit`. It is referencing a node named "EnemyHit".

5. `@onready var explode = $Explode`: This line declares a variable named `explode` and assigns it the value of `$Explode`. It is referencing a node named "Explode".

These nodes can be seen in the screenshot below of the game scene
![[01-game_scene_nodes.png]]

### (other) Variables
```GDscript
# Load the game over screen at compile time for use later on.
var game_over_screen = preload("res://scenes/game_over_screen.tscn")
var player_lives = 3
var score = 0
```

`var game_over_screen = preload("res://scenes/game_over_screen.tscn"):`
This line declares a variable named game_over_screen.

The `preload` function is used to load a resource at compile time. In this case, it loads a scene from the specified path `res://scenes/game_over_screen.tscn`. This means that the `game_over_screen` variable will hold a reference to the preloaded scene, which can be instantiated later in the game.

`var player_lives = 3:`
This line declares a variable named player_lives and initialises it with the value 3.
This variable likely keeps track of the number of lives the player has in the game.

`var score = 0:`
This line declares a variable named score and initialises it with the value `0`.
This variable is used to keep track of the player's score in the game.

### \_ready()
```GDscript
func _ready():
	hud.set_score(score)
	hud.set_lives(player_lives)
```

\_ready()is called when the scene and its nodes have loaded. Here we are setting some values in the UI. 

```GDscript
# Enemy off-screen deathzone
# Called when the 'deathzone area' is entered by an Area2D node
# The zone is on layer 4, and detects the enemy on layer 2
# When called it clears the area nodes queue, removing the enemy from the game
func _on_death_zone_area_entered(area:Area2D):
	area.queue_free()


# Player took damage
# Called when a custom signal "took_damage" is called in the enemy script
func _on_player_took_damage():
	explode.play()
	player_lives -= 1
	hud.set_lives(player_lives)
	if player_lives == 0:
		player.die()
		print("Game Over!!")
		await(get_tree().create_timer(0.5).timeout)
		var game_over = game_over_screen.instantiate()
		print("score: ", score)
		game_over.set_score(score)
		ui.add_child(game_over)



func _on_enemy_spawner_enemy_spawned(enemy:Variant):
	enemy.connect("died", on_enemy_died)
	# add_child(enemy)

func on_enemy_died():
	score += 100
	hud.set_score(score)
	enemy_hit.play()
	print("Score: ", score)


func _on_enemy_spawner_path_enemy_spawned(path_enemy:Variant):
	# Add child first before connecting signals
	# This is because the path_enemy will emit a signal when it dies
	# and we want to connect to that signal before it is emitted
	add_child(path_enemy)
	path_enemy.enemy.connect("died", on_enemy_died)

```

The provided GDScript code is part of a game script that handles enemy spawning and the player's score in the Godot Engine. The script defines three functions: `_on_enemy_spawner_enemy_spawned`, `on_enemy_died`, and `_on_enemy_spawner_path_enemy_spawned`.

The `_on_enemy_spawner_enemy_spawned` function is called whenever a new enemy is spawned. It takes an `enemy` parameter. Inside this function, the `enemy` object is connected to a signal named `"died"`, which triggers the `on_enemy_died` function when the enemy dies. 

The `on_enemy_died` function is responsible for handling the event when an enemy dies. When called, it increments the `score` variable by 100 points. It then updates the HUD (Heads-Up Display) to reflect the new score by calling `hud.set_score(score)`. Additionally, it plays a sound effect using `enemy_hit.play()` and prints the updated score to the output pane with `print("Score: ", score)`. This function ensures that the player receives immediate feedback when an enemy is defeated.

The `_on_enemy_spawner_path_enemy_spawned` function is similar to `_on_enemy_spawner_enemy_spawned`, but it deals with a `path_enemy` parameter. This function first adds the `path_enemy` to the scene tree using `add_child(path_enemy)`. This step is crucial because the `path_enemy` will emit a signal when it dies, and the script needs to connect to that signal before it is emitted. After adding the `path_enemy` to the scene, the function connects the `died` signal of the `path_enemy.enemy` to the `on_enemy_died` function, ensuring that the score is updated and other actions are taken when the path enemy dies.

