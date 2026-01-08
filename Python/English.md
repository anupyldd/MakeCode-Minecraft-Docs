### Table of contents:
- [Functions](#functions)
  - [Common](#common)
  - [Player](#player)
  - [Blocks](#blocks)
  - [Mobs](#mobs)
  - [Agent](#agent)
  - [Gameplay](#gameplay)
  - [Position](#position)
- [Classes](#classes)
- [Enums](#enums)
- [Types](#types)
- [Other](#other)
  - [Inventory Slot Layout](#inventory-slot-layout)
    
# Functions

## Common



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
- WALK (1) - Walking normally (default if on ground)
- SWIM_WATER (2) - Swimming in water
- FALL (3) - In the air when not flying (Falling up or down)
- CLIMB (4) - Climbing a ladder
- SWIM_LAVA (5) - Swimming in lava
- FLY (6) - Flying
- RIDING (7) - Riding anything
- SNEAK (8) - Sneaking
- SPRINT (9) - Sprinting
- BOUNCE (10) - bounce
- FROST_WALK (11) - Frost walk over water
- TELEPORT (12) - Teleport
- UNKNOWN (-1) - Unknown travel method

### FillOperation
Fill options for exixting blocks. Control keeping, replacing, or destroying existing blocks
- DESTROY - Replaces all blocks (including air) in the fill region with the specified block, dropping the existing blocks (including those that are unchanged) and block contents as entities as if they had been mined with an unenchanted diamond shovel or pickaxe. (Blocks that can only be mined with shears, such as vines, will not drop; neither will liquids.)
- HOLLOW - Replaces only blocks on the outer edge of the fill region with the specified block. Inner blocks are changed to air, dropping their contents as entities but not themselves. If the fill region has no inner blocks (because it is smaller than three blocks in at least one dimension), acts like replace.
- KEEP - Replaces only air blocks in the fill region with the specified block.
- OUTLINE - Replaces only blocks on the outer edge of the fill region with the specified block. Inner blocks are not affected. If the fill region has no inner blocks (because it is smaller than three blocks in at least one dimension), acts like replace.
- REPLACE - Replaces all blocks (including air) in the fill region with the specified block, without dropping blocks or block contents as entities.

### CompassDirection
- WEST
- EAST
- NORTH
- SOUTH

### TurnDirection
- LEFT
- RIGHT

### SixDirection
- FORWARD 
- BACK 
- LEFT 
- RIGHT 
- UP 
- DOWN

### LeverPosition
Positions for aligning a lever when on or off
- BLOCK_BOTTOM_EAST_WHEN_OFF
- BLOCK_BOTTOM_POINTS_SOUTH_WHEN_OFF
- BLOCK_TOP_POINTS_EAST_WHEN_OFF
- BLOCK_TOP_POINTS_SOUTH_WHEN_OFF
- BLOCK_SIDE_FACING_EAST
- BLOCK_SIDE_FACING_WEST
- BLOCK_SIDE_FACING_NORTH
- BLOCK_SIDE_FACING_SOUTH

### ComparatorMode
Comparator modes
- COMPARE
- SUBTRACT

### TestForBlocksMask
- ALL - Every block in the source and destination regions must match exactly.
- MASKED - Air blocks in the source region will match any block in the destination region.

### CloneMode
- FORCE - The cloned region is overwritten by the destination region if the two regions overlap.
- MOVE - the cloned region is replaced with air after the cloning.
- NORMAL - The cloned region is not changed; if the destination region overlaps it, then the clone operation does nothing.

### MonsterMob
Lists all mobs that are considered monsters.

### TargetSelectorKind
- ALL_ENTITIES - Select all players and mobs.
- ALL_PLAYERS - Select all players in the world.
- LOCAL_PLAYER - Select the current player (you).
- MY_AGENT - Select the agent.
- NEAREST_PLAYER - Select the player nearest to the world origin.
- RANDOM_PLAYER - Select a random player in the world.

### GameMode
- SURVIVAL - This is the default Minecraft playing mode. Players have to gather the materials they want to craft or place. The player’s health, hunger, experience and oxygen are enabled. Tools and equipment durability is enabled. In this mode, the player can die and will return to the spawn point if they do.
- CREATIVE - Players can get an unlimited amount of blocks or items in the game. Players can fly around in the world and destroy blocks instantly. This mode is meant for players that want to spend time building things.
- ADVENTURE - Kind of the same as survival mode, but it has more restrictions on placing certain blocks and destroying blocks in the game world. This mode is meant for playing in worlds where the players must solve puzzles or complete challenges.

### AgentAssist
- PLACE_ON_MOVE - the agent will place a block from its active inventory slot every time it moves.
- PLACE_FROM_ANY_SLOT - if there are no blocks or items in the agent’s active inventory slot, the agent will try to use other inventory slots. 
- DESTROY_OBSTACLES - if the agent can’t move because of an obstacle, it will destroy the obstacle before moving.
- DETROY_OBSTACLES - seems to be a typo left in the code, functions the same was as `DESTROY_OBSTACLES`.

### AgentDetection
- BLOCK - detect any block that can be destroyed.
- REDSTONE - detect redstone only.

### Weather
- CLEAR - sunny, no rain or storms
- RAIN - rainy, no sun
- THUNDER - thunderstorm, lot’s of rain

### DayTime
- DAY (0) - Equals 1,000 ticks (7:00 AM)
- MIDDAY (6000) - Equals 6,000 ticks (12:00 PM)
- DUSK (12000) - Equals 12,000 ticks (6:00 PM)
- NIGHT (14000) - Equals 13,000 ticks (7:00 PM)
- MIDNIGHT (18000) - Equals to 18,000 ticks (12:00 AM)
- DAWN (23000) - Equals 0 ticks (6:00 AM)

### GameDifficulty
- PEACEFUL - monsters cannot spawn and you get more hearts quickly.
- EASY - easy gameplay level.
- NORMAL - normal gameplay level.
- HARD - the really difficult gameplay level.

### TimeQuery
- DAY - the number of game days since the creation of the world
- DAY_TIME - the current time of day in the game.
- GAME_TIME - the number of game ticks since the creation of the world.
- REAL_LIFE - the real-life time of day, expressed in Minecraft game ticks.

### GameRule

*For some reason some of these are differ between the docs and the code editor autocomplete suggestions. Some of these seem like different names for the same thing, but I haven't tested to see if it's so.*
- *(D) - present only in the docs.*
- *(E) - present only in the code editor.*
- *(DE) - present in both the docs and the editor.*

**Rules:**
    
- PV_P *(DE)* - players can attack each other 
- DROWNING_DAMAGE *(DE)* - staying for too long under water will damage the player 
- FALL_DAMAGE *(DE)* - falling from really high will damage the player
- FIRE_DAMAGE *(DE)* - fire will damage the player 
- DAYLIGHT_CYCLE *(DE)* - time will advance in the game 
- MOB_LOOT *(DE)* - mobs will drop loot upon dying 
- MOB_SPAWNING *(DE)* - mobs are able to spawn 
- MOB_GRIEFING *(DE)* - mobs can affect the game world (for example, endermen picking up blocks, or creepers exploding the environment) 
- WEATHER_CYCLE *(DE)* - weather will change naturally 
- BLOCK_DROPS *(D)* - blocks that are successfully mined will drop as an item and be collectible by players 
- KEEP_INVENTORY *(DE)* - players will not lose their inventory upon dying
- COMMAND_BLOCK_OUTPUT *(E)*
- DO_FIRE_TICK *(E)*
- NATURAL_REGENERATION *(E)*
- TILE_DROPS *(E)*
- ENTITY_DROPS *(E)*
- SHOW_COORDINATES *(E)*
- TNT_EXPLODES *(E)*

Axis
TODO

---

# Other

## Inventory Slot Layout
```
| 01 | 02 | 03 | 04 | 05 | 06 | 07 | 08 | 09 |
|----|----|----|----|----|----|----|----|----|
| 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 |
|----|----|----|----|----|----|----|----|----|
| 19 | 20 | 21 | 22 | 23 | 24 | 25 | 26 | 27 |
```
























