

Consists of the following scenes:
```
bullet.tscn
enemy_spawner.tscn
game_over_screen.tscn
path_enemy.tscn
rocket.tscn
enemy.tscn
game.tscn
hud.tscn
player.tscn
```

Scripts:
```
bullet.gd
enemy_spawner.gd
game_over_screen.gd
path_enemy.gd
enemy.gd
game.gd
hud.gd
player.gd
```


game.tscn:
![[01-game_scene_nodes.png]]
This is the main scene for the application. 
The root node is a [[Node2D]] element. This node holds the child nodes that make up the scene. The scene contains UI elements, the background, control elements (the DeathZone!), and also instances of the [[Player]] and [[EnemySpawner]] scenes. It also contains nodes for playing audio. 

- The [[CanvasLayer]] node, named UI to hold UI elements. The Canvas layer is useful as this automatically starts on a higher level layer than other nodes, ensuring it is visible. 
- [[TextureRect]] holds the background texture image.
- [[Aread2D]] called [[DeathZone]] for controlling enemy sprites when they leave the screen.
- EnemyHit and Explode are [[AudioStreamPlayer2D]] nodes for playing sound files.
- [[Player]] and [[EnemySpawner]] are instances of other scenes.


