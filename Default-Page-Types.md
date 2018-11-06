This page specifies the various page types provided by default in Patchouli. If you need other page types for whatever case, please see [Using Templates](https://github.com/Vazkii/Patchouli/wiki/Using-Templates) for information on creating your own.

These pages should be used in Entries, in the "pages" array, via specifying which type you want by using "type" on each object. You can read more in [Entry JSON Format](https://github.com/Vazkii/Patchouli/wiki/Entry-JSON-Format).

The following attributes are common to every page type:

* **type** (String, _mandatory_)

What type this page is. This isn't used by the page itself, but rather by the loader to determine what page should be loaded. For example, if you want a text page, you set this to "text".

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

## Image Pages
![](https://i.imgur.com/NnWb10b.png)  
Page type: **"image"**

**Attibutes**:
* **images** (String Array, _mandatory_)

An array with images to display. Images should be in resource location format and suffixed with ".png". Images used here should ideally be dimensioned as 256x256, and use only a 200x200 canvas centered in the top-left corner for contents, which are rendered at a 0.5x scale compared to the rest of the book in pixel size.

If there's more than one image in this array, arrow buttons are shown like in the picture, allowing the viewer to switch between images. If there's only one image, they're not.

For modpack makers, if you want to use your own images, you'll need another tool to load them in, such as [Resource Loader](https://minecraft.curseforge.com/projects/resource-loader).

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

The title of the page, to be displayed above both recipes. This is optional, but if you include it, only this title will be displayed, rather than the 

* **text** (String)

The text to display on this page, under the recipes. This text can be [formatted](https://github.com/Vazkii/Patchouli/wiki/Text-Formatting-101).

Note: the text will not display if there are two recipes with two different outputs, and "title" is not set. This is the case of the image displayed, in which both recipes have the output names displayed, and there's no space for text.