# Minecraft Logic Gates
Build 2D Logic Gate systems!

## Starting Out
To start creating logic gate systems, first run `/function mclg:spawn_ui` in chat. 
- Customize UI size with the command `/scoreboard players set $uiSize __variable__ <int>`. Automatically sets it to the next multiple of 50.

To place a single block, right click anywhere in the UI while not spriting.
To remove a single block, left click anywhere in the UI while not sprinting.

To fill an area with blocks, right click anywhere in the UI while spriting. This will allow you to set the two corners to fill. Once you've selected your two corners, right click while sprinting one more time to confirm and place.
- Already placed blocks take priority over newly filled blocks.

To remove an area of blocks, left click anywhere in the UI while sprinting. Unlike filling blocks, there are special modes when removing blocks:
- Having both an empty offhand and mainhand removes all blocks.
- Having a filled offhand and an empty mainhand will filter out blocks that do not match the specific one in your offhand.
- Having a filled offhand and mainhand will replace blocks that match the one in your offhand with the one in your mainhand.

## Building circuits
While you *can* place any block inside the UI, certain blocks have special functions:

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
This acts as a block for all gate types, and a select few circuits. By default, there are 6 two-input gate types (AND, NAND, NOR, OR, XOR, XNOR) and 1 one-input gate type (NOT). Since sequential circuits aren't supported, there area also T flip flops, D flip flops, and JK flip flops.

## Saving Circuits
You can use shulkers boxes to save an area of element positions and data relative to a point. To do this, simply right click two points while not sprinting with a shulker box in your mainhand. This will give you a number of shulker boxes.
 - If the selected area contains > 999 ui elements, a new shulker box will be created. This is due to packet limitations.
 - Shulker boxes that are a part of the same circuit are linked by cicruit IDs inside custom data. Placing one will place the full circuit.
 - There are a number of pre-added circuits. Simply do `/function mclg:give` to get a selection of circuits. Alternatively, you can run `/function mclg:give_all` to get every one.

## Running Circuits
Once you've linked your inputs and outputs, you can run them. 
On your initial starting bits (latnerns), run `/function mclg:toggle_starter`. You can also do this in bulk with `execute as <target entities> run function mclg:toggle_starters`. 
Then, you can use either use the command `/function mclg:id_flood` to do one quick but slower run, or compile them with `/function mclg:compile`, then run `/function mclg:storage_flood` for a faster but less variable version.
  - If you compile it, any modifications require recompiling before running again.
  
## Installation
### Datapack
Navigate to releases and download the datapack.zip file. Then open your minecraft saves folder, find your world, open the datapacks folder, and copy paste the downloaded datapack.zip file.

### Building
Download python 3.11+ alongside pip and run `pip install git+https://github.com/WingedSeal/jmc.git#subdirectory=src` to install jmc. Inside the root folder, open a command prompt and simply run `jmc`. Then, run compile, and the datapack will output to src/build.
