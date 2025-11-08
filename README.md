# Minecraft Logic Gates
Build 2D Logic Gate systems!

Features with a strikethrough are planned but not yet fully implemented.

## Starting Out
To start creating logic gate systems, first run `/function mclg:spawn_ui` in chat. 

To place a single element, right click anywhere in the UI while not spriting.
To remove a single element, left click anywhere in the UI while not sprinting.

To fill an area with elements, right click anywhere in the UI while spriting. This will allow you to set the two corners to fill. Once you've selected your two corners, right click while sprinting one more time to confirm and place.
- Already placed elements take priority over newly filled elements.

To remove an area of elements, left click anywhere in the UI while sprinting. Unlike filling elements, there are special modes when removing elements:
- Having both an empty offhand and mainhand removes all elements.
- Having a filled offhand and an empty mainhand will filter out elements that do not match the specific one in your offhand.
- Having a filled offhand and mainhand will replace elements that match the one in your offhand with the one in your mainhand.

## Building circuits
While you *can* place any element inside the UI, certain elements have special functions:

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

### Sea Lantern
This acts as a block for all gate types, and a select few circuits. By default, there are 6 two-input gate types (AND, NAND, NOR, OR, XOR, XNOR) and 1 one-input gate type (NOT). Since sequential circuits aren't supported, ~~T flip flops, D flip flops, and JK flip flops are also included~~.

## Saving Circuits
You can use shulkers boxes to save an area of element positions and data relative to a point. To do this, simply right click two points while not sprinting with a shulker box in your mainhand. This will give you a number of shulker boxes.
 - If the selected area contains > 999 ui elements, a new shulker box will be created. This is due to player packet limitations.
 - Shulker boxes that are a part of the same circuit are linked by cicruit IDs inside custom data. Placing one will place the full circuit.
 - There are a number of pre-added circuits. Simply do `/function mclg:give` to get a selection of circuits. Alternatively, you can run `/function mclg:give_all` to get every one.

## Running Circuits
Once you've linked your inputs and outputs, you can run them. 
On your initial starting bits (typically lanterns), run `/function mclg:toggle_starter`. ~~You can also do this in bulk with `execute as <target entities> run function mclg:toggle_starters`~~. 
Then, you can use either use the command `/function mclg:id_flood` to do one quick but slower run, ~~or compile them with `/function mclg:compile`, then run `/function mclg:storage_flood` for a faster but less variable version.~~
  - If you compile it, any modifications require recompiling before running again.

## Settings
There are a number of settings accessible within the pause menu.

## Installation
### Datapack
First, install [Bookshelf View](https://modrinth.com/datapack/bookshelf-view/version/3.1.1). Then, navigate to releases and download the datapack.zip file you want. Lastly, open your minecraft saves folder, find your world, open the datapacks folder, and copy paste both datapacks inside.

### Building
Download python 3.11+ alongside pip and run `pip install git+https://github.com/WingedSeal/jmc.git#subdirectory=src` to install jmc. Inside the root folder, open a command prompt and simply run `jmc compile`, and the datapack will output to src/build.
