### Table of contents:
- [Functions](#functions)
  - [Player](#player)
  - [Blocks](#blocks)
  - [Mobs](#mobs)
  - [Agent](#agent)
  - [Gameplay](#gameplay)
  - [Position](#position)
  - [Math](#math)
- [Classes](#classes)
- [Enums](#enums)
- [Types](#types)
- [Constants](#constants)
- [Other](#other)
    
# Functions

## Player

* #### `player.on_chat(command, handler)`

  **Description:** Runs code when you type a certain message in the game chat
  
  **Parameters:**

  * `command`: `str` – the chat keyword that will be associated with this command (`*` for all messages), e.g. “jump”
  * `handler`: `(number, number, number) -> None` – code to run when the keyword is typed in the chat by the current player

* #### `player.on_item_interacted(item, handler)`

  **Description:** Runs code when an item is used
  
  **Parameters:**

  * `item`: `number` – the type of item used that will cause the code to run, such as: `TRIDENT`
  * `handler`: `() -> None` – the code to run when the item is used by the current player

* #### `player.say(message)`

  **Description:** Posts a message to the game chat
  
  **Parameters:**

  * `message`: `any` – the message to display in the chat, e.g. “Hi!”

* #### `player.teleport(to)`

  **Description:** Teleports the current player to another position
  
  **Parameters:**

  * `to`: `Position` – the destination position

* #### `player.on_travelled(method, handler)`

  **Description:** Runs code when the current player travels in a certain way
  
  **Parameters:**

  * `method`: `TravelMethod` – the travel method. Available methods: walk, swim water, fall, climb, swim lava, fly, riding, sneak, sprint, bounce
  * `handler`: `() -> None` – code to run when the player travels

* #### `player.on_died(handler)`

  **Description:** Runs code when the current player dies
  
  **Parameters:**

  * `handler`: `() -> None` – code to run when the current player dies

* #### `player.position()`

  **Description:** Returns the world position of the current player
  
  **Parameters:**
  *(none)*

* #### `player.get_orientation()`

  **Description:** Returns the player's orientation, in degrees
  
  **Parameters:**
  *(none)*

* #### `player.name()`

  **Description:** Returns the name of the current player (you)
  
  **Parameters:**
  *(none)*

* #### `player.execute(command)`

  **Description:** Executes a game command as the current player
  
  **Parameters:**

  * `command`: `str` – the slash command to execute (you do not have to put the leading `/`), e.g. “say Hi!”

* #### `player.tell(target, message)`

  **Description:** Whispers a message to targets
  
  **Parameters:**

  * `target`: `TargetSelector` – a selector of entities
  * `message`: `any` – the text to whisper, e.g. “Hi!”

* #### `player.on_arrow_shot(handler)`

  **Description:** Runs code when the current player shoots an arrow
  
  **Parameters:**

  * `handler`: `() -> None` – code to run when the player shoots an arrow

* #### `player.run_chat_command(command)`

  **Description:** Executes a chat command in your code
  
  **Parameters:**

  * `command`: `str` – the chat command to run, like “jump”

* #### `player.run_chat_command_with_arguments(command, arg)`

  **Description:** Executes a chat command in your code with arguments
  
  **Parameters:**

  * `command`: `str` – the chat command to run, like “jump”
  * `arg`: `str` – a string containing all the arguments you wish to give to the chat command

* #### `player.on_tell_command(command, handler)`

  **Description:** Runs code when another player whispers you a certain message
  
  **Parameters:**

  * `command`: `str` – the chat keyword that will be associated with this command (`*` for all messages), e.g. “jump”
  * `handler`: `() -> None` – code to run when the keyword is whispered to the current player

* #### `player.on_teleported(handler)`

  **Description:** Runs code when the current player gets teleported
  
  **Parameters:**

  * `handler`: `() -> None` – code to run when the player gets teleported

* #### `player.chat_command_syntax_error(helpStr)`

  **Description:** Displays a chat command help message in the game chat
  
  **Parameters:**

  * `helpStr`: `str` – the help message to display

* #### `player.error_message(msg, multiline)`

  **Description:** Displays an error in the game chat
  
  **Parameters:**

  * `msg`: `str` – the error to display in the game chat
  * `multiline`: `bool` – whether the message is multiline

* #### `player.get_chat_arg(index)`

  **Description:** Gets the specified argument from the latest player chat message
  
  **Parameters:**

  * `index`: `number` – index of the argument

* #### `player.get_chat_args(command)`

  **Description:** Gets the arguments for the specified command
  
  **Parameters:**

  * `command`: `str`

* #### `player.message()`

  **Description:** Gets the last message, if any
  
  **Parameters:**
  *(none)*

* #### `player.on_chat_command_core(command, handler)`

  **Description:** Runs code when a keyword is typed in the chat
  
  **Parameters:**

  * `command`: `str` – the chat keyword to listen for
  * `handler`: `() -> None` – code to run when the keyword is typed

* #### `player.warning_message(msg, multiline)`

  **Description:** Displays a warning in the game chat (orange text)
  
  **Parameters:**

  * `msg`: `str` – the warning to display in the game chat
  * `multiline`: `bool` – whether the message is multiline

---

## Blocks

* #### `blocks.place(block, pos)`

  **Description:** Places a block in the world
  
  **Parameters:**

  * `block`: `number` – the block to place
  * `pos`: `Position` – the position at which to place the block

* #### `blocks.on_block_placed(block, handler)`

  **Description:** Runs code when a certain type of block is placed
  
  **Parameters:**

  * `block`: `number` – the type of block that, when it is placed, will start some code
  * `handler`: `() -> None` – the code to run when the selected block type is placed in the world

* #### `blocks.on_block_broken(block, handler)`

  **Description:** Runs code when a certain type of block is mined or broken
  
  **Parameters:**

  * `block`: `number` – the type of block that, when it is broken, will start some code
  * `handler`: `() -> None` – the code to run when the selected block type is mined or broken

* #### `blocks.test_for_block(block, pos)`

  **Description:** Tests whether the block at the specified coordinate is of a certain type
  
  **Parameters:**

  * `block`: `number` – the type of the block to test for
  * `pos`: `Position` – the position (coordinates) where you want to check for the block

* #### `blocks.fill(block, from, to, operator)`

  **Description:** Fills a volume between two positions
  
  **Parameters:**

  * `block`: `number` – the block used to fill the region
  * `from`: `Position` – the first corner of the cubic region
  * `to`: `Position` – the opposite corner of the cubic region
  * `operator`: `FillOperation` – what happens to the existing blocks in the region

* #### `blocks.print(text, block, position, direction)`

  **Description:** Creates the specified text in the game world, made of the specified block, at the given location
  
  **Parameters:**

  * `text`: `str` – the text to print in the world, e.g. “HELLO”
  * `block`: `number` – the block type used to create the text
  * `position`: `Position` – the position where the text is printed in the world
  * `direction`: `CompassDirection` – the direction (axis) along which the text is printed

* #### `blocks.block_with_data(b, data)`

  **Description:** Represents a block or item from the game with a data value
  
  **Parameters:**

  * `b`: `number` – the block or item
  * `data`: `number` – the data value for the block or item

* #### `blocks.block_by_id(id)`

  **Description:** Represents a block or item from the game by its value ID
  
  **Parameters:**

  * `id`: `number` – the ID of the block or item from the game

* #### `blocks.block_by_name(name)`

  **Description:** Represents a block or item from the game by its code name
  
  **Parameters:**

  * `name`: `str` – the name of the block, e.g. “stone”

* #### `blocks.lever(position)`

  **Description:** Creates a lever in a particular state
  
  **Parameters:**

  * `position`: `LeverPosition` – the position/state of the lever

* #### `blocks.repeater(direction, delay)`

  **Description:** Creates a repeater in a particular state
  
  **Parameters:**

  * `direction`: `CompassDirection` – the direction in which the repeater is facing
  * `delay`: `number` – the delay time for the repeater, in game ticks

* #### `blocks.comparator(direction, mode)`

  **Description:** Creates a comparator in a particular state
  
  **Parameters:**

  * `direction`: `CompassDirection` – the direction which the comparator is facing
  * `mode`: `ComparatorMode` – the comparison mode of the comparator

* #### `blocks.replace(newblock, oldblock, from, to)`

  **Description:** Replaces all the blocks of a certain type inside the specified region with a new block type
  
  **Parameters:**

  * `newblock`: `number` – the new block type that replaces existing blocks
  * `oldblock`: `number` – the block type that is replaced
  * `from`: `Position` – the first corner of the cubic region
  * `to`: `Position` – the opposite corner of the cubic region

* #### `blocks.clone(begin, end, destination, mask, mode)`

  **Description:** Clones a cubic region into a different location
  
  **Parameters:**

  * `begin`: `Position` – the first corner of the cubic region
  * `end`: `Position` – the opposite corner of the cubic region
  * `destination`: `Position` – the first corner of the destination region
  * `mask`: `CloneMask` – how to handle air blocks (replace or masked)
  * `mode`: `CloneMode` – how to handle the cloned region

* #### `blocks.clone_filtered(begin, end, destination, block, mode)`

  **Description:** Clones a cubic region into a different location, if the blocks in the region match a certain block type
  
  **Parameters:**

  * `begin`: `Position` – the first corner of the cubic region
  * `end`: `Position` – the opposite corner of the cubic region
  * `destination`: `Position` – the first corner of the destination region
  * `block`: `number` – the block type to look for when cloning
  * `mode`: `CloneMode` – how to handle the cloned region

* #### `blocks.save_structure(name, from, to, includeEntities, saveMode, includeBlocks)`

  **Description:** Saves the structure within a range of positions as a named object
  
  **Parameters:**

  * `name`: `str` – the name of the structure
  * `from`: `Position` – the starting position
  * `to`: `Position` – the ending position
  * `includeEntities`: `bool` – whether to include entities
  * `saveMode`: `unknown` – where the structure is saved (memory or disk)
  * `includeBlocks`: `bool` – whether to include blocks

* #### `blocks.load_structure(name, to, rotation, mirror, animationMode, animationSeconds, includeEntities, includeBlocks, integrity)`

  **Description:** Loads a structure with the given name at the specified position
  
  **Parameters:**

  * `name`: `str` – the name of the structure
  * `to`: `Position` – the position to load the structure at
  * `rotation`: `number` – degrees to rotate (0°, 90°, 180°, 270°)
  * `mirror`: `number` – the mirroring axis
  * `animationMode`: `StructureAnimationMode` – the animation type
  * `animationSeconds`: `number` – duration of the animation in seconds
  * `includeEntities`: `bool` – whether to include entities
  * `includeBlocks`: `bool` – whether to include blocks
  * `integrity`: `number` – how exactly to place blocks and entities (0–100)

* #### `blocks.delete_structure(name)`

  **Description:** Deletes the structure with the given name from memory
  
  **Parameters:**

  * `name`: `str` – the name of the structure to delete

* #### `blocks.name_of_block(block)`

  **Description:** Returns the name of the specified block
  
  **Parameters:**

  * `block`: `number` – the block to get the name of

* #### `blocks.test_for_blocks(begin, end, destination, mask)`

  **Description:** Tests whether the blocks in two regions match
  
  **Parameters:**

  * `begin`: `Position` – the first corner of the first region
  * `end`: `Position` – the opposite corner of the first region
  * `destination`: `Position` – the first corner of the second region
  * `mask`: `TestForBlocksMask` – how blocks are compared


---

## Mobs

* #### `mobs.spawn(mob, destination)`

  **Description:** Summons a creature at a given location. To spawn monster mobs, the world difficulty must be set to something higher than Peaceful (Easy, Normal, or Hard).
  
  **Parameters:**

  * `mob`: `number` – the type of creature to spawn
  * `destination`: `Position` – the position where the creature is spawned

* #### `mobs.on_mob_killed(mob, handler)`

  **Description:** Runs code when a creature of a certain type is killed
  
  **Parameters:**

  * `mob`: `number` – the type of creature
  * `handler`: `() -> None` – the code to run when the selected creature type is killed

* #### `mobs.kill(target)`

  **Description:** Kills the selected entities
  
  **Parameters:**

  * `target`: `TargetSelector` – a selector that chooses which mobs are killed

* #### `mobs.monster(name)`

  **Description:** Represents a monster from the game. To spawn monster mobs, the world difficulty must be set to something higher than Peaceful (Easy, Normal, or Hard).
  
  **Parameters:**

  * `name`: `MonsterMob` – the type of the monster

* #### `mobs.apply_effect(effect, target, duration, amplifier)`

  **Description:** Applies a status effect to the specified target
  
  **Parameters:**

  * `effect`: `number` – the effect to apply (e.g. `Effect.Speed`, `Effect.Hunger`)
  * `target`: `TargetSelector` – the player(s) or entities to apply the effect to
  * `duration`: `number` – the number of seconds the effect is applied for
  * `amplifier`: `number` – the strength multiplier for the effect (0–127)

* #### `mobs.clear_effect(target)`

  **Description:** Clears all status effects from the specified target
  
  **Parameters:**

  * `target`: `TargetSelector` – the player(s) or entities to remove all effects from

* #### `mobs.give(target, block, amount)`

  **Description:** Gives blocks or items from the game to the specified players
  
  **Parameters:**

  * `target`: `TargetSelector` – determines which players receive the item
  * `block`: `number` – the block or item to give
  * `amount`: `number` – how many to give, e.g. 1

* #### `mobs.teleport_to_position(target, destination)`

  **Description:** Teleports entities to another location
  
  **Parameters:**

  * `target`: `TargetSelector` – selects which entities are teleported
  * `destination`: `Position` – the position where the entities are teleported to

* #### `mobs.teleport_to_player(target, destination)`

  **Description:** Teleports entities to a player
  
  **Parameters:**

  * `target`: `TargetSelector` – selects which entities will be teleported
  * `destination`: `TargetSelector` – selects the player to teleport the entities to

* #### `mobs.enchant(target, spell, level)`

  **Description:** Applies a certain enchantment to the specified targets
  
  **Parameters:**

  * `target`: `TargetSelector` – determines which players receive the enchantment
  * `spell`: `str` – the code name of the enchantment, e.g. “infinity”
  * `level`: `number` – the strength level of the enchantment, e.g. 1

* #### `mobs.execute_detect(detectBlock, detectPosition, command)`

  **Description:** Executes a command if a certain block type is detected at the specified position
  
  **Parameters:**

  * `detectBlock`: `number` – the block type to test for
  * `detectPosition`: `Position` – the position where the block is detected
  * `command`: `str` – the full command to run if the block is detected

* #### `mobs.execute(target, position, command)`

  **Description:** Executes a command as other targets
  
  **Parameters:**

  * `target`: `TargetSelector` – selects which entities execute the command
  * `position`: `Position` – the position where the command runs
  * `command`: `str` – the full command to execute

* #### `mobs.spawn_particle(particle, position)`

  **Description:** Spawns a particle effect at the given location
  
  **Parameters:**

  * `particle`: `number` – the particle effect to spawn
  * `position`: `Position` – the position to spawn the particle effect at

* #### `mobs.target(kind)`

  **Description:** Selects a set of players or mobs
  
  **Parameters:**

  * `kind`: `TargetSelectorKind` – the kind of targets to select

* #### `mobs.near(target, pos, radius)`

  **Description:** Selects targets near a given position
  
  **Parameters:**

  * `target`: `TargetSelector` – the type of mobs to select
  * `pos`: `Position` – the position near which to select targets
  * `radius`: `number` – how far away (in blocks) to search, e.g. 5

* #### `mobs.entities_by_type(type)`

  **Description:** Selects all mobs (animals or monsters) of a given type
  
  **Parameters:**

  * `type`: `number` – the type of mob to select

* #### `mobs.player_by_name(name)`

  **Description:** Selects the player with the given name
  
  **Parameters:**

  * `name`: `str` – the name of the player to select

* #### `mobs.players_in_game_mode(mode)`

  **Description:** Selects all players in the given game mode
  
  **Parameters:**

  * `mode`: `GameMode` – the game mode to filter players by

* #### `mobs.is_monster(mob)`

  **Description:** Returns true if the specified mob is a monster
  
  **Parameters:**

  * `mob`: `number` – the mob to check

* #### `mobs.mob_name_to_id(mobName)`

  **Description:** Converts a mob name to its ID
  
  **Parameters:**

  * `mobName`: `str` – the name of the mob

* #### `mobs.parse_selector(str)`

  **Description:** Parses a string into a `TargetSelector` object. This function does not validate argument types or names. Returns the parsed selector or `null` if the string is invalid.
  
  **Parameters:**

  * `str`: `str` – the selector string to parse

* #### `mobs.query_target(target)`

  **Description:** Queries information about a given target
  
  **Parameters:**

  * `target`: `TargetSelector` – the target to query

## Agent

* #### `agent.teleport_to_player()`

  **Description:** Teleports the agent to the player
  
  **Parameters:**
  *(none)*

* #### `agent.move(direction, blocks)`

  **Description:** Requests the agent to move in the specified direction
  
  **Parameters:**

  * `direction`: `number` – the direction to move the agent, such as `FORWARD`
  * `blocks`: `number` – how far the agent should move, in blocks, e.g. 1

* #### `agent.turn(direction)`

  **Description:** Turns the agent in the specified direction
  
  **Parameters:**

  * `direction`: `number` – the turn direction, e.g. `TurnDirection.Left`

* #### `agent.get_position()`

  **Description:** Returns the agent's position in world coordinates
  
  **Parameters:**
  *(none)*

* #### `agent.get_orientation()`

  **Description:** Returns the agent's orientation, in degrees
  
  **Parameters:**
  *(none)*

* #### `agent.teleport(pos, dir)`

  **Description:** Teleports the agent to the specified coordinates facing the specified orientation
  
  **Parameters:**

  * `pos`: `Position` – the destination position
  * `dir`: `number` – the compass direction (in degrees) that the agent will face

* #### `agent.set_assist(assist, on)`

  **Description:** Controls which assists are enabled for the agent
  
  **Parameters:**

  * `assist`: `AgentAssist` – the super power of the agent
  * `on`: `bool` – whether the assist is enabled (`True`) or disabled (`False`)

* #### `agent.place(direction)`

  **Description:** Places an item or block in the world from the agent's currently selected inventory slot
  
  **Parameters:**

  * `direction`: `number` – the direction in which to place the item, e.g. `BACK`

* #### `agent.interact(direction)`

  **Description:** Interacts with an item
  
  **Parameters:**

  * `direction`: `number` – the `SixDirection` in which to interact with the item

* #### `agent.destroy(direction)`

  **Description:** Commands the agent to destroy a block in the given direction
  
  **Parameters:**

  * `direction`: `number` – the direction in which the agent will destroy a block

* #### `agent.till(direction)`

  **Description:** Commands the agent to till soil in the given direction
  
  **Parameters:**

  * `direction`: `number` – the direction in which to till the soil

* #### `agent.attack(direction)`

  **Description:** Commands the agent to attack in the given direction
  
  **Parameters:**

  * `direction`: `number` – the direction in which to attack

* #### `agent.collect_all()`

  **Description:** Commands the agent to collect all nearby blocks and items
  
  **Parameters:**
  *(none)*

* #### `agent.collect(block)`

  **Description:** Commands the agent to collect a block or item of the specified type
  
  **Parameters:**

  * `block`: `number` – the type of block or item to collect

* #### `agent.inspect_block(direction)`

  **Description:** Inspects a block in the specified direction and returns the block ID
  
  **Parameters:**

  * `direction`: `number` – the direction in which to inspect, e.g. `FORWARD`

* #### `agent.detect(kind, direction)`

  **Description:** Detects if there is a block next to the agent in the specified direction
  
  **Parameters:**

  * `kind`: `AgentDetection` – what the agent should attempt to detect
  * `direction`: `number` – the direction in which to perform the detection

* #### `agent.set_slot(slot)`

  **Description:** Sets the agent's active inventory slot
  
  **Parameters:**

  * `slot`: `number` – the slot index between 1 and 27

* #### `agent.set_item(blockOrItem, count, slot)`

  **Description:** Puts the specified block or item in the agent's inventory
  
  **Parameters:**

  * `blockOrItem`: `number` – the block or item to place in a slot
  * `count`: `number` – the number of blocks or items to put in the slot
  * `slot`: `number` – the slot index (1–27), e.g. 1

* #### `agent.drop_all(direction)`

  **Description:** Commands the agent to drop its entire inventory in the given direction
  
  **Parameters:**

  * `direction`: `number` – the direction in which to drop items

* #### `agent.drop(direction, slot, quantity)`

  **Description:** Drops an item from the inventory
  
  **Parameters:**

  * `direction`: `number` – the direction in which to drop the item, e.g. `BACK`
  * `slot`: `number` – the slot from which the item will be dropped (1–27)
  * `quantity`: `number` – the number of items to drop

* #### `agent.transfer(quantity, sourceSlot, destinationSlot)`

  **Description:** Transfers items from one inventory slot to another
  
  **Parameters:**

  * `quantity`: `number` – the number of items to transfer, e.g. 1
  * `sourceSlot`: `number` – the source slot index (1–27)
  * `destinationSlot`: `number` – the destination slot index (1–27)

* #### `agent.get_item_count(slot)`

  **Description:** Gets the number of items in the specified slot
  
  **Parameters:**

  * `slot`: `number` – the inventory slot to count items in

* #### `agent.get_item_detail(slot)`

  **Description:** Gets the ID of the item in the specified inventory slot of the agent
  
  **Parameters:**

  * `slot`: `number` – the slot from which the item ID is returned

* #### `agent.get_item_space(slot)`

  **Description:** Gets the remaining space in the specified slot
  
  **Parameters:**

  * `slot`: `number` – the slot for which the remaining space is calculated

* #### `agent.turn_left()`

  **Description:** Turns the agent left by 90 degrees
  
  **Parameters:**
  *(none)*

* #### `agent.turn_right()`

  **Description:** Turns the agent right by 90 degrees
  
  **Parameters:**
  *(none)*



## Gameplay

* #### `gameplay.set_weather(weather)`

  **Description:** Changes the current weather
  
  **Parameters:**

  * `weather`: `number` – the desired weather

* #### `gameplay.weather_query()`

  **Description:** Gets the current weather in the game world
  
  **Parameters:**
  *(none)*

* #### `gameplay.toggle_downfall()`

  **Description:** Starts raining if it isn’t, or stops raining if it is
  
  **Parameters:**
  *(none)*

* #### `gameplay.time_set(time)`

  **Description:** Sets the current time of day to a preset time or a custom hour, in game ticks
  
  **Parameters:**

  * `time`: `number` – the desired time of day

* #### `gameplay.time_add(amount)`

  **Description:** Adds ticks to the current time of day
  
  **Parameters:**

  * `amount`: `number` – the number of ticks to add

* #### `gameplay.set_difficulty(difficulty)`

  **Description:** Changes the game difficulty
  
  **Parameters:**

  * `difficulty`: `GameDifficulty` – the new difficulty level for the game

* #### `gameplay.set_game_mode(mode, player)`

  **Description:** Changes the game mode for the selected players
  
  **Parameters:**

  * `mode`: `GameMode` – the new game mode
  * `player`: `TargetSelector` – a selector for the players whose game mode is changed

* #### `gameplay.title(target, title, subTitle)`

  **Description:** Shows a title and subtitle to the selected targets
  
  **Parameters:**

  * `target`: `TargetSelector` – determines which players receive the title
  * `title`: `str` – the large font title to display
  * `subTitle`: `str` – the secondary title to display (optional)

* #### `gameplay.time_query(query)`

  **Description:** Gets the current time of day, in game ticks
  
  **Parameters:**

  * `query`: `TimeQuery` – the type of time to query

* #### `gameplay.is_daylight_time(query)`

  **Description:** Checks whether the specified time is daylight time
  
  **Parameters:**

  * `query`: `DayTime` – the time of day to query

* #### `gameplay.xp(amount, target)`

  **Description:** Gives experience points to the selected players
  
  **Parameters:**

  * `amount`: `number` – the number of experience points to give
  * `target`: `TargetSelector` – selects the players who receive the experience

* #### `gameplay.set_game_rule(rule, enabled)`

  **Description:** Enables or disables a game rule
  
  **Parameters:**

  * `rule`: `GameRule` – the game rule to change
  * `enabled`: `bool` – set to `True` to enable or `False` to disable

* #### `gameplay.time(time)`

  **Description:** Represents a preset time of the day
  
  **Parameters:**

  * `time`: `DayTime` – the preset time of day

* #### `gameplay.dismiss_chat()`

  **Description:** Closes the chat window if it is open (EE only)
  
  **Parameters:**
  *(none)*


## Position

* #### `pos(x, y, z)`

  **Description:** Creates a new relative position (`~East/West`, `~up/down`, `~South/North`). A relative position is the distance in each direction from the player’s feet.
  
  **Parameters:**

  * `x`: `number` – the East (+x) or West (−x) distance from the player, in blocks
  * `y`: `number` – the up (+y) or down (−y) distance from the player, in blocks
  * `z`: `number` – the South (+z) or North (−z) distance from the player, in blocks

* #### `pos_camera(x, y, z)`

  **Description:** Creates a new camera (player) position: right/left, up/down, in front/behind. This position is relative to the direction the player is currently facing, starting from the player’s feet.
  
  **Parameters:**

  * `x`: `number` – the right (+x) or left (−x) distance from the player, in blocks
  * `y`: `number` – the up (+y) or down (−y) distance from the player, in blocks
  * `z`: `number` – the forward (+z) or backward (−z) distance from the player, in blocks

* #### `pos_local(x, y, z)`

  **Description:** Creates a new local position (`^right/^left`, `^up/^down`, `^forward/^backward`) based on the direction the player is looking. This position does not align with world axes.
  
  **Parameters:**

  * `x`: `number` – the right (+x) or left (−x) distance from the player’s view, in blocks
  * `y`: `number` – the up (+y) or down (−y) distance from the player’s view, in blocks
  * `z`: `number` – the forward (+z) or backward (−z) distance from the player’s view, in blocks

* #### `world(x, y, z)`

  **Description:** Creates a new world (absolute) position relative to the world origin `(0, 0, 0)`.
  
  **Parameters:**

  * `x`: `number` – the East (+x) or West (−x) distance from world coordinate 0, in blocks
  * `y`: `number` – the up (+y) or down (−y) distance from world coordinate 0, in blocks
  * `z`: `number` – the South (+z) or North (−z) distance from world coordinate 0, in blocks

* #### `positions.add(p1, p2)`

  **Description:** Adds two positions together and returns a new position. The result has the same type as the first position.
  
  **Parameters:**

  * `p1`: `Position` – the first position (determines the result type)
  * `p2`: `Position` – the second position to add

* #### `positions.equals(p1, p2)`

  **Description:** Compares two positions to check if they are equivalent in the world. Relative and local positions are compared using their actual world positions.
  
  **Parameters:**

  * `p1`: `Position` – the first position
  * `p2`: `Position` – the second position

* #### `randpos(p1, p2)`

  **Description:** Picks a random position inside a cube-shaped region defined by two corner positions.
  
  **Parameters:**

  * `p1`: `Position` – the first corner of the cube
  * `p2`: `Position` – the opposite corner of the cube

* #### `positions.ground_position(pos)`

  **Description:** Finds the ground position beneath the given position. Solid blocks and liquids are treated as ground.
  
  **Parameters:**

  * `pos`: `Position` – the position to start searching from

* #### `positions.to_compass_direction(deg)`

  **Description:** Converts an angle in degrees to the closest compass direction used in the game.
  
  **Parameters:**

  * `deg`: `number` – the angle in degrees to convert


## Math

* #### `randint(min, max)`

  **Description:** Returns a pseudorandom number between min and max included. If both numbers are integral, the result is integral.
  
  **Parameters:**

  * `min`: `number` – the lower inclusive bound
  * `max`: `number` – the upper inclusive bound

---

## Classes

### `TargetSelector`

* #### `TargetSelector.at_coordinate(p)`

  **Description:** Sets the base coordinates of the target selector.
  
  **Parameters:**

  * `p`: `Position` – the position to assign to the selector

* #### `TargetSelector.within_radius(radius)`

  **Description:** Sets the maximum distance from the selector’s base coordinates.
  
  **Parameters:**

  * `radius`: `number` – the maximum distance in blocks, e.g. 5

* #### `TargetSelector.add_rule(rule, value)`

  **Description:** Adds a rule (argument) to the target selector.
  
  **Parameters:**

  * `rule`: `str` – the rule name, e.g. `"type"`
  * `value`: `str` – the rule value, e.g. `"chicken"`

* #### `TargetSelector.outside_radius(radius)`

  **Description:** Sets the minimum distance from the selector’s base coordinates.
  
  **Parameters:**

  * `radius`: `number` – the minimum distance in blocks, e.g. 10

* #### `TargetSelector.to_string()`

  **Description:** Returns the game notation string for this target selector.
  
  **Parameters:**
  *(none)*

### `Position`

* #### `Position.get_value(direction)`

  **Description:** Gets the coordinate value of the position along one axis.
  
  **Parameters:**

  * `direction`: `Axis` – the axis to query (`x`, `y`, or `z`)

* #### `Position.to_world()`

  **Description:** Converts the position into a world (absolute) position.
  
  **Parameters:**
  *(none)*

* #### `Position.to_string()`

  **Description:** Returns a human-readable string representation of the position.
  
  **Parameters:**
  *(none)*

---

# Enums

### TravelMethod
The method of travel for player or mob
- `WALK` (1) - Walking normally (default if on ground)
- `SWIM_WATER` (2) - Swimming in water
- `FALL` (3) - In the air when not flying (Falling up or down)
- `CLIMB` (4) - Climbing a ladder
- `SWIM_LAVA` (5) - Swimming in lava
- `FLY` (6) - Flying
- `RIDING` (7) - Riding anything
- `SNEAK` (8) - Sneaking
- `SPRINT` (9) - Sprinting
- `BOUNCE` (10) - bounce
- `FROST_WALK` (11) - Frost walk over water
- `TELEPORT` (12) - Teleport
- `UNKNOWN` (-1) - Unknown travel method

### FillOperation
Fill options for exixting blocks. Control keeping, replacing, or destroying existing blocks
- `DESTROY` - Replaces all blocks (including air) in the fill region with the specified block, dropping the existing blocks (including those that are unchanged) and block contents as entities as if they had been mined with an unenchanted diamond shovel or pickaxe. (Blocks that can only be mined with shears, such as vines, will not drop; neither will liquids.)
- `HOLLOW` - Replaces only blocks on the outer edge of the fill region with the specified block. Inner blocks are changed to air, dropping their contents as entities but not themselves. If the fill region has no inner blocks (because it is smaller than three blocks in at least one dimension), acts like replace.
- `KEEP` - Replaces only air blocks in the fill region with the specified block.
- `OUTLINE` - Replaces only blocks on the outer edge of the fill region with the specified block. Inner blocks are not affected. If the fill region has no inner blocks (because it is smaller than three blocks in at least one dimension), acts like replace.
- `REPLACE` - Replaces all blocks (including air) in the fill region with the specified block, without dropping blocks or block contents as entities.

### CompassDirection
- `WEST`
- `EAST`
- `NORTH`
- `SOUTH`

### TurnDirection
- `LEFT`
- `RIGHT`

### SixDirection
- `FORWARD`
- `BACK`
- `LEFT`
- `RIGHT`
- `UP`
- `DOWN`

### LeverPosition
Positions for aligning a lever when on or off
- `BLOCK_BOTTOM_EAST_WHEN_OFF`
- `BLOCK_BOTTOM_POINTS_SOUTH_WHEN_OFF`
- `BLOCK_TOP_POINTS_EAST_WHEN_OFF`
- `BLOCK_TOP_POINTS_SOUTH_WHEN_OFF`
- `BLOCK_SIDE_FACING_EAST`
- `BLOCK_SIDE_FACING_WEST`
- `BLOCK_SIDE_FACING_NORTH`
- `BLOCK_SIDE_FACING_SOUTH`

### ComparatorMode
Comparator modes
- `COMPARE`
- `SUBTRACT`

### TestForBlocksMask
- `ALL` - Every block in the source and destination regions must match exactly.
- `MASKED` - Air blocks in the source region will match any block in the destination region.

### CloneMode
- `FORCE` - The cloned region is overwritten by the destination region if the two regions overlap.
- `MOVE` - the cloned region is replaced with air after the cloning.
- `NORMAL` - The cloned region is not changed; if the destination region overlaps it, then the clone operation does nothing.

### MonsterMob
Lists all mobs that are considered monsters.

### TargetSelectorKind
- `ALL_ENTITIES` - Select all players and mobs.
- `ALL_PLAYERS` - Select all players in the world.
- `LOCAL_PLAYER` - Select the current player (you).
- `MY_AGENT` - Select the agent.
- `NEAREST_PLAYER` - Select the player nearest to the world origin.
- `RANDOM_PLAYER` - Select a random player in the world.

### GameMode
- `SURVIVAL` - This is the default Minecraft playing mode. Players have to gather the materials they want to craft or place. The player’s health, hunger, experience and oxygen are enabled. Tools and equipment durability is enabled. In this mode, the player can die and will return to the spawn point if they do.
- `CREATIVE` - Players can get an unlimited amount of blocks or items in the game. Players can fly around in the world and destroy blocks instantly. This mode is meant for players that want to spend time building things.
- `ADVENTURE` - Kind of the same as survival mode, but it has more restrictions on placing certain blocks and destroying blocks in the game world. This mode is meant for playing in worlds where the players must solve puzzles or complete challenges.

### AgentAssist
- `PLACE_ON_MOVE` - the agent will place a block from its active inventory slot every time it moves.
- `PLACE_FROM_ANY_SLOT` - if there are no blocks or items in the agent’s active inventory slot, the agent will try to use other inventory slots. 
- `DESTROY_OBSTACLES` - if the agent can’t move because of an obstacle, it will destroy the obstacle before moving.
- `DETROY_OBSTACLES` - seems to be a typo left in the code, functions the same was as `DESTROY_OBSTACLES`.

### AgentDetection
- `BLOCK` - detect any block that can be destroyed.
- `REDSTONE` - detect redstone only.

### Weather
- `CLEAR` - sunny, no rain or storms
- `RAIN` - rainy, no sun
- `THUNDER` - thunderstorm, lot’s of rain

### DayTime
- `DAY` (0) - Equals 1,000 ticks (7:00 AM)
- `MIDDAY` (6000) - Equals 6,000 ticks (12:00 PM)
- `DUSK` (12000) - Equals 12,000 ticks (6:00 PM)
- `NIGHT` (14000) - Equals 13,000 ticks (7:00 PM)
- `MIDNIGHT` (18000) - Equals to 18,000 ticks (12:00 AM)
- `DAWN` (23000) - Equals 0 ticks (6:00 AM)

### GameDifficulty
- `PEACEFUL` - monsters cannot spawn and you get more hearts quickly.
- `EASY` - easy gameplay level.
- `NORMAL` - normal gameplay level.
- `HARD` - the really difficult gameplay level.

### TimeQuery
- `DAY` - the number of game days since the creation of the world
- `DAY_TIME` - the current time of day in the game.
- `GAME_TIME` - the number of game ticks since the creation of the world.
- `REAL_LIFE` - the real-life time of day, expressed in Minecraft game ticks.

### GameRule

*For some reason some of these are differ between the docs and the code editor autocomplete suggestions. Some of these seem like different names for the same thing, but I haven't tested to see if it's so.*
- *(D) - present only in the docs.*
- *(E) - present only in the code editor.*
- *(DE) - present in both the docs and the editor.*

**Rules:**
    
- `PV_P` *(DE)* - players can attack each other 
- `DROWNING_DAMAGE` *(DE)* - staying for too long under water will damage the player 
- `FALL_DAMAGE` *(DE)* - falling from really high will damage the player
- `FIRE_DAMAGE` *(DE)* - fire will damage the player 
- `DAYLIGHT_CYCLE` *(DE)* - time will advance in the game 
- `MOB_LOOT` *(DE)* - mobs will drop loot upon dying 
- `MOB_SPAWNING` *(DE)* - mobs are able to spawn 
- `MOB_GRIEFING` *(DE)* - mobs can affect the game world (for example, endermen picking up blocks, or creepers exploding the environment) 
- `WEATHER_CYCLE` *(DE)* - weather will change naturally 
- `BLOCK_DROPS` *(D)* - blocks that are successfully mined will drop as an item and be collectible by players 
- `KEEP_INVENTORY` *(DE)* - players will not lose their inventory upon dying
- `COMMAND_BLOCK_OUTPUT` *(E)*
- `DO_FIRE_TICK` *(E)*
- `NATURAL_REGENERATION` *(E)*
- `TILE_DROPS` *(E)*
- `ENTITY_DROPS` *(E)*
- `SHOW_COORDINATES` *(E)*
- `TNT_EXPLODES` *(E)*

### Axis
- `X`
- `Y`
- `Z`

---

# Constants

```
FORWARD = SixDirection.Forward
BACK = SixDirection.Back
LEFT = SixDirection.Left
RIGHT = SixDirection.Right
UP = SixDirection.Up
DOWN = SixDirection.Down


NEAREST_PLAYER = TargetSelectorKind.NearestPlayer
LOCAL_PLAYER = TargetSelectorKind.LocalPlayer
RANDOM_PLAYER = TargetSelectorKind.RandomPlayer
ALL_PLAYERS = TargetSelectorKind.AllPlayers
ALL_ENTITIES = TargetSelectorKind.AllEntities
MY_AGENT = TargetSelectorKind.MyAgent


GRASS = Block.Grass
AIR = Block.Air
STONE = Block.Stone
GRANITE = Block.Granite
POLISHED_GRANITE = Block.PolishedGranite
DIORITE = Block.Diorite
POLISHED_DIORITE = Block.PolishedDiorite
ANDESITE = Block.Andesite
POLISHED_ANDESITE = Block.PolishedAndesite
DIRT = Block.Dirt
COARSE_DIRT = Block.CoarseDirt
COBBLESTONE = Block.Cobblestone
PLANKS_OAK = Block.PlanksOak
PLANKS_SPRUCE = Block.PlanksSpruce
PLANKS_BIRCH = Block.PlanksBirch
PLANKS_JUNGLE = Block.PlanksJungle
PLANKS_ACACIA = Block.PlanksAcacia
PLANKS_DARK_OAK = Block.PlanksDarkOak
OAK_SAPLING = Block.OakSapling
SPRUCE_SAPLING = Block.SpruceSapling
BIRCH_SAPLING = Block.BirchSapling
JUNGLE_SAPLING = Block.JungleSapling
ACACIA_SAPLING = Block.AcaciaSapling
DARK_OAK_SAPLING = Block.DarkOakSapling
BEDROCK = Block.Bedrock
WATER = Block.Water
LAVA = Block.Lava
SAND = Block.Sand
RED_SAND = Block.RedSand
GRAVEL = Block.Gravel
GOLD_ORE = Block.GoldOre
IRON_ORE = Block.IronOre
COAL_ORE = Block.CoalOre
LOG_OAK = Block.LogOak
LOG_SPRUCE = Block.LogSpruce
LOG_BIRCH = Block.LogBirch
LOG_JUNGLE = Block.LogJungle
LEAVES_OAK = Block.LeavesOak
LEAVES_SPRUCE = Block.LeavesSpruce
LEAVES_BIRCH = Block.LeavesBirch
LEAVES_JUNGLE = Block.LeavesJungle
SPONGE = Block.Sponge
WET_SPONGE = Block.WetSponge
GLASS = Block.Glass
LAPIS_ORE = Block.LapisOre
LAPIS_LAZULI_BLOCK = Block.LapisLazuliBlock
DISPENSER = Block.Dispenser
SANDSTONE = Block.Sandstone
CHISELED_SANDSTONE = Block.ChiseledSandstone
SMOOTH_SANDSTONE = Block.SmoothSandstone
NOTE_BLOCK = Block.NoteBlock
BED = Block.Bed
POWERED_RAIL = Block.PoweredRail
DETECTOR_RAIL = Block.DetectorRail
STICKY_PISTON = Block.StickyPiston
COBWEB = Block.Cobweb
TALLGRASS = Block.Tallgrass
FERN = Block.Fern
DEAD_BUSH = Block.DeadBush
PISTON = Block.Piston
WOOL = Block.Wool
ORANGE_WOOL = Block.OrangeWool
MAGENTA_WOOL = Block.MagentaWool
LIGHT_BLUE_WOOL = Block.LightBlueWool
YELLOW_WOOL = Block.YellowWool
LIME_WOOL = Block.LimeWool
PINK_WOOL = Block.PinkWool
GRAY_WOOL = Block.GrayWool
LIGHT_GRAY_WOOL = Block.LightGrayWool
CYAN_WOOL = Block.CyanWool
PURPLE_WOOL = Block.PurpleWool
BLUE_WOOL = Block.BlueWool
BROWN_WOOL = Block.BrownWool
GREEN_WOOL = Block.GreenWool
RED_WOOL = Block.RedWool
BLACK_WOOL = Block.BlackWool
YELLOW_FLOWER = Block.YellowFlower
POPPY = Block.Poppy
BLUE_ORCHID = Block.BlueOrchid
ALLIUM = Block.Allium
AZURE_BLUET = Block.AzureBluet
RED_TULIP = Block.RedTulip
ORANGE_TULIP = Block.OrangeTulip
WHITE_TULIP = Block.WhiteTulip
PINK_TULIP = Block.PinkTulip
OXEYE_DAISY = Block.OxeyeDaisy
BAMBOO = Block.Bamboo
CORNFLOWER = Block.Cornflower
LILY_OF_THE_VALLEY = Block.LilyOfTheValley
BROWN_MUSHROOM = Block.BrownMushroom
RED_MUSHROOM = Block.RedMushroom
GOLD_BLOCK = Block.GoldBlock
IRON_BLOCK = Block.IronBlock
DOUBLE_STONE_SLAB = Block.DoubleStoneSlab
SMOOTH_STONE_SLAB = Block.SmoothStoneSlab
MOSSY_STONE_BRICK_SLAB = Block.MossyStoneBrickSlab
SANDSTONE_SLAB = Block.SandstoneSlab
COBBLESTONE_SLAB = Block.CobblestoneSlab
BRICKS_SLAB = Block.BricksSlab
STONE_BRICKS_SLAB = Block.StoneBricksSlab
QUARTZ_SLAB = Block.QuartzSlab
NETHER_BRICK_SLAB = Block.NetherBrickSlab
BRICKS = Block.Bricks
TNT = Block.TNT
BOOKSHELF = Block.Bookshelf
MOSS_STONE = Block.MossStone
OBSIDIAN = Block.Obsidian
TORCH = Block.Torch
FIRE = Block.Fire
MONSTER_SPAWNER = Block.MonsterSpawner
OAK_WOOD_STAIRS = Block.OakWoodStairs
CHEST = Block.Chest
REDSTONE_WIRE = Block.RedstoneWire
DIAMOND_ORE = Block.DiamondOre
DIAMOND_BLOCK = Block.DiamondBlock
CRAFTING_TABLE = Block.CraftingTable
CROPS = Block.Crops
FARMLAND = Block.Farmland
FURNACE = Block.Furnace
LADDER = Block.Ladder
RAIL = Block.Rail
COBBLESTONE_STAIRS = Block.CobblestoneStairs
LEVER = Block.Lever
STONE_PRESSURE_PLATE = Block.StonePressurePlate
WOODEN_PRESSURE_PLATE = Block.WoodenPressurePlate
REDSTONE_ORE = Block.RedstoneOre
REDSTONE_TORCH = Block.RedstoneTorch
STONE_BUTTON = Block.StoneButton
TOP_SNOW = Block.TopSnow
ICE = Block.Ice
SNOW = Block.Snow
CACTUS = Block.Cactus
CLAY = Block.Clay
SUGAR_CANE = Block.SugarCane
JUKEBOX = Block.Jukebox
OAK_FENCE = Block.OakFence
SPRUCE_FENCE = Block.SpruceFence
BIRCH_FENCE = Block.BirchFence
JUNGLE_FENCE = Block.JungleFence
ACACIA_FENCE = Block.AcaciaFence
DARK_OAK_FENCE = Block.DarkOakFence
PUMPKIN = Block.Pumpkin
NETHERRACK = Block.Netherrack
SOUL_SAND = Block.SoulSand
GLOWSTONE = Block.Glowstone
JACK_O_LANTERN = Block.JackOLantern
CAKE = Block.Cake
UNPOWERED_REPEATER = Block.UnpoweredRepeater
WOODEN_TRAPDOOR = Block.WoodenTrapdoor
STONE_MONSTER_EGG = Block.StoneMonsterEgg
COBBLESTONE_MONSTER_EGG = Block.CobblestoneMonsterEgg
STONE_BRICK_MONSTER_EGG = Block.StoneBrickMonsterEgg
MOSSY_STONE_BRICK_MONSTER_EGG = Block.MossyStoneBrickMonsterEgg
CRACKED_STONE_BRICK_MONSTER_EGG = Block.CrackedStoneBrickMonsterEgg
CHISELED_STONE_BRICK_MONSTER_EGG = Block.ChiseledStoneBrickMonsterEgg
STONE_BRICKS = Block.StoneBricks
MOSSY_STONE_BRICKS = Block.MossyStoneBricks
CRACKED_STONE_BRICKS = Block.CrackedStoneBricks
CHISELED_STONE_BRICKS = Block.ChiseledStoneBricks
MUSHROOM0 = Block.Mushroom0
MUSHROOM14 = Block.Mushroom14
MUSHROOM15 = Block.Mushroom15
RED_MUSHROOM_BLOCK = Block.RedMushroomBlock
IRON_BARS = Block.IronBars
GLASS_PANE = Block.GlassPane
MELON_BLOCK = Block.MelonBlock
PUMPKIN_STEM = Block.PumpkinStem
MELON_STEM = Block.MelonStem
VINES = Block.Vines
OAK_FENCE_GATE = Block.OakFenceGate
BRICK_STAIRS = Block.BrickStairs
STONE_BRICK_STAIRS = Block.StoneBrickStairs
MYCELIUM = Block.Mycelium
LILY_PAD = Block.LilyPad
NETHER_BRICK = Block.NetherBrick
NETHER_BRICK_FENCE = Block.NetherBrickFence
NETHER_BRICK_STAIRS = Block.NetherBrickStairs
NETHER_WART = Block.NetherWart
ENCHANTMENT_TABLE = Block.EnchantmentTable
BREWING_STAND = Block.BrewingStand
CAULDRON = Block.Cauldron
END_PORTAL = Block.EndPortal
ENDSTONE = Block.Endstone
DRAGON_EGG = Block.DragonEgg
REDSTONE_LAMP = Block.RedstoneLamp
DROPPER = Block.Dropper
ACTIVATOR_RAIL = Block.ActivatorRail
COCOA = Block.Cocoa
SANDSTONE_STAIRS = Block.SandstoneStairs
EMERALD_ORE = Block.EmeraldOre
ENDER_CHEST = Block.EnderChest
TRIPWIRE_HOOK = Block.TripwireHook
TRIPWIRE = Block.Tripwire
EMERALD_BLOCK = Block.EmeraldBlock
SPRUCE_WOOD_STAIRS = Block.SpruceWoodStairs
BIRCH_WOOD_STAIRS = Block.BirchWoodStairs
JUNGLE_WOOD_STAIRS = Block.JungleWoodStairs
BEACON = Block.Beacon
COBBLESTONE_WALL = Block.CobblestoneWall
MOSSY_COBBLESTONE_WALL = Block.MossyCobblestoneWall
FLOWER_POT = Block.FlowerPot
CARROTS = Block.Carrots
POTATOES = Block.Potatoes
WOODEN_BUTTON = Block.WoodenButton
SKELETON_SKULL = Block.SkeletonSkull
ANVIL = Block.Anvil
SLIGHTLY_DAMAGED_ANVIL = Block.SlightlyDamagedAnvil
VERY_DAMAGED_ANVIL = Block.VeryDamagedAnvil
TRAPPED_CHEST = Block.TrappedChest
WEIGHTED_PRESSURE_PLATE_LIGHT = Block.WeightedPressurePlateLight
WEIGHTED_PRESSURE_PLATE_HEAVY = Block.WeightedPressurePlateHeavy
UNPOWERED_COMPARATOR = Block.UnpoweredComparator
DAYLIGHT_SENSOR = Block.DaylightSensor
REDSTONE_BLOCK = Block.RedstoneBlock
QUARTZ_ORE = Block.QuartzOre
HOPPER = Block.Hopper
BLOCK_OF_QUARTZ = Block.BlockOfQuartz
CHISELED_QUARTZ_BLOCK = Block.ChiseledQuartzBlock
PILLAR_QUARTZ_BLOCK = Block.PillarQuartzBlock
QUARTZ_STAIRS = Block.QuartzStairs
DOUBLE_WOODEN_SLAB = Block.DoubleWoodenSlab
OAK_WOOD_SLAB = Block.OakWoodSlab
SPRUCE_WOOD_SLAB = Block.SpruceWoodSlab
BIRCH_WOOD_SLAB = Block.BirchWoodSlab
JUNGLE_WOOD_SLAB = Block.JungleWoodSlab
ACACIA_WOOD_SLAB = Block.AcaciaWoodSlab
DARK_OAK_WOOD_SLAB = Block.DarkOakWoodSlab
WHITE_TERRACOTTA = Block.WhiteTerracotta
ORANGE_TERRACOTTA = Block.OrangeTerracotta
MAGENTA_TERRACOTTA = Block.MagentaTerracotta
LIGHT_BLUE_TERRACOTTA = Block.LightBlueTerracotta
YELLOW_TERRACOTTA = Block.YellowTerracotta
LIME_TERRACOTTA = Block.LimeTerracotta
PINK_TERRACOTTA = Block.PinkTerracotta
GRAY_TERRACOTTA = Block.GrayTerracotta
LIGHT_GRAY_TERRACOTTA = Block.LightGrayTerracotta
CYAN_TERRACOTTA = Block.CyanTerracotta
PURPLE_TERRACOTTA = Block.PurpleTerracotta
BLUE_TERRACOTTA = Block.BlueTerracotta
BROWN_TERRACOTTA = Block.BrownTerracotta
GREEN_TERRACOTTA = Block.GreenTerracotta
RED_TERRACOTTA = Block.RedTerracotta
BLACK_TERRACOTTA = Block.BlackTerracotta
WHITE_STAINED_GLASS_PANE = Block.WhiteStainedGlassPane
ORANGE_STAINED_GLASS_PANE = Block.OrangeStainedGlassPane
MAGENTA_STAINED_GLASS_PANE = Block.MagentaStainedGlassPane
LIGHT_BLUE_STAINED_GLASS_PANE = Block.LightBlueStainedGlassPane
YELLOW_STAINED_GLASS_PANE = Block.YellowStainedGlassPane
LIME_STAINED_GLASS_PANE = Block.LimeStainedGlassPane
PINK_STAINED_GLASS_PANE = Block.PinkStainedGlassPane
GRAY_STAINED_GLASS_PANE = Block.GrayStainedGlassPane
LIGHT_GRAY_STAINED_GLASS_PANE = Block.LightGrayStainedGlassPane
CYAN_STAINED_GLASS_PANE = Block.CyanStainedGlassPane
PURPLE_STAINED_GLASS_PANE = Block.PurpleStainedGlassPane
BLUE_STAINED_GLASS_PANE = Block.BlueStainedGlassPane
BROWN_STAINED_GLASS_PANE = Block.BrownStainedGlassPane
GREEN_STAINED_GLASS_PANE = Block.GreenStainedGlassPane
RED_STAINED_GLASS_PANE = Block.RedStainedGlassPane
BLACK_STAINED_GLASS_PANE = Block.BlackStainedGlassPane
ACACIA_LEAVES = Block.AcaciaLeaves
DARK_OAK_LEAVES = Block.DarkOakLeaves
LOG_ACACIA = Block.LogAcacia
LOG_DARK_OAK = Block.LogDarkOak
ACACIA_WOOD_STAIRS = Block.AcaciaWoodStairs
DARK_OAK_WOOD_STAIRS = Block.DarkOakWoodStairs
SLIME_BLOCK = Block.SlimeBlock
IRON_TRAPDOOR = Block.IronTrapdoor
PRISMARINE = Block.Prismarine
DARK_PRISMARINE = Block.DarkPrismarine
PRISMARINE_BRICKS = Block.PrismarineBricks
SEA_LANTERN = Block.SeaLantern
HAY_BLOCK = Block.HayBlock
WHITE_CARPET = Block.WhiteCarpet
ORANGE_CARPET = Block.OrangeCarpet
MAGENTA_CARPET = Block.MagentaCarpet
LIGHT_BLUE_CARPET = Block.LightBlueCarpet
YELLOW_CARPET = Block.YellowCarpet
LIME_CARPET = Block.LimeCarpet
PINK_CARPET = Block.PinkCarpet
GRAY_CARPET = Block.GrayCarpet
LIGHT_GRAY_CARPET = Block.LightGrayCarpet
CYAN_CARPET = Block.CyanCarpet
PURPLE_CARPET = Block.PurpleCarpet
BLUE_CARPET = Block.BlueCarpet
BROWN_CARPET = Block.BrownCarpet
GREEN_CARPET = Block.GreenCarpet
RED_CARPET = Block.RedCarpet
BLACK_CARPET = Block.BlackCarpet
HARDENED_CLAY = Block.HardenedClay
COAL_BLOCK = Block.CoalBlock
PACKED_ICE = Block.PackedIce
SUNFLOWER = Block.Sunflower
LILAC = Block.Lilac
DOUBLE_TALLGRASS = Block.DoubleTallgrass
LARGE_FERN = Block.LargeFern
ROSE_BUSH = Block.RoseBush
PEONY = Block.Peony
RED_SANDSTONE = Block.RedSandstone
CHISELED_RED_SANDSTONE = Block.ChiseledRedSandstone
SMOOTH_RED_SANDSTONE = Block.SmoothRedSandstone
RED_SANDSTONE_STAIRS = Block.RedSandstoneStairs
DOUBLE_RED_SANDSTONE_SLAB = Block.DoubleRedSandstoneSlab
RED_SANDSTONE_SLAB = Block.RedSandstoneSlab
PURPUR_SLAB = Block.PurpurSlab
PRISMARINE_SLAB = Block.PrismarineSlab
DARK_PRISMARINE_SLAB = Block.DarkPrismarineSlab
PRISMARINE_BRICK_SLAB = Block.PrismarineBrickSlab
SPRUCE_FENCE_GATE = Block.SpruceFenceGate
BIRCH_FENCE_GATE = Block.BirchFenceGate
JUNGLE_FENCE_GATE = Block.JungleFenceGate
DARK_OAK_FENCE_GATE = Block.DarkOakFenceGate
ACACIA_FENCE_GATE = Block.AcaciaFenceGate
GRASS_PATH = Block.GrassPath
FRAME = Block.Frame
CHORUS_FLOWER = Block.ChorusFlower
PURPUR_BLOCK = Block.PurpurBlock
PURPUR_PILLAR = Block.PurpurPillar
PURPUR_STAIRS = Block.PurpurStairs
SHULKER_BOX = Block.ShulkerBox
END_STONE_BRICKS = Block.EndStoneBricks
END_ROD = Block.EndRod
MAGMA_BLOCK = Block.MagmaBlock
NETHER_WART_BLOCK = Block.NetherWartBlock
RED_NETHER_BRICK = Block.RedNetherBrick
BONE_BLOCK = Block.BoneBlock
WHITE_SHULKER_BOX = Block.WhiteShulkerBox
ORANGE_SHULKER_BOX = Block.OrangeShulkerBox
MAGENTA_SHULKER_BOX = Block.MagentaShulkerBox
LIGHT_BLUE_SHULKER_BOX = Block.LightBlueShulkerBox
YELLOW_SHULKER_BOX = Block.YellowShulkerBox
LIME_SHULKER_BOX = Block.LimeShulkerBox
PINK_SHULKER_BOX = Block.PinkShulkerBox
GRAY_SHULKER_BOX = Block.GrayShulkerBox
SILVER_SHULKER_BOX = Block.SilverShulkerBox
CYAN_SHULKER_BOX = Block.CyanShulkerBox
PURPLE_SHULKER_BOX = Block.PurpleShulkerBox
BLUE_SHULKER_BOX = Block.BlueShulkerBox
BROWN_SHULKER_BOX = Block.BrownShulkerBox
GREEN_SHULKER_BOX = Block.GreenShulkerBox
RED_SHULKER_BOX = Block.RedShulkerBox
BLACK_SHULKER_BOX = Block.BlackShulkerBox
PURPLE_GLAZED_TERRACOTTA = Block.PurpleGlazedTerracotta
WHITE_GLAZED_TERRACOTTA = Block.WhiteGlazedTerracotta
ORANGE_GLAZED_TERRACOTTA = Block.OrangeGlazedTerracotta
MAGENTA_GLAZED_TERRACOTTA = Block.MagentaGlazedTerracotta
LIGHT_BLUE_GLAZED_TERRACOTTA = Block.LightBlueGlazedTerracotta
YELLOW_GLAZED_TERRACOTTA = Block.YellowGlazedTerracotta
LIME_GLAZED_TERRACOTTA = Block.LimeGlazedTerracotta
PINK_GLAZED_TERRACOTTA = Block.PinkGlazedTerracotta
GRAY_GLAZED_TERRACOTTA = Block.GrayGlazedTerracotta
LIGHT_GRAY_GLAZED_TERRACOTTA = Block.LightGrayGlazedTerracotta
CYAN_GLAZED_TERRACOTTA = Block.CyanGlazedTerracotta
BLUE_GLAZED_TERRACOTTA = Block.BlueGlazedTerracotta
BROWN_GLAZED_TERRACOTTA = Block.BrownGlazedTerracotta
GREEN_GLAZED_TERRACOTTA = Block.GreenGlazedTerracotta
RED_GLAZED_TERRACOTTA = Block.RedGlazedTerracotta
BLACK_GLAZED_TERRACOTTA = Block.BlackGlazedTerracotta
WHITE_CONCRETE = Block.WhiteConcrete
ORANGE_CONCRETE = Block.OrangeConcrete
MAGENTA_CONCRETE = Block.MagentaConcrete
LIGHT_BLUE_CONCRETE = Block.LightBlueConcrete
YELLOW_CONCRETE = Block.YellowConcrete
LIME_CONCRETE = Block.LimeConcrete
PINK_CONCRETE = Block.PinkConcrete
GRAY_CONCRETE = Block.GrayConcrete
LIGHT_GRAY_CONCRETE = Block.LightGrayConcrete
CYAN_CONCRETE = Block.CyanConcrete
PURPLE_CONCRETE = Block.PurpleConcrete
BLUE_CONCRETE = Block.BlueConcrete
BROWN_CONCRETE = Block.BrownConcrete
GREEN_CONCRETE = Block.GreenConcrete
RED_CONCRETE = Block.RedConcrete
BLACK_CONCRETE = Block.BlackConcrete
WHITE_CONCRETE_POWDER = Block.WhiteConcretePowder
ORANGE_CONCRETE_POWDER = Block.OrangeConcretePowder
MAGENTA_CONCRETE_POWDER = Block.MagentaConcretePowder
LIGHT_BLUE_CONCRETE_POWDER = Block.LightBlueConcretePowder
YELLOW_CONCRETE_POWDER = Block.YellowConcretePowder
LIME_CONCRETE_POWDER = Block.LimeConcretePowder
PINK_CONCRETE_POWDER = Block.PinkConcretePowder
GRAY_CONCRETE_POWDER = Block.GrayConcretePowder
LIGHT_GRAY_CONCRETE_POWDER = Block.LightGrayConcretePowder
CYAN_CONCRETE_POWDER = Block.CyanConcretePowder
PURPLE_CONCRETE_POWDER = Block.PurpleConcretePowder
BLUE_CONCRETE_POWDER = Block.BlueConcretePowder
BROWN_CONCRETE_POWDER = Block.BrownConcretePowder
GREEN_CONCRETE_POWDER = Block.GreenConcretePowder
RED_CONCRETE_POWDER = Block.RedConcretePowder
BLACK_CONCRETE_POWDER = Block.BlackConcretePowder
CHORUS_PLANT = Block.ChorusPlant
WHITE_STAINED_GLASS = Block.WhiteStainedGlass
ORANGE_STAINED_GLASS = Block.OrangeStainedGlass
MAGENTA_STAINED_GLASS = Block.MagentaStainedGlass
LIGHT_BLUE_STAINED_GLASS = Block.LightBlueStainedGlass
YELLOW_STAINED_GLASS = Block.YellowStainedGlass
LIME_STAINED_GLASS = Block.LimeStainedGlass
PINK_STAINED_GLASS = Block.PinkStainedGlass
GRAY_STAINED_GLASS = Block.GrayStainedGlass
LIGHT_GRAY_STAINED_GLASS = Block.LightGrayStainedGlass
CYAN_STAINED_GLASS = Block.CyanStainedGlass
PURPLE_STAINED_GLASS = Block.PurpleStainedGlass
BLUE_STAINED_GLASS = Block.BlueStainedGlass
BROWN_STAINED_GLASS = Block.BrownStainedGlass
GREEN_STAINED_GLASS = Block.GreenStainedGlass
RED_STAINED_GLASS = Block.RedStainedGlass
BLACK_STAINED_GLASS = Block.BlackStainedGlass
PODZOL = Block.Podzol
BEETROOT = Block.Beetroot
STONECUTTER = Block.Stonecutter
OBSERVER = Block.Observer
STRUCTURE_BLOCK = Block.StructureBlock
PRISMARINE_STAIRS = Block.PrismarineStairs
DARK_PRISMARINE_STAIRS = Block.DarkPrismarineStairs
PRISMARINE_BRICK_STAIRS = Block.PrismarineBrickStairs
STRIPPED_SPRUCE_WOOD = Block.StrippedSpruceWood
STRIPPED_BIRCH_WOOD = Block.StrippedBirchWood
STRIPPED_JUNGLE_WOOD = Block.StrippedJungleWood
STRIPPED_ACACIA_WOOD = Block.StrippedAcaciaWood
STRIPPED_DARK_OAK_WOOD = Block.StrippedDarkOakWood
STRIPPED_OAK_WOOD = Block.StrippedOakWood
SCAFFOLDING = Block.Scaffolding
BLUE_ICE = Block.BlueIce
SEAGRASS = Block.Seagrass
TUBE_CORAL = Block.TubeCoral
BRAIN_CORAL = Block.BrainCoral
BUBBLE_CORAL = Block.BubbleCoral
FIRE_CORAL = Block.FireCoral
HORN_CORAL = Block.HornCoral
TUBE_CORAL_BLOCK = Block.TubeCoralBlock
BRAIN_CORAL_BLOCK = Block.BrainCoralBlock
BUBBLE_CORAL_BLOCK = Block.BubbleCoralBlock
FIRE_CORAL_BLOCK = Block.FireCoralBlock
HORN_CORAL_BLOCK = Block.HornCoralBlock
DEAD_TUBE_CORAL_BLOCK = Block.DeadTubeCoralBlock
DEAD_BRAIN_CORAL_BLOCK = Block.DeadBrainCoralBlock
DEAD_BUBBLE_CORAL_BLOCK = Block.DeadBubbleCoralBlock
DEAD_FIRE_CORAL_BLOCK = Block.DeadFireCoralBlock
DEAD_HORN_CORAL_BLOCK = Block.DeadHornCoralBlock
TUBE_CORAL_FAN = Block.TubeCoralFan
BRAIN_CORAL_FAN = Block.BrainCoralFan
BUBBLE_CORAL_FAN = Block.BubbleCoralFan
FIRE_CORAL_FAN = Block.FireCoralFan
HORN_CORAL_FAN = Block.HornCoralFan
DEAD_TUBE_CORAL_FAN = Block.DeadTubeCoralFan
DEAD_BRAIN_CORAL_FAN = Block.DeadBrainCoralFan
DEAD_BUBBLE_CORAL_FAN = Block.DeadBubbleCoralFan
DEAD_FIRE_CORAL_FAN = Block.DeadFireCoralFan
DEAD_HORN_CORAL_FAN = Block.DeadHornCoralFan
KELP = Block.Kelp
DRIED_KELP_BLOCK = Block.DriedKelpBlock
ACACIA_BUTTON = Block.AcaciaButton
BIRCH_BUTTON = Block.BirchButton
DARK_OAK_BUTTON = Block.DarkOakButton
JUNGLE_BUTTON = Block.JungleButton
SPRUCE_BUTTON = Block.SpruceButton
ACACIA_TRAPDOOR = Block.AcaciaTrapdoor
BIRCH_TRAPDOOR = Block.BirchTrapdoor
DARK_OAK_TRAPDOOR = Block.DarkOakTrapdoor
JUNGLE_TRAPDOOR = Block.JungleTrapdoor
SPRUCE_TRAPDOOR = Block.SpruceTrapdoor
ACACIA_PRESSURE_PLATE = Block.AcaciaPressurePlate
BIRCH_PRESSURE_PLATE = Block.BirchPressurePlate
DARK_OAK_PRESSURE_PLATE = Block.DarkOakPressurePlate
JUNGLE_PRESSURE_PLATE = Block.JunglePressurePlate
SPRUCE_PRESSURE_PLATE = Block.SprucePressurePlate
CARVED_PUMPKIN = Block.CarvedPumpkin
SEA_PICKLE = Block.SeaPickle
CARTOGRAPHY_TABLE = Block.CartographyTable
FLETCHING_TABLE = Block.FletchingTable
BLAST_FURNACE = Block.BlastFurnace
STONECUTTER_BLOCK = Block.StonecutterBlock
SMOKER = Block.Smoker
SMITHING_TABLE = Block.SmithingTable
BARREL = Block.Barrel
LOOM = Block.Loom
BELL = Block.Bell
CAMPFIRE = Block.Campfire
COMPOSTER = Block.Composter
BEE_NEST = Block.BeeNest
BEEHIVE = Block.Beehive
HONEY_BLOCK = Block.HoneyBlock
HONEYCOMB_BLOCK = Block.HoneycombBlock
CRIMSON_PLANKS = Block.CrimsonPlanks
WARPED_PLANKS = Block.WarpedPlanks
BLACKSTONE_WALL = Block.BlackstoneWall
CRIMSON_FENCE = Block.CrimsonFence
WARPED_FENCE = Block.WarpedFence
CRIMSON_FENCE_GATE = Block.CrimsonFenceGate
WARPED_FENCE_GATE = Block.WarpedFenceGate
CHAIN = Block.Chain
SMALL_DRIPLEAF = Block.SmallDripleaf
CRIMSON_STAIRS = Block.CrimsonStairs
WARPED_STAIRS = Block.WarpedStairs
BLACKSTONE_STAIRS = Block.BlackstoneStairs
GLOW_LICHEN = Block.GlowLichen
CRIMSON_BUTTON = Block.CrimsonButton
ANCIENT_DEBRIS = Block.AncientDebris
RESPAWN_ANCHOR = Block.RespawnAnchor
TINTED_GLASS = Block.TintedGlass
SOUL_SOIL = Block.SoulSoil
CRIMSON_SLAB = Block.CrimsonSlab
WARPED_SLAB = Block.WarpedSlab
BLACKSTONE_SLAB = Block.BlackstoneSlab
CHISELED_NETHER_BRICKS = Block.ChiseledNetherBricks
CRACKED_NETHER_BRICKS = Block.CrackedNetherBricks
BLOCK_OF_COPPER = Block.BlockOfCopper
EXPOSED_COPPER = Block.ExposedCopper
WEATHERED_COPPER = Block.WeatheredCopper
OXIDIZED_COPPER = Block.OxidizedCopper
BLOCK_OF_NETHERITE = Block.BlockOfNetherite
SHROOMLIGHT = Block.Shroomlight
CRIMSON_DOOR = Block.CrimsonDoor
BASALT = Block.Basalt
POLISHED_BASALT = Block.PolishedBasalt
BLACKSTONE = Block.Blackstone
POLISHED_BLACKSTONE = Block.PolishedBlackstone
AZALEA_LEAVES = Block.AzaleaLeaves
POINTED_DRIPSTONE = Block.PointedDripstone
BIG_DRIPLEAF = Block.BigDripleaf
AZALEA = Block.Azalea
FLOWERING_AZALEA = Block.FloweringAzalea
AMETHYST_BLOCK = Block.AmethystBlock
AMETHYST_CLUSTER = Block.AmethystCluster
CRYING_OBSIDIAN = Block.CryingObsidian
LIGHTNING_ROD = Block.LightningRod
WARPED_BUTTON = Block.WarpedButton
CRIMSON_PRESSURE_PLATE = Block.CrimsonPressurePlate
WARPED_PRESSURE_PLATE = Block.WarpedPressurePlate
TARGET = Block.Target
WARPED_DOOR = Block.WarpedDoor
POWDER_SNOW = Block.PowderSnow
IRON_DOOR = Block.IronDoor
SOUL_CAMPFIRE = Block.SoulCampfire
ACACIA_SIGN = Block.AcaciaSign
BIRCH_SIGN = Block.BirchSign
SLATE = Block.Slate
POSTER = Block.Poster
BOARD = Block.Board
CRIMSON_SIGN = Block.CrimsonSign
DARK_OAK_SIGN = Block.DarkOakSign
JUNGLE_SIGN = Block.JungleSign
MANGROVE_BUTTON = Block.MangroveButton
MANGROVE_DOOR = Block.MangroveDoor
MANGROVE_FENCE = Block.MangroveFence
MANGROVE_FENCE_GATE = Block.MangroveFenceGate
MANGROVE_LEAVES = Block.MangroveLeaves
MANGROVE_LOG = Block.MangroveLog
MANGROVE_PLANKS = Block.MangrovePlanks
MANGROVE_PRESSURE_PLATE = Block.MangrovePressurePlate
MANGROVE_PROPAGULE = Block.MangrovePropagule
MANGROVE_ROOTS = Block.MangroveRoots
MANGROVE_SLAB = Block.MangroveSlab
MANGROVE_STAIRS = Block.MangroveStairs
MANGROVE_SIGN = Block.MangroveSign
MANGROVE_TRAPDOOR = Block.MangroveTrapdoor
MANGROVE_WOOD = Block.MangroveWood
MUD = Block.Mud
MUD_BRICKS = Block.MudBricks
MUDDY_MANGROVE_ROOTS = Block.MuddyMangroveRoots
OCHRE_FROGLIGHT = Block.OchreFroglight
PACKED_MUD = Block.PackedMud
PEARLESCENT_FROGLIGHT = Block.PearlescentFroglight
REINFORCED_DEEPSLATE = Block.ReinforcedDeepslate
SCULK = Block.Sculk
SCULK_CATALYST = Block.SculkCatalyst
SCULK_SHRIEKER = Block.SculkShrieker
SCULK_VEIN = Block.SculkVein
SPRUCE_SIGN = Block.SpruceSign
STRIPPED_MANGROVE_LOG = Block.StrippedMangroveLog
STRIPPED_MANGROVE_WOOD = Block.StrippedMangroveWood
VERDANT_FROGLIGHT = Block.VerdantFroglight
WARPED_SIGN = Block.WarpedSign
ACACIA_DOOR = Block.AcaciaDoor
FLOWERING_AZALEA_LEAVES = Block.FloweringAzaleaLeaves
BIRCH_DOOR = Block.BirchDoor
DARK_OAK_DOOR = Block.DarkOakDoor
JUNGLE_DOOR = Block.JungleDoor
SPRUCE_DOOR = Block.SpruceDoor
OAK_DOOR = Block.OakDoor
BLOCK_OF_RAW_IRON = Block.BlockOfRawIron
BANNER = Block.Banner
SMOOTH_RED_SANDSTONE_SLAB = Block.SmoothRedSandstoneSlab
OAK_SIGN = Block.OakSign
WARPED_FUNGUS = Block.WarpedFungus
BIRCH_WOOD = Block.BirchWood
ACACIA_WOOD = Block.AcaciaWood
STONE_SLAB = Block.StoneSlab
BLOCK_OF_BAMBOO = Block.BlockOfBamboo
BAMBOO_BUTTON = Block.BambooButton
BAMBOO_FENCE = Block.BambooFence
BAMBOO_FENCE_GATE = Block.BambooFenceGate
BAMBOO_MOSAIC = Block.BambooMosaic
BAMBOO_MOSAIC_SLAB = Block.BambooMosaicSlab
BAMBOO_MOSAIC_STAIRS = Block.BambooMosaicStairs
BAMBOO_PLANKS = Block.BambooPlanks
BAMBOO_PRESSURE_PLATE = Block.BambooPressurePlate
BAMBOO_SLAB = Block.BambooSlab
BAMBOO_STAIRS = Block.BambooStairs
BAMBOO_STANDING_SIGN = Block.BambooStandingSign
BAMBOO_TRAPDOOR = Block.BambooTrapdoor
CHERRY_BUTTON = Block.CherryButton
CHERRY_FENCE = Block.CherryFence
CHERRY_FENCE_GATE = Block.CherryFenceGate
CHERRY_LEAVES = Block.CherryLeaves
CHERRY_LOG = Block.CherryLog
CHERRY_PLANKS = Block.CherryPlanks
CHERRY_PRESSURE_PLATE = Block.CherryPressurePlate
CHERRY_SAPLING = Block.CherrySapling
CHERRY_SLAB = Block.CherrySlab
CHERRY_STAIRS = Block.CherryStairs
CHERRY_STANDING_SIGN = Block.CherryStandingSign
CHERRY_TRAPDOOR = Block.CherryTrapdoor
CHERRY_WOOD = Block.CherryWood
CHISELED_BOOKSHELF = Block.ChiseledBookshelf
MOSS_BLOCK = Block.MossBlock
BLOCK_OF_STRIPPED_BAMBOO = Block.BlockOfStrippedBamboo
STRIPPED_CHERRY_LOG = Block.StrippedCherryLog
STRIPPED_CHERRY_WOOD = Block.StrippedCherryWood
SUSPICIOUS_GRAVEL = Block.SuspiciousGravel
SUSPICIOUS_SAND = Block.SuspiciousSand
TORCHFLOWER = Block.Torchflower
CHISELED_TUFF = Block.ChiseledTuff
CHISELED_TUFF_BRICKS = Block.ChiseledTuffBricks
COPPER_DOOR = Block.CopperDoor
COPPER_TRAPDOOR = Block.CopperTrapdoor
CRAFTER = Block.Crafter
POLISHED_TUFF = Block.PolishedTuff
POLISHED_TUFF_SLAB = Block.PolishedTuffSlab
POLISHED_TUFF_STAIRS = Block.PolishedTuffStairs
POLISHED_TUFF_WALL = Block.PolishedTuffWall
SHORT_GRASS = Block.ShortGrass
TUFF = Block.Tuff
TUFF_BRICK_SLAB = Block.TuffBrickSlab
TUFF_BRICK_STAIRS = Block.TuffBrickStairs
TUFF_BRICK_WALL = Block.TuffBrickWall
TUFF_BRICKS = Block.TuffBricks
TUFF_SLAB = Block.TuffSlab
TUFF_STAIRS = Block.TuffStairs
TUFF_WALL = Block.TuffWall
BLACK_CANDLE = Block.BlackCandle
BLUE_CANDLE = Block.BlueCandle
BROWN_CANDLE = Block.BrownCandle
BUSH = Block.Bush
CACTUS_FLOWER = Block.CactusFlower
CANDLE = Block.Candle
CLOSED_EYEBLOSSOM = Block.ClosedEyeblossom
CREAKING_HEART = Block.CreakingHeart
CYAN_CANDLE = Block.CyanCandle
DRIED_GHAST = Block.DriedGhast
FIREFLY_BUSH = Block.FireflyBush
GRAY_CANDLE = Block.GrayCandle
GREEN_CANDLE = Block.GreenCandle
LEAF_LITTER = Block.LeafLitter
LIGHT_BLUE_CANDLE = Block.LightBlueCandle
LIGHT_GRAY_CANDLE = Block.LightGrayCandle
LIME_CANDLE = Block.LimeCandle
MAGENTA_CANDLE = Block.MagentaCandle
OPEN_EYEBLOSSOM = Block.OpenEyeblossom
ORANGE_CANDLE = Block.OrangeCandle
PALE_HANGING_MOSS = Block.PaleHangingMoss
PALE_MOSS_BLOCK = Block.PaleMossBlock
PALE_MOSS_CARPET = Block.PaleMossCarpet
PALE_OAK_BUTTON = Block.PaleOakButton
PALE_OAK_DOOR = Block.PaleOakDoor
PALE_OAK_FENCE = Block.PaleOakFence
PALE_OAK_FENCE_GATE = Block.PaleOakFenceGate
PALE_OAK_HANGING_SIGN = Block.PaleOakHangingSign
PALE_OAK_LEAVES = Block.PaleOakLeaves
PALE_OAK_LOG = Block.PaleOakLog
PALE_OAK_PLANKS = Block.PaleOakPlanks
PALE_OAK_PRESSURE_PLATE = Block.PaleOakPressurePlate
PALE_OAK_SAPLING = Block.PaleOakSapling
PALE_OAK_SLAB = Block.PaleOakSlab
PALE_OAK_STAIRS = Block.PaleOakStairs
PALE_OAK_STANDING_SIGN = Block.PaleOakStandingSign
PALE_OAK_TRAPDOOR = Block.PaleOakTrapdoor
PALE_OAK_WOOD = Block.PaleOakWood
PINK_CANDLE = Block.PinkCandle
PURPLE_CANDLE = Block.PurpleCandle
RED_CANDLE = Block.RedCandle
BLOCK_OF_RESIN = Block.BlockOfResin
TALL_DRY_GRASS = Block.TallDryGrass
WHITE_CANDLE = Block.WhiteCandle
WILDFLOWERS = Block.Wildflowers
YELLOW_CANDLE = Block.YellowCandle


CHICKEN = AnimalMob.Chicken
COW = AnimalMob.Cow
PIG = AnimalMob.Pig
SHEEP = AnimalMob.Sheep
WOLF = AnimalMob.Wolf
VILLAGER = AnimalMob.Villager
MUSHROOM_COW = AnimalMob.MushroomCow
SQUID = AnimalMob.Squid
RABBIT = AnimalMob.Rabbit
BAT = AnimalMob.Bat
OCELOT = AnimalMob.Ocelot
HORSE = AnimalMob.Horse
DONKEY = AnimalMob.Donkey
MULE = AnimalMob.Mule
SKELETON_HORSE = AnimalMob.SkeletonHorse
ZOMBIE_HORSE = AnimalMob.ZombieHorse
POLAR_BEAR = AnimalMob.PolarBear
LLAMA = AnimalMob.Llama
PARROT = AnimalMob.Parrot
DOLPHIN = AnimalMob.Dolphin
SEA_TURTLE = AnimalMob.SeaTurtle
CAT = AnimalMob.Cat
PUFFERFISH = AnimalMob.Pufferfish
SALMON = AnimalMob.Salmon
TROPICAL_FISH = AnimalMob.TropicalFish
COD = AnimalMob.Cod
PANDA = AnimalMob.Panda
WANDERING_TRADER = AnimalMob.WanderingTrader
FOX = AnimalMob.Fox
BEE = AnimalMob.Bee
AXOLOTL = AnimalMob.Axolotl
GLOW_SQUID = AnimalMob.GlowSquid
GOAT = AnimalMob.Goat
STRIDER = AnimalMob.Strider
ALLAY = AnimalMob.Allay
FROG = AnimalMob.Frog
TADPOLE = AnimalMob.Tadpole
CAMEL = AnimalMob.Camel
SNIFFER = AnimalMob.Sniffer
ARMADILLO = AnimalMob.Armadillo
AGENT = AnimalMob.Agent
HAPPY_GHAST = AnimalMob.HappyGhast


WALK = TravelMethod.Walk
SWIM_WATER = TravelMethod.SwimWater
FALL = TravelMethod.Fall
CLIMB = TravelMethod.Climb
SWIM_LAVA = TravelMethod.SwimLava
FLY = TravelMethod.Fly
RIDING = TravelMethod.Riding
SNEAK = TravelMethod.Sneak
SPRINT = TravelMethod.Sprint
BOUNCE = TravelMethod.Bounce
FROST_WALK = TravelMethod.FrostWalk
TELEPORT = TravelMethod.Teleport


IRON_SHOVEL = Item.IronShovel
IRON_PICKAXE = Item.IronPickaxe
IRON_AXE = Item.IronAxe
FLINT_AND_STEEL = Item.FlintAndSteel
APPLE = Item.Apple
BOW = Item.Bow
ARROW = Item.Arrow
COAL = Item.Coal
CHARCOAL = Item.Charcoal
DIAMOND = Item.Diamond
IRON_INGOT = Item.IronIngot
GOLD_INGOT = Item.GoldIngot
IRON_SWORD = Item.IronSword
WOODEN_SWORD = Item.WoodenSword
WOODEN_SHOVEL = Item.WoodenShovel
WOODEN_PICKAXE = Item.WoodenPickaxe
WOODEN_AXE = Item.WoodenAxe
STONE_SWORD = Item.StoneSword
STONE_SHOVEL = Item.StoneShovel
STONE_PICKAXE = Item.StonePickaxe
STONE_AXE = Item.StoneAxe
DIAMOND_SWORD = Item.DiamondSword
DIAMOND_SHOVEL = Item.DiamondShovel
DIAMOND_PICKAXE = Item.DiamondPickaxe
DIAMOND_AXE = Item.DiamondAxe
STICK = Item.Stick
BOWL = Item.Bowl
MUSHROOM_STEW = Item.MushroomStew
GOLDEN_SWORD = Item.GoldenSword
GOLDEN_SHOVEL = Item.GoldenShovel
GOLDEN_PICKAXE = Item.GoldenPickaxe
GOLDEN_AXE = Item.GoldenAxe
STRING = Item.String
FEATHER = Item.Feather
GUNPOWDER = Item.Gunpowder
WOODEN_HOE = Item.WoodenHoe
STONE_HOE = Item.StoneHoe
IRON_HOE = Item.IronHoe
DIAMOND_HOE = Item.DiamondHoe
GOLDEN_HOE = Item.GoldenHoe
SEEDS = Item.Seeds
WHEAT = Item.Wheat
BREAD = Item.Bread
LEATHER_CAP = Item.LeatherCap
LEATHER_CHESTPLATE = Item.LeatherChestplate
LEATHER_PANTS = Item.LeatherPants
LEATHER_BOOTS = Item.LeatherBoots
CHAINMAIL_HELMET = Item.ChainmailHelmet
CHAINMAIL_CHESTPLATE = Item.ChainmailChestplate
CHAINMAIL_LEGGINGS = Item.ChainmailLeggings
CHAINMAIL_BOOTS = Item.ChainmailBoots
IRON_HELMET = Item.IronHelmet
IRON_CHESTPLATE = Item.IronChestplate
IRON_LEGGINGS = Item.IronLeggings
IRON_BOOTS = Item.IronBoots
DIAMOND_HELMET = Item.DiamondHelmet
DIAMOND_CHESTPLATE = Item.DiamondChestplate
DIAMOND_LEGGINGS = Item.DiamondLeggings
DIAMOND_BOOTS = Item.DiamondBoots
GOLDEN_HELMET = Item.GoldenHelmet
GOLDEN_CHESTPLATE = Item.GoldenChestplate
GOLDEN_LEGGINGS = Item.GoldenLeggings
GOLDEN_BOOTS = Item.GoldenBoots
FLINT = Item.Flint
RAW_PORKCHOP = Item.RawPorkchop
COOKED_PORKCHOP = Item.CookedPorkchop
PAINTING = Item.Painting
GOLDEN_APPLE = Item.GoldenApple
OAK_DOOR_ITEM = Item.OakDoor
BUCKET = Item.Bucket
MILK = Item.Milk
BUCKET_OF_COD = Item.BucketOfCod
BUCKET_OF_SALMON = Item.BucketOfSalmon
BUCKET_OF_TROPICAL_FISH = Item.BucketOfTropicalFish
WATER_BUCKET = Item.WaterBucket
LAVA_BUCKET = Item.LavaBucket
MINECART = Item.Minecart
SADDLE = Item.Saddle
IRON_DOOR_ITEM = Item.IronDoor
REDSTONE = Item.Redstone
SNOWBALL = Item.Snowball
BOAT = Item.Boat
SPRUCE_BOAT = Item.SpruceBoat
BIRCH_BOAT = Item.BirchBoat
JUNGLE_BOAT = Item.JungleBoat
ACACIA_BOAT = Item.AcaciaBoat
DARK_OAK_BOAT = Item.DarkOakBoat
LEATHER = Item.Leather
KELP_ITEM = Item.Kelp
BRICK = Item.Brick
CLAY_BALL = Item.ClayBall
REEDS = Item.Reeds
PAPER = Item.Paper
BOOK = Item.Book
SLIMEBALL = Item.Slimeball
MINECART_WITH_CHEST = Item.MinecartWithChest
EGG = Item.Egg
COMPASS = Item.Compass
FISHING_ROD = Item.FishingRod
CLOCK = Item.Clock
GLOWSTONE_DUST = Item.GlowstoneDust
RAW_FISH = Item.RawFish
COOKED_FISH = Item.CookedFish
INK_SAC = Item.InkSac
ROSE_RED = Item.RoseRed
CACTUS_GREEN = Item.CactusGreen
COCOA_BEANS = Item.CocoaBeans
LAPIS_LAZULI = Item.LapisLazuli
PURPLE_DYE = Item.PurpleDye
CYAN_DYE = Item.CyanDye
LIGHT_GRAY_DYE = Item.LightGrayDye
GRAY_DYE = Item.GrayDye
PINK_DYE = Item.PinkDye
LIME_DYE = Item.LimeDye
DANDELION_YELLOW = Item.DandelionYellow
LIGHT_BLUE_DYE = Item.LightBlueDye
MAGENTA_DYE = Item.MagentaDye
ORANGE_DYE = Item.OrangeDye
BONE_MEAL = Item.BoneMeal
BONE = Item.Bone
SUGAR = Item.Sugar
CAKE_ITEM = Item.Cake
BED_ITEM = Item.Bed
ORANGE_BED = Item.OrangeBed
MAGENTA_BED = Item.MagentaBed
LIGHT_BLUE_BED = Item.LightBlueBed
YELLOW_BED = Item.YellowBed
LIME_BED = Item.LimeBed
PINK_BED = Item.PinkBed
GRAY_BED = Item.GrayBed
LIGHT_GRAY_BED = Item.LightGrayBed
CYAN_BED = Item.CyanBed
PURPLE_BED = Item.PurpleBed
BLUE_BED = Item.BlueBed
BROWN_BED = Item.BrownBed
GREEN_BED = Item.GreenBed
RED_BED = Item.RedBed
BLACK_BED = Item.BlackBed
REPEATER = Item.Repeater
COOKIE = Item.Cookie
MAP = Item.Map
SHEARS = Item.Shears
MELON = Item.Melon
PUMPKIN_SEEDS = Item.PumpkinSeeds
MELON_SEEDS = Item.MelonSeeds
RAW_BEEF = Item.RawBeef
COOKED_BEEF = Item.CookedBeef
RAW_CHICKEN = Item.RawChicken
COOKED_CHICKEN = Item.CookedChicken
ROTTEN_FLESH = Item.RottenFlesh
ENDER_PEARL = Item.EnderPearl
BLAZE_ROD = Item.BlazeRod
GHAST_TEAR = Item.GhastTear
GOLD_NUGGET = Item.GoldNugget
NETHER_WART_ITEM = Item.NetherWart
GLASS_BOTTLE = Item.GlassBottle
SPIDER_EYE = Item.SpiderEye
FERMENTED_SPIDER_EYE = Item.FermentedSpiderEye
BLAZE_POWDER = Item.BlazePowder
MAGMA_CREAM = Item.MagmaCream
BREWING_STAND_ITEM = Item.BrewingStand
CAULDRON_ITEM = Item.Cauldron
ENDER_EYE = Item.EnderEye
GLISTERING_MELON = Item.GlisteringMelon
SPAWN_CHICKEN = Item.SpawnChicken
SPAWN_COW = Item.SpawnCow
SPAWN_PIG = Item.SpawnPig
SPAWN_SHEEP = Item.SpawnSheep
SPAWN_WOLF = Item.SpawnWolf
SPAWN_VILLAGER = Item.SpawnVillager
SPAWN_MOOSHROOM = Item.SpawnMooshroom
SPAWN_SQUID = Item.SpawnSquid
SPAWN_RABBIT = Item.SpawnRabbit
SPAWN_BAT = Item.SpawnBat
SPAWN_OCELOT = Item.SpawnOcelot
SPAWN_HORSE = Item.SpawnHorse
SPAWN_DONKEY = Item.SpawnDonkey
SPAWN_MULE = Item.SpawnMule
SPAWN_SKELETON_HORSE = Item.SpawnSkeletonHorse
SPAWN_ZOMBIE_HORSE = Item.SpawnZombieHorse
SPAWN_POLAR_BEAR = Item.SpawnPolarBear
SPAWN_LLAMA = Item.SpawnLlama
SPAWN_PARROT = Item.SpawnParrot
SPAWN_DOLPHIN = Item.SpawnDolphin
SPAWN_RAVAGER = Item.SpawnRavager
SPAWN_ZOMBIE = Item.SpawnZombie
SPAWN_CREEPER = Item.SpawnCreeper
SPAWN_SKELETON = Item.SpawnSkeleton
SPAWN_SPIDER = Item.SpawnSpider
SPAWN_ZOMBIE_PIGMAN = Item.SpawnZombiePigman
SPAWN_SLIME = Item.SpawnSlime
SPAWN_ENDERMAN = Item.SpawnEnderman
SPAWN_SILVERFISH = Item.SpawnSilverfish
SPAWN_CAVE_SPIDER = Item.SpawnCaveSpider
SPAWN_GHAST = Item.SpawnGhast
SPAWN_MAGMA_CUBE = Item.SpawnMagmaCube
SPAWN_BLAZE = Item.SpawnBlaze
SPAWN_ZOMBIE_VILLAGER = Item.SpawnZombieVillager
SPAWN_WITCH = Item.SpawnWitch
SPAWN_STRAY = Item.SpawnStray
SPAWN_HUSK = Item.SpawnHusk
SPAWN_WITHER_SKELETON = Item.SpawnWitherSkeleton
SPAWN_GUARDIAN = Item.SpawnGuardian
SPAWN_ELDER_GUARDIAN = Item.SpawnElderGuardian
SPAWN_SHULKER = Item.SpawnShulker
SPAWN_ENDERMITE = Item.SpawnEndermite
SPAWN_VINDICATOR = Item.SpawnVindicator
SPAWN_PHANTOM = Item.SpawnPhantom
SPAWN_SEA_TURTLE = Item.SpawnSeaTurtle
SPAWN_CAT = Item.SpawnCat
SPAWN_EVOKER = Item.SpawnEvoker
SPAWN_VEX = Item.SpawnVex
SPAWN_PUFFERFISH = Item.SpawnPufferfish
SPAWN_SALMON = Item.SpawnSalmon
SPAWN_DROWNED = Item.SpawnDrowned
SPAWN_TROPICAL_FISH = Item.SpawnTropicalFish
SPAWN_COD = Item.SpawnCod
SPAWN_FOX = Item.SpawnFox
SPAWN_PANDA = Item.SpawnPanda
SPAWN_PILLAGER = Item.SpawnPillager
SPAWN_WANDERING_TRADER = Item.SpawnWanderingTrader
SPAWN_BEE = Item.SpawnBee
EXPERIENCE_BOTTLE = Item.ExperienceBottle
FIREBALL = Item.Fireball
BOOK_QUILL = Item.BookQuill
EMERALD = Item.Emerald
ITEM_FRAME = Item.ItemFrame
FLOWER_POT_ITEM = Item.FlowerPot
CARROT = Item.Carrot
POTATO = Item.Potato
BAKED_POTATO = Item.BakedPotato
POISONOUS_POTATO = Item.PoisonousPotato
EMPTY_MAP = Item.EmptyMap
EMPTY_LOCATOR_MAP = Item.EmptyLocatorMap
GOLDEN_CARROT = Item.GoldenCarrot
CARROT_ON_A_STICK = Item.CarrotOnAStick
NETHER_STAR = Item.NetherStar
PUMPKIN_PIE = Item.PumpkinPie
ENCHANTED_BOOK = Item.EnchantedBook
COMPARATOR = Item.Comparator
NETHERBRICK = Item.Netherbrick
QUARTZ = Item.Quartz
MINECART_WITH_T_N_T = Item.MinecartWithTNT
MINECART_WITH_HOPPER = Item.MinecartWithHopper
PRISMARINE_SHARD = Item.PrismarineShard
HOPPER_ITEM = Item.Hopper
RAW_RABBIT = Item.RawRabbit
COOKED_RABBIT = Item.CookedRabbit
RABBIT_STEW = Item.RabbitStew
RABBIT_FOOT = Item.RabbitFoot
RABBIT_HIDE = Item.RabbitHide
LEATHER_HORSE_ARMOR = Item.LeatherHorseArmor
IRON_HORSE_ARMOR = Item.IronHorseArmor
GOLD_HORSE_ARMOR = Item.GoldHorseArmor
DIAMOND_HORSE_ARMOR = Item.DiamondHorseArmor
LEAD = Item.Lead
NAME_TAG = Item.NameTag
PRISMARINE_CRYSTALS = Item.PrismarineCrystals
RAW_MUTTON = Item.RawMutton
COOKED_MUTTON = Item.CookedMutton
ARMOR_STAND = Item.ArmorStand
END_CRYSTAL = Item.EndCrystal
SPRUCE_DOOR_ITEM = Item.SpruceDoor
BIRCH_DOOR_ITEM = Item.BirchDoor
JUNGLE_DOOR_ITEM = Item.JungleDoor
ACACIA_DOOR_ITEM = Item.AcaciaDoor
DARK_OAK_DOOR_ITEM = Item.DarkOakDoor
CHORUS_FRUIT = Item.ChorusFruit
CHORUS_FRUIT_POPPED = Item.ChorusFruitPopped
DRAGON_S_BREATH = Item.DragonSBreath
ELYTRA = Item.Elytra
SHULKER_SHELL = Item.ShulkerShell
TOTEM = Item.Totem
IRON_NUGGET = Item.IronNugget
TRIDENT = Item.Trident
BEETROOT_ITEM = Item.Beetroot
BEETROOT_SEEDS = Item.BeetrootSeeds
BEETROOT_SOUP = Item.BeetrootSoup
RAW_SALMON = Item.RawSalmon
CLOWNFISH = Item.Clownfish
PUFFERFISH_ITEM = Item.Pufferfish
COOKED_SALMON = Item.CookedSalmon
DRIED_KELP = Item.DriedKelp
ENCHANTED_APPLE = Item.EnchantedApple
HEART_OF_THE_SEA = Item.HeartOfTheSea
SWEET_BERRIES = Item.SweetBerries
CAMPFIRE_ITEM = Item.Campfire
HONEYCOMB = Item.Honeycomb
HONEY_BOTTLE = Item.HoneyBottle
SPAWN_PIGLIN = Item.SpawnPiglin
NETHERITE_INGOT = Item.NetheriteIngot
COPPER_INGOT = Item.CopperIngot
GREEN_DYE = Item.GreenDye
GLOW_BERRIES = Item.GlowBerries
RED_DYE = Item.RedDye
YELLOW_DYE = Item.YellowDye
GLOW_INK_SAC = Item.GlowInkSac
NETHERITE_SWORD = Item.NetheriteSword
SPAWN_ZOMBIFIED_PIGLIN = Item.SpawnZombifiedPiglin
SPAWN_GLOW_SQUID = Item.SpawnGlowSquid
SPAWN_STRIDER = Item.SpawnStrider
SPAWN_HOGLIN = Item.SpawnHoglin
SPAWN_ZOGLIN = Item.SpawnZoglin
SPAWN_GOAT = Item.SpawnGoat
SPAWN_AXOLOTL = Item.SpawnAxolotl
NETHERITE_HELMET = Item.NetheriteHelmet
NETHERITE_CHESTPLATE = Item.NetheriteChestplate
NETHERITE_LEGGINGS = Item.NetheriteLeggings
NETHERITE_BOOTS = Item.NetheriteBoots
NETHERITE_AXE = Item.NetheriteAxe
NETHERITE_PICKAXE = Item.NetheritePickaxe
RAW_COPPER = Item.RawCopper
NETHERITE_SHOVEL = Item.NetheriteShovel
NETHERITE_HOE = Item.NetheriteHoe
WARPED_FUNGUS_ON_A_STICK = Item.WarpedFungusOnAStick
POWDER_SNOW_BUCKET = Item.PowderSnowBucket
BUCKET_OF_AXOLOTL = Item.BucketOfAxolotl
RAW_IRON = Item.RawIron
RAW_GOLD = Item.RawGold
NETHERITE_SCRAP = Item.NetheriteScrap
SPAWN_ALLAY = Item.SpawnAllay
ECHO_SHARD = Item.EchoShard
SPAWN_FROG = Item.SpawnFrog
GOAT_HORN = Item.GoatHorn
MANGROVE_BOAT = Item.MangroveBoat
MANGROVE_BOAT_WITH_CHEST = Item.MangroveBoatWithChest
RECOVERY_COMPASS = Item.RecoveryCompass
BUCKET_OF_TADPOLE = Item.BucketOfTadpole
SPAWN_TADPOLE = Item.SpawnTadpole
SPAWN_WARDEN = Item.SpawnWarden
SPAWN_TRADER_LLAMA = Item.SpawnTraderLlama
TROPICAL_FISH_ITEM = Item.TropicalFish
BAMBOO_RAFT = Item.BambooRaft
SPAWN_CAMEL = Item.SpawnCamel
SPAWN_SNIFFER = Item.SpawnSniffer
SHIELD = Item.Shield
MACE = Item.Mace
WIND_CHARGE = Item.WindCharge
WOLF_ARMOR = Item.WolfArmor
SPAWN_ARMADILLO = Item.SpawnArmadillo
SPAWN_BREEZE = Item.SpawnBreeze
BLACK_HARNESS = Item.BlackHarness
BLUE_HARNESS = Item.BlueHarness
BROWN_HARNESS = Item.BrownHarness
CYAN_HARNESS = Item.CyanHarness
GRAY_HARNESS = Item.GrayHarness
GREEN_HARNESS = Item.GreenHarness
LIGHT_BLUE_HARNESS = Item.LightBlueHarness
LIGHT_GRAY_HARNESS = Item.LightGrayHarness
LIME_HARNESS = Item.LimeHarness
PALE_OAK_BOAT_WITH_CHEST = Item.PaleOakBoatWithChest
PURPLE_HARNESS = Item.PurpleHarness
RED_HARNESS = Item.RedHarness
WHITE_HARNESS = Item.WhiteHarness
YELLOW_HARNESS = Item.YellowHarness


PRIMED_TNT = ProjectileMob.PrimedTnt
XP_BOTTLE = ProjectileMob.XpBottle
XP_ORB = ProjectileMob.XpOrb
FIREWORKS_ROCKET = ProjectileMob.FireworksRocket
ARROW_PROJECTILE_MOB = ProjectileMob.Arrow
SNOWBALL_PROJECTILE_MOB = ProjectileMob.Snowball
EGG_PROJECTILE_MOB = ProjectileMob.Egg
SPLASH_POTION = ProjectileMob.SplashPotion
LIGHTNING_BOLT = ProjectileMob.LightningBolt
EVOCATION_FANG = ProjectileMob.EvocationFang


ZOMBIE = MonsterMob.Zombie
CREEPER = MonsterMob.Creeper
SKELETON = MonsterMob.Skeleton
SPIDER = MonsterMob.Spider
PIG_ZOMBIE = MonsterMob.PigZombie
SLIME = MonsterMob.Slime
ENDERMAN = MonsterMob.Enderman
SILVERFISH = MonsterMob.Silverfish
CAVE_SPIDER = MonsterMob.CaveSpider
GHAST = MonsterMob.Ghast
LAVA_SLIME = MonsterMob.LavaSlime
BLAZE = MonsterMob.Blaze
ZOMBIE_VILLAGER = MonsterMob.ZombieVillager
WITCH = MonsterMob.Witch
STRAY = MonsterMob.Stray
HUSK = MonsterMob.Husk
WITHER_SKELETON = MonsterMob.WitherSkeleton
GUARDIAN = MonsterMob.Guardian
ELDER_GUARDIAN = MonsterMob.ElderGuardian
SHULKER = MonsterMob.Shulker
ENDERMITE = MonsterMob.Endermite
VINDICATOR = MonsterMob.Vindicator
PHANTOM = MonsterMob.Phantom
RAVAGER = MonsterMob.Ravager
EVOKER = MonsterMob.Evoker
VEX = MonsterMob.Vex
DROWNED = MonsterMob.Drowned
PILLAGER = MonsterMob.Pillager
HOGLIN = MonsterMob.Hoglin
PIGLIN = MonsterMob.Piglin
ZOGLIN = MonsterMob.Zoglin
WARDEN = MonsterMob.Warden
BREEZE = MonsterMob.Breeze
CREAKING = MonsterMob.Creaking
ENDER_DRAGON = MonsterMob.EnderDragon
IRON_GOLEM = MonsterMob.IronGolem
PIGLIN_BRUTE = MonsterMob.PiglinBrute
SNOW_GOLEM = MonsterMob.SnowGolem
WITHER_MONSTER_MOB = MonsterMob.Wither


SPEED = Effect.Speed
SLOWNESS = Effect.Slowness
HASTE = Effect.Haste
MINING_FATIGUE = Effect.MiningFatigue
STRENGTH = Effect.Strength
JUMP_BOOST = Effect.JumpBoost
NAUSEA = Effect.Nausea
REGENERATION = Effect.Regeneration
RESISTANCE = Effect.Resistance
FIRE_RESISTANCE = Effect.FireResistance
WATER_BREATHING = Effect.WaterBreathing
INVISIBILITY = Effect.Invisibility
BLINDNESS = Effect.Blindness
NIGHT_VISION = Effect.NightVision
HUNGER = Effect.Hunger
WEAKNESS = Effect.Weakness
POISON = Effect.Poison
WITHER = Effect.Wither
HEALTH_BOOST = Effect.HealthBoost
ABSORPTION = Effect.Absorption
LEVITATION = Effect.Levitation


ATTACK = AgentCommand.Attack
DESTROY = AgentCommand.Destroy
TILL = AgentCommand.Till
DROP_ALL = AgentCommand.DropAll


PLACE_ON_MOVE = AgentAssist.PlaceOnMove
PLACE_FROM_ANY_SLOT = AgentAssist.PlaceFromAnySlot
DESTROY_OBSTACLES = AgentAssist.DestroyObstacles


WEST = CompassDirection.West
EAST = CompassDirection.East
NORTH = CompassDirection.North
SOUTH = CompassDirection.South


NORTH_CARDINAL_DIRECTION = CardinalDirection.North
EAST_CARDINAL_DIRECTION = CardinalDirection.East
SOUTH_CARDINAL_DIRECTION = CardinalDirection.South
UP_CARDINAL_DIRECTION = CardinalDirection.Up
WEST_CARDINAL_DIRECTION = CardinalDirection.West
DOWN_CARDINAL_DIRECTION = CardinalDirection.Down


WHITE = BlockColor.White
ORANGE = BlockColor.Orange
MAGENTA = BlockColor.Magenta
LIGHT_BLUE = BlockColor.LightBlue
YELLOW = BlockColor.Yellow
LIME = BlockColor.Lime
PINK = BlockColor.Pink
GRAY = BlockColor.Gray
LIGHT_GRAY = BlockColor.LightGray
CYAN = BlockColor.Cyan
PURPLE = BlockColor.Purple
BLUE = BlockColor.Blue
BROWN = BlockColor.Brown
GREEN = BlockColor.Green
RED = BlockColor.Red
BLACK = BlockColor.Black


DAY = DayTime.Day
DAWN = DayTime.Dawn
MIDDAY = DayTime.Midday
DUSK = DayTime.Dusk
NIGHT = DayTime.Night
MIDNIGHT = DayTime.Midnight


PV_P = GameRule.PvP
DROWNING_DAMAGE = GameRule.DrowningDamage
FALL_DAMAGE = GameRule.FallDamage
FIRE_DAMAGE = GameRule.FireDamage
DAYLIGHT_CYCLE = GameRule.DaylightCycle
MOB_LOOT = GameRule.MobLoot
MOB_SPAWNING = GameRule.MobSpawning
WEATHER_CYCLE = GameRule.WeatherCycle
MOB_GRIEFING = GameRule.MobGriefing
TILE_DROPS = GameRule.TileDrops
KEEP_INVENTORY = GameRule.KeepInventory
TNT_EXPLODES = GameRule.TntExplodes
NATURAL_REGENERATION = GameRule.NaturalRegeneration
COMMAND_BLOCK_OUTPUT = GameRule.CommandBlockOutput
ENTITY_DROPS = GameRule.EntityDrops
DO_FIRE_TICK = GameRule.DoFireTick
SHOW_COORDINATES = GameRule.ShowCoordinates


SURVIVAL = GameMode.Survival
CREATIVE = GameMode.Creative
ADVENTURE = GameMode.Adventure


CLEAR = Weather.Clear
RAIN = Weather.Rain
THUNDER = Weather.Thunder


PEACEFUL = GameDifficulty.Peaceful
EASY = GameDifficulty.Easy
NORMAL = GameDifficulty.Normal
HARD = GameDifficulty.Hard


GAME_TIME = TimeQuery.GameTime
DAY_TIME = TimeQuery.DayTime
DAY_TIME_QUERY = TimeQuery.Day
REAL_LIFE = TimeQuery.RealLife


BLOCK_BOTTOM_EAST_WHEN_OFF = LeverPosition.BlockBottomEastWhenOff
BLOCK_SIDE_FACING_EAST = LeverPosition.BlockSideFacingEast
BLOCK_SIDE_FACING_WEST = LeverPosition.BlockSideFacingWest
BLOCK_SIDE_FACING_SOUTH = LeverPosition.BlockSideFacingSouth
BLOCK_SIDE_FACING_NORTH = LeverPosition.BlockSideFacingNorth
BLOCK_TOP_POINTS_SOUTH_WHEN_OFF = LeverPosition.BlockTopPointsSouthWhenOff
BLOCK_TOP_POINTS_EAST_WHEN_OFF = LeverPosition.BlockTopPointsEastWhenOff
BLOCK_BOTTOM_POINTS_SOUTH_WHEN_OFF = LeverPosition.BlockBottomPointsSouthWhenOff


WOOL_COLORED_BLOCK = ColoredBlock.Wool
CONCRETE = ColoredBlock.Concrete


MEMORY = StructureSaveMode.Memory
DISK = StructureSaveMode.Disk


DEGREES0 = StructureRotation.Degrees0
DEGREES90 = StructureRotation.Degrees90
DEGREES180 = StructureRotation.Degrees180
DEGREES270 = StructureRotation.Degrees270


NONE = StructureMirrorAxis.None
X = StructureMirrorAxis.X
Z = StructureMirrorAxis.Z
XZ = StructureMirrorAxis.XZ


NONE_STRUCTURE_ANIMATION_MODE = StructureAnimationMode.None
BLOCK_BY_BLOCK = StructureAnimationMode.BlockByBlock
LAYER_BY_LAYER = StructureAnimationMode.LayerByLayer


EXPLOSION_HUGE = Particle.ExplosionHuge
BALLOON_GAS = Particle.BalloonGas
BASIC_CRIT = Particle.BasicCrit
BASIC_FLAME = Particle.BasicFlame
BASIC_PORTAL = Particle.BasicPortal
BLEACH = Particle.Bleach
BLUE_FLAME = Particle.BlueFlame
CANDLE_FLAME = Particle.CandleFlame
COLORED_FLAME = Particle.ColoredFlame
CRITICAL_HIT = Particle.CriticalHit
CROP_GROWTH = Particle.CropGrowth
CROP_GROWTH_AREA = Particle.CropGrowthArea
DRAGON_BREATH_FIRE = Particle.DragonBreathFire
DRAGON_BREATH_TRAIL = Particle.DragonBreathTrail
DRAGON_DESTROY_BLOCK = Particle.DragonDestroyBlock
DRIP_HONEY = Particle.DripHoney
DRIP_LAVA = Particle.DripLava
DRIP_NECTAR = Particle.DripNectar
DRIP_STALACTITE_LAVA = Particle.DripStalactiteLava
DRIP_STALACTITE_WATER = Particle.DripStalactiteWater
DRIP_WATER = Particle.DripWater
DUST_FALLING = Particle.DustFalling
DUST_FALLING_BORDER = Particle.DustFallingBorder
DUST_FALLING_CONCRETE_POWDER = Particle.DustFallingConcretePowder
DUST_FALLING_DRAGON_EGG = Particle.DustFallingDragonEgg
DUST_FALLING_GRAVEL = Particle.DustFallingGravel
DUST_FALLING_RED_SAND = Particle.DustFallingRedSand
DUST_FALLING_SAND = Particle.DustFallingSand
DUST_FALLING_SCAFFOLDING = Particle.DustFallingScaffolding
DUST_FALLING_TOP_SNOW = Particle.DustFallingTopSnow
DUST_LAB_TABLE_HEATBLOCK = Particle.DustLabTableHeatblock
DUST_MYCELIUM = Particle.DustMycelium
DUST_OBSIDIAN_GLOW = Particle.DustObsidianGlow
DUST_REDSTONE_ORE = Particle.DustRedstoneOre
DUST_REDSTONE_REPEATER = Particle.DustRedstoneRepeater
DUST_REDSTONE_TORCH = Particle.DustRedstoneTorch
DUST_REDSTONE_WIRE = Particle.DustRedstoneWire
DUST_RISING_BORDER = Particle.DustRisingBorder
EGG_DESTROY = Particle.EggDestroy
ELEPHANT_TOOTH_PASTE_VAPOR = Particle.ElephantToothPasteVapor
ENCHANTING_TABLE = Particle.EnchantingTable
END_CHEST = Particle.EndChest
ENDROD = Particle.Endrod
EVOCATION_FANG_PARTICLE = Particle.EvocationFang
EXPLOSION = Particle.Explosion
EXPLOSION_CAMERA_SHOOT = Particle.ExplosionCameraShoot
EXPLOSION_CAULDRON = Particle.ExplosionCauldron
EXPLOSION_DEATH = Particle.ExplosionDeath
EXPLOSION_DRAGON_DEATH = Particle.ExplosionDragonDeath
EXPLOSION_DRAGON_DYING = Particle.ExplosionDragonDying
EXPLOSION_HUGE_LAB = Particle.ExplosionHugeLab
EXPLOSION_LARGE = Particle.ExplosionLarge
EXPLOSION_SINGLE = Particle.ExplosionSingle
EYEOFENDER_DEATH_EXPLODE = Particle.EyeofenderDeathExplode
FIRE_VAPOR = Particle.FireVapor
HEART = Particle.Heart
ICE_EVAPORATION = Particle.IceEvaporation
KNOCKBACK_ROAR = Particle.KnockbackRoar
LAB_TABLE_MYSTICAL = Particle.LabTableMystical
LAVA_PARTICLE = Particle.Lava
MAGNESIUM_SALTS = Particle.MagnesiumSalts
MOB_BLOCK_SPAWN = Particle.MobBlockSpawn
MOB_PORTAL = Particle.MobPortal
MOBFLAME = Particle.Mobflame
MOBFLAME_SINGLE = Particle.MobflameSingle
MOBSPELL = Particle.Mobspell
NOTE = Particle.Note
OBSIDIAN_TEAR = Particle.ObsidianTear
PHANTOM_TRAIL = Particle.PhantomTrail
PORTAL_DIRECTIONAL = Particle.PortalDirectional
PORTAL_REVERSE = Particle.PortalReverse
RAIN_SPLASH = Particle.RainSplash
SCULK_SENSOR_REDSTONE = Particle.SculkSensorRedstone
SHRIEK = Particle.Shriek
SHULKER_BULLET = Particle.ShulkerBullet
SILVERFISH_GRIEF = Particle.SilverfishGrief
SMOKE_BASIC = Particle.SmokeBasic
SMOKE_CAMPFIRE = Particle.SmokeCampfire
SMOKE_CAMPFIRE_TALL = Particle.SmokeCampfireTall
SMOKE_LLAMA_SPIT = Particle.SmokeLlamaSpit
SNOWFLAKE = Particle.Snowflake
SOUL = Particle.Soul
SOUL_SCULK = Particle.SoulSculk
SPARKLER = Particle.Sparkler
SPELL_ARROW = Particle.SpellArrow
SPELL_EVOKER = Particle.SpellEvoker
SPELL_SPLASH = Particle.SpellSplash
SPORE_BLOSSOM_AMBIENT = Particle.SporeBlossomAmbient
SPORE_BLOSSOM_SHOWER = Particle.SporeBlossomShower
STUNNED = Particle.Stunned
TOTEM_PARTICLE = Particle.Totem
TOTEM_SINGLE = Particle.TotemSingle
VILLAGER_ANGRY = Particle.VillagerAngry
VILLAGER_HAPPY = Particle.VillagerHappy
WATER_EVAPORATION_ACTOR = Particle.WaterEvaporationActor
WATER_EVAPORATION_BUCKET = Particle.WaterEvaporationBucket
WATER_EVAPORATION_SINGLE = Particle.WaterEvaporationSingle
WATER_SPLASH = Particle.WaterSplash
WATER_SPLASH_SINGLE = Particle.WaterSplashSingle
WATER_WAKE = Particle.WaterWake
WITHER_BOSS_INVULNERABLE = Particle.WitherBossInvulnerable
```

# Other

## Inventory Slot Layout
```
| 01 | 02 | 03 | 04 | 05 | 06 | 07 | 08 | 09 |
|----|----|----|----|----|----|----|----|----|
| 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 |
|----|----|----|----|----|----|----|----|----|
| 19 | 20 | 21 | 22 | 23 | 24 | 25 | 26 | 27 |
```
























