# How to make custom commands

  - [Java](#java)
    - [Trigger](#trigger)
  - [Functions](#functions)
  - [Bedrock](#bedrock)

## Java
### Trigger

In the Java edition of the game, you can create scoreboard objectives with the `trigger` criteria, this scorebaord objective can be changed by non-operator players.

```mcfunction
scorebaord objectives add example_trigger trigger
```

This command changes a score, so we can run a command as any player with a score of 1 or above. After that, we reset the score so it does not trigger each tick. Last, we need to enable the objective, if the score is not enabled, players can not run the command.

```mcfunction
# Command blocks
execute as @a[scores={example_trigger=1..}] run say I triggered the command
scoreboard players reset @a example_trigger
scoreboard players enable @a example_trigger
```

Any player that wants to run the command must type the `trigger` command in chat:

```mcfunction
/trigger example_trigger
```

It is possible to add multiple options to one command (like arguments) but it's limited to only 32 bit integers (without the 0, since it is the "default" state). You could perform one acation if the score is 1 and another action if it is 2 and so on.

## Functions

Functions could be considered custom commands, but only works for operator players. The adventage of them is that they can take macro arguments as inputs.

## Bedrock
For bedrock, check this detailed article for behavior packs https://wiki.bedrock.dev/scripting/custom-commands.