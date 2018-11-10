This page specifies the various template components provided by Patchouli. These components should be used in Templates, in the "components" array, via specifying which type you want by using "type" on each object. You can read more in [Using Templates](https://github.com/Vazkii/Patchouli/wiki/Using-Templates).

The following attributes are common to every component type:

* **type** (String, _mandatory_)

What type this component is. This isn't used by the component itself, but rather by the loader to determine what component should be loaded. For example, if you want a text component, you set this to "text".

* **x** (integer)

Defaults to 0. The horizontal position of this component in the page.

* **y** (integer)

Defaults to 0. The vertical position of this component in the page.

* **advancement** (String)

A resource location to point at, to make a component appear when that advancement is completed. See [Locking Content with Advancements](https://github.com/Vazkii/Patchouli/wiki/Locking-Content-with-Advancements) for more info on locking content. Excluding this attribute or leaving it empty will make the component always display.

* **negate_advancement** (boolean)

Defaults to false. If set to true, the *advancement* field will be negated, making the component only show if the advancement hasn't been gotten yet.

* **flag** (String)

A config flag expression that determines whether this component should show or not. See [Using Config Flags](https://github.com/Vazkii/Patchouli/wiki/Using-Config-Flags) for more info on config flags.

## Example Usage

Here's an example of using a text component:

```json
{
    "type": "text",
    "text": "This is an example",
    "x": 20,
    "y": 30
}
```  

## Text Components
Component type: **"text"**  
Draws a text block, which supports [formatting](https://github.com/Vazkii/Patchouli/wiki/Text-Formatting-101).

**Attributes:**
* **text** (String, _mandatory_)

The text to display: Can be a variable.

* **color** (String)

The default color of the text, in hex (e.g. "FF0000" would be pure red). If not set it defaults to the book's text color. Can be a variable.

* **max_width** (integer)

The maximum width allowed for a line in this block. If not set, it defaults to the full width of a page.

* **line_height** (integer)

The height of each line. The default is 9, which is what patchouli uses everywhere else. If you set this to more than that, there will be space between the text lines. If you set it to less, the lines will overlap and look bad.

## Item Components
Component type: **"item"**  
Draws an item, which you can hover over to see its tooltip, or click to open the page that shows how to craft it, if there's one.

**Attributes:**

* **item** (String, _mandatory_)

An [ItemStack String](https://github.com/Vazkii/Patchouli/wiki/ItemStack-String-Format) representing the item you want to show. Can be a variable.

* **framed** (boolean)

Defaults to false. If true, it'll draw a small frame around the item in the same way that the recipe pages does for the output.

* **link_recipe** (boolean)

Defaults to false. Set this to true to mark any page this component is used in as the "recipe page" for the item being shown. If you do so, when looking at pages that display the item, you can shift-click the item to be taken to the page that uses this component.

## Image Components
Component type: **"image"**  
Draws an image, or part of it.

**Warning**: Using images whose width and height aren't powers of two (16, 32, 64, 128, 256, 1024...) will cause things to break. Do not do it.

**Attributes:**

* **image** (String, _mandatory)

A resource location pointing to the image you want to draw. Can be a variable.

* **width** (integer, _mandatory_)

The width of the area that you want to draw from your image. This starts counting from the left.

* **height** (integer, _mandatory_)

The width of the area that you want to draw from your image. This starts counting from the top.

* **u** (integer)

How many pixels from the left of the image you want to start drawing the image. If you don't set this, it'll default to 0, and start drawing at the very left.

* **v** (integer)

How many pixels from the top of the image you want to start drawing the image. If you don't set this, it'll default to 0, and start drawing at the very top.

* **texture_width** (integer)

The width of the image you want to draw. If you don't set this it'll default to 256. If your image's width is different from 256, you need to set the value, or it'll look weird.

* **texture_height** (integer)

The height of the image you want to draw. If you don't set this it'll default to 256. If your image's height is different from 256, you need to set the value, or it'll look weird.

* **scale** (float)

The scale at which you want to display this image. Defaults to 1.