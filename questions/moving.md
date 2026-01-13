# Detect the player moving

  - [Java](#java)
    - [Predicate](#predicate)
    - [Commands](#commands)
  - [Bedrock](#bedrock)

## Java
### Predicate
To detect the player moving, you can use the following predicate

```json
{
  "condition": "minecraft:entity_properties",
  "entity": "this",
  "predicate": {
    "movement": {
      "horizontal_speed": {
        "min": 0.01
      }
    }
  }
}
```
This can be used as a target selector `@e[predicate=...]` or with `execute if predicate`, but then it must be `as` an entity

### Commands
In older versions, where this predicate didn't exist, you can store the position values and compare to the previous tick

```mcfunction
# In chat
scoreboard objectives add Pos.x dummy
scoreboard objectives add Pos.x.copy dummy
scoreboard objectives add Pos.z dummy
scoreboard objectives add Pos.z.copy dummy

# Command blocks
execute as @a run scoreboard players operation @s Pos.x.copy = @s Pos.x
execute as @a run scoreboard players operation @s Pos.z.copy = @s Pos.z
execute as @a store result score Pos.x run data get entity @s Pos[0] 100
execute as @a store result score Pos.z run data get entity @s Pos[2] 100
execute as @a unless score @s Pos.x = @s Pos.x.copy run say I'm moving on the x axis
execute as @a unless score @s Pos.z = @s Pos.z.copy run say I'm moving on the z axis
```

We have 4 scoreboards. `Pos.x` and `Pos.z` will be where the position will be stored and the `.copy` scoreboards contains the value of the previous tick.

First, we copy the values from the previous tick into the copy scoreboards (multiplied by 100 to retain decimal places), then, we update the current values from the data of the player `Pos[0]` and `Pos[2]`.

Last, we compare if the values aren't the same, if they aren't, we know The player moved.

If you want to run a command when the player moves with this method but don't care if it's the X or Z axis then you can change the last 2 commands to add a tag, the run any command as the player with the tag and lastly remove the tag.

```mcfunction
execute as @a unless score @s Pos.x = @s Pos.x.copy run tag @s add moving
execute as @a unless score @s Pos.z = @s Pos.z.copy run tag @s add moving
execute as @a[tag=moving] run say I'm moving
tag @a remove moving
```

## Bedrock
For bedrock, check this detailed article https://wiki.bedrock.dev/commands/movement-detections#is-moving.