
Create a new project.
Create a new scene - `level`

**Using Pixel Art:**
Looks blurry, so need to set the texture filter:
![[01-TextureFilter.png]]

Goto **Project Settings** and change the **Default Texture Filter**

![[02-textureFilter.png]]

If pixel art is too small:

You can use transform > scale but has to be changed in each sprite.

or can change viewport size. Change to smaller size view port, e.g. 1920 / 4 wide, and change the stretching
![[03-ProjSettings-Viewport.png]]



Creating the Player:

![[04-player_scene.png]]

The player scene is a `CharacterBody2D` root node, along with `AnimatedSprite2D` and `CollisionShape2D` child nodes.

With the `AnimatedSprite2D` selected, create a set of new Sprite Frames
![[05-new_sprite_frames.png]]

The **Animations** Panel:

![[06-AnimationsPanel.png]]

Create additional animations using the "Add Animation" button.
If adding an animation sprite sheet, use the "Add frames..." button (looks like a grid).
![[07-Animation_Window.png]]

Enter the settings to match the sheet. IN this example the sprite sheet contains a single row of 11 objects. Set the corresponding horizontal and vertical values:
```
H: 11
V: 1
```

The size will autocomplete and should match the sheet. 
Select the frames that should be included in the animation and click the Add button. 

For a single frame the folder icon or drag the sprite image into the frame space. 

