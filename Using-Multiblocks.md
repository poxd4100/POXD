Patchouli comes with a system that allows you to define multiblocks and then visualize them in the world. These multiblocks can be either defined in code by modders (using the API), or defined in JSON inline with the entry data.

This page is written like a tutorial to get you to understand how multiblock objects work, as writing the object structure formally wouldn't properly convey how to construct it.

The page focuses on creating multiblocks using JSON, but the fundamentals also apply to doing so using code. Making multiblocks with code allows you to create state matchers using arbitrary predicates and using the multiblock for server-side validation and placement (if you allow Patchouli as a required mod). You can look into the [Patchouli API](https://github.com/Vazkii/Patchouli/tree/master/src/main/java/vazkii/patchouli/api) for how to do this, or see an example of it being done [here](https://github.com/Vazkii/Patchouli/blob/master/src/main/java/vazkii/patchouli/common/multiblock/MultiblockRegistry.java).

## Multiblock Format

A Multiblock is composed of a 2 dimensional String Array (the pattern), and a mapping of characters present in the pattern to state matchers.

As a demonstration of how to create a multiblock, we'll be using the following... thing as a demonstration:

![](https://i.imgur.com/s7hMVe8.png)

A multiblock can be defined using a JSON object. Let's begin with an empty one and add in as we go.

```
"multiblock": {

}
```

### The Mapping

We'll begin by discussing which types of blocks we have here. Looking at the pic we have:

* Gold Blocks
* Red Terracotta
* Gray Wool (which for this demo we want to allow it to be any color)
* Air
* A few corners we can't see, but let's say they're allowed to be any block

Once we know what types of blocks this structure uses, we assign a letter to each:

* **G**: Gold Blocks
* **R**: Red Terracotta
* **W**: Any Wool

Patchouli already provides built in characters for Air and (Any Block), which are respectively a space, and an underscore, so we don't have to account for those.

Now, we need to convert these to data the game can understand. There's two cases in here you'll have to think about. Just matching against the block type, or matching a block with a particular state. In this case, Red Terracotta is the same  block as Blue Terracotta, so we need to account for that.

We then define our mapping using internal IDs and appending block state values in square brackets after if needed. If multiple block state values are needed we just separate them with a comma, but that won't be needed here. Any states you don't want to match against, you simply don't include. Therefore, we have:

* **G**: minecraft:gold_block
* **R**: minecraft:stained_hardened_clay[color=red]
* **W**: minecraft:wool

Looks good. Let's put these mappings into our json using a "mapping" block:
```
"multiblock": {
    "mapping": {
         "G": "minecraft:gold_block",
         "R": "minecraft:stained_hardened_clay[color=red]",
         "W": "minecraft:wool"
     }
}
```