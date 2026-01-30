# Minecraft Logic Gates
Build 2D Logic Gate systems!

Features with a strikethrough are planned but not yet fully implemented.

## Starting Out
To start creating logic gate systems, first run `/function mclg:spawn_ui` in chat. 
Run `/function mclg:give_wrench` to get the wrench item.
Run `/function mclg:give_runtime_manager` to get the runtime manager item.

To place a single element, right click anywhere in the UI while not spriting.
To remove a single element, left click anywhere in the UI while not sprinting.

To fill an area with elements, right click anywhere in the UI while spriting. This will allow you to set the two corners to fill. Once you've selected your two corners, right click while sprinting one more time to confirm and place.
- Already placed elements take priority over newly filled elements.

To remove an area of elements, left click anywhere in the UI while sprinting. Unlike filling elements, there are special modes when removing elements:
- Having both an empty offhand and mainhand removes all elements.
- Having a filled offhand and an empty mainhand will filter out elements that do not match the specific one in your offhand.
- Having a filled offhand and mainhand will replace elements that match the one in your offhand with the one in your mainhand.

## Building circuits
While you can place *any* block inside the UI, certain blocks have special functions:

### Lighting / End Rods
Carries bits in one direction.

### Cut Copper / Quartz stairs
Changes the direction the bit travles in.

### Copper Bulbs
Allows wires to perpendicularly cross over eachother.

### Copper Grates
Splits a wire into at most 3 directions.

### Redstone Lamp
Holds a bit in a state of on or off. When placed as an output, delays propagation by 1 cycle.

## Target block
Just like redstone lanterns, but they don't have a display.

### Sea Lantern
This acts as a block for all gate types, and a select few circuits. By default, there are 6 two-input gate types (AND, NAND, NOR, OR, XOR, XNOR) and 1 one-input gate type (NOT). I tried my best to add support for sequential curcuits, but no guarantees.

## Saving Circuits to be reused for later
You can use shulkers boxes to save an area of element positions and data relative to a point. To do this, simply right click two points while not sprinting with a shulker box in your mainhand. This will give you a number of shulker boxes.
 - If the selected area contains > 999 ui elements, a new shulker box will be created. For some reason, you can only store so much data before it the player gets kicked from the world, causing a softlock.
 - Shulker boxes that are a part of the same circuit are linked by cicruit IDs inside custom data. Placing one will place the full circuit.

## Creating truth tables
You can create truth tables of circuits to be reused for later with the runtime manager. To do this, you have to:
 - Set the starting inputs using the runtime manager.
 - Set the outputs using the runtime manager.
 - Select the area you want to use for the truth table.
This creates the truth table.
To reuse the truth table, first, give it a name by running `/function mclg:name_truth_table (name:"<name>")`. After this, it's stored with that name, and you can assign it by running `/functoin mclg:assign_truth_table (name:"<name>")`.
When assigning, it will prompt you to select your defined inputs and outputs, starting at input 0. Both inputs and outputs ordered from closest to the first point when selecting the area to the farthest.

## Running Circuits
Once you've linked your inputs and outputs, you can run them. 
On your initial starting bits (typically lanterns), run `/function mclg:toggle_starter`. ~~You can also do this in bulk with `execute as <target entities> run function mclg:toggle_starters`~~. 
Then, you can use either use the command `/function mclg:id_flood` to run the circuit.

## Settings
There are a number of settings accessible within the pause menu.

## Installation
### Datapack
First, install [Bookshelf View](https://modrinth.com/datapack/bookshelf-view/version/3.1.1). Then, navigate to releases and download the datapack.zip file you want. Lastly, open your minecraft saves folder, find your world, open the datapacks folder, and copy paste both datapacks inside.

### Building
Download python 3.11+ alongside pip and run `pip install git+https://github.com/WingedSeal/jmc.git#subdirectory=src` to install jmc. Inside the root folder, open a command prompt and simply run `jmc compile`, and the datapack will output to src/build.
