The map has to be constructed with 3 components:
- walls
- collectibles
- and free space.

The map can be composed of only these 5 characters:
- 0 for an empty space,
- 1 for a wall,
- C for a collectible,
- E for a map exit,
- P for the player’s starting position.

Here is a simple valid map:

```
1111111111111
10010000000C1
1000011111001
1P0011E000001
1111111111111
```

- The map must contain **1 exit**, at least **1 collectible**, and **1 starting position** to be valid.

- If the map contains a duplicates characters (exit/start), you should display an error message.

- The map must be rectangular.
- The map must be closed/surrounded by walls. If it’s not, the program must return an error.
- You have to check if there’s a valid path in the map.
- You must be able to parse any kind of map, as long as it respects the above rules.
- Another example of a minimal `.ber` map:

```
1111111111111111111111111111111111
1E0000000000000C00000C000000000001
1010010100100000101001000000010101
1010010010101010001001000000010101
1P0000000C00C0000000000000000000C1
1111111111111111111111111111111111
```

- If any misconfiguration of any kind is encountered in the file, the program must exit in a clean way, and return "Error\n" followed by an explicit error message of your choice.
