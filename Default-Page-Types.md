This page specifies the various page types provided by default in Patchouli. If you need other page types for whatever case, please see [Using Templates](https://github.com/Vazkii/Patchouli/wiki/Using-Templates) for information on creating your own.

These pages should be used in Entries, in the "pages" array, via specifying which type you want by using "type" on each object. You can read more in [Entry JSON Format](https://github.com/Vazkii/Patchouli/wiki/Entry-JSON-Format).

The following attributes are common to every page type:

* **type** (String, _mandatory_)

What type this page is. This isn't used by the page itself, but rather by the loader to determine what page should be loaded. For example, if you want a text page, you set this to "text".

* **advancement** (String)

A resource location to point at, to make a page appear when that advancement is completed. See [Locking Content with Advancements](https://github.com/Vazkii/Patchouli/wiki/Locking-Content-with-Advancements) for more info on locking content. Excluding this attribute or leaving it empty will leave the page unlocked from the start. Providing a nonexistent advancement will permanently lock this entry unless the advancement at the resource location starts existing.

* **flag** (String)

A config flag expression that determines whether this page should exist or not. See [Using Config Flags](https://github.com/Vazkii/Patchouli/wiki/Using-Config-Flags) for more info on config flags.

## Example Usage

Here's an example of using a text page:

```json
{
    "type": "text",
    "text": "This is an example"
}
```  

## Text Pages
![](https://i.imgur.com/cYGwnxb.png)  
Page type: **"text"**

**Text pages should always be the first page in any entry**. If a text page is the first page in an entry, it'll display the header you see in the left page. For all other pages, it'll display as you can see in the right one.

**Attributes**:
* **text** (String, _mandatory_)

The text to display on this page. This text can be [formatted](https://github.com/Vazkii/Patchouli/wiki/Text-Formatting-101).

* **title** (String)

An optional title to display at the top of the page. If you set this, the rest of the text will be shifted down a bit. You can't use "title" in the first page of an entry.

## Image Pages
![](https://i.imgur.com/NnWb10b.png)  
Page type: **"image"**

**Attibutes**:
* **images** (String Array, _mandatory_)

An array with images to display. Images should be in resource location format and suffixed with ".png". Images used here should ideally be dimensioned as 256x256, and use only a 200x200 canvas centered in the top-left corner for contents, which are rendered at a 0.5x scale compared to the rest of the book in pixel size.

If there's more than one image in this array, arrow buttons are shown like in the picture, allowing the viewer to switch between images. If there's only one image, they're not.

* **title** (String)

The title of the page, shown above the image.

* **border** (boolean)

Defaults to false. Set to true if you want the image to be bordered, like in the picture. It's suggested that border is set to true for images that use the entire canvas, whereas images that don't touch the corners shouldn't have it.

* **text** (String)

The text to display on this page, under the image. This text can be [formatted](https://github.com/Vazkii/Patchouli/wiki/Text-Formatting-101).

## Crafting Recipe Pages

![](https://i.imgur.com/ySSi5zL.png)  
Page type: **"crafting"**

**Attibutes**:
* **recipe** (String, _mandatory_)

The ID of the first recipe you want to show.

* **recipe2** (String)

The ID of the second recipe you want to show. Displaying two recipes is optional.

* **title** (String)

The title of the page, to be displayed above both recipes. This is optional, but if you include it, only this title will be displayed, rather than the names of both recipe output items.

* **text** (String)

The text to display on this page, under the recipes. This text can be [formatted](https://github.com/Vazkii/Patchouli/wiki/Text-Formatting-101).

Note: the text will not display if there are two recipes with two different outputs, and "title" is not set. This is the case of the image displayed, in which both recipes have the output names displayed, and there's no space for text.

## Smelting Recipe Pages

![](https://i.imgur.com/noBfGCc.png)  
Page type: **"smelting"**

**Attibutes**:
* **recipe** (String, _mandatory_)

The first recipe you want to show. Given that furnace recipes are only named properly as of 1.13, instead of using a recipe ID, we use an [ItemStack String](https://github.com/Vazkii/Patchouli/wiki/ItemStack-String-Format) that corresponds to the item being smelted, so if you wanted to show the recipe for smelting sand to glass, you'd use "minecraft:sand" here.

* **recipe2** (String)

The second recipe you want to show. See "recipe" above for format. Displaying two recipes is optional.

* **title** (String)

The title of the page, to be displayed above both recipes. This is optional, but if you include it, only this title will be displayed, rather than the names of both recipe output items.

* **text** (String)

The text to display on this page, under the recipes. This text can be [formatted](https://github.com/Vazkii/Patchouli/wiki/Text-Formatting-101).

## Multiblock Pages

![](https://i.imgur.com/uTt7Zsc.png)  
Page type: **"multiblock"**

* **name** (String, _mandatory_)

The name of the multiblock you're displaying. Shows as a header above the multiblock display.

* **multiblock_id** (String)

For modders only. The ID of the multiblock you want to display. See [API Usage](https://github.com/Vazkii/Patchouli/wiki/API-Usage) for how to create and register Multiblocks in code.

_Note: Either this or "multiblock" need to be set for this page type to work._

* **multiblock** (Object)

The multiblock object to display. See [Using Multiblocks](https://github.com/Vazkii/Patchouli/wiki/Using-Multiblocks) for how to create this object.

_Note: Either this or "multiblock_id" need to be set for this page type to work._

* **enable_visualize** (boolean)

Defaults to true. Set this to false to disable the "Visualize" button.

* **text** (String)

The text to display on this page, under the multiblock. This text can be [formatted](https://github.com/Vazkii/Patchouli/wiki/Text-Formatting-101).

## Entity Pages

TODO

## Spotlight Pages

TODO

## Link Pages

TODO

## Relations Pages

TODO

## Empty Pages

TODO