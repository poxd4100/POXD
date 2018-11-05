Across the book specification, you'll find objects that specify they can be "formatted". Patchouli comes with a text formatting system that allows you to write rich text using a few formatting codes. 

Formatting codes can be tested out in real time using the ingame editor (the pencil in the main page). Read on for what you can use.

## Default Formatting Codes

* **$()** - Clears any formatting currently applied
* **$(br)** - Adds a line break
* **$(br2)** - Adds two line breaks (or a new paragraph, if you will)
* **$(li)** - Makes a list element for a bullet point list
    * You can also use **$(li2)**, **$(li3)**, etc, for nested lists
* **$(#rrggbb)** - Hex code color (e.g. $(#ff0000) makes the text red) 
    * **$(#rgb)** is also allowed (e.g. $(#f00) also makes the text red)
* **$(0-f)** - Color code (e.g. $(6) makes the text gold color)
* **$(k/l/m/n/o)** - Formatting code (e.g. $(o) makes the text italic)
* **$(l:entryid)** - Internal Link, replace entryid with the id of an entry in your book and this will create a clickable link to it!
* **$(l:http://...)** - External Link, similar to previous, but when clicked, opens the website
* **$(/l)** - End Link, ends the current link but maintains formatting ($() also ends links)
* **$(playername)** - Inserts the name of the player

## Default Macros

A bunch of macros are provided by default. If you write what's on the left, it'll automatically alias to what's on the right.

* $(obf) -> $(k)
* $(bold) -> $(l)
* $(strike) -> $(m)
* $(italic) -> $(o)
* $(italics) -> $(o)
* $(list -> $(li 
    * _(the lack of closing parenthesis is intended to allow you to do $(list2), $(list3), etc)_
* $(reset) -> $()
* $(clear) -> $()
* $(2br) -> $(br2)
* $(p) -> $(br2)
* /$ -> $()
* \<br> -> $(br)
* $(nocolor) -> $(0)
* $(item) -> $(#b0b)
* $(thing) -> $(#490)

You are recommended to use $(item) and $(thing) as generic colors to highlight items and concepts, respectively.

## Custom Macros

Individual books are allowed to create their own macros. These macros will work for the book they're defined for only. Macros defined by books override the default ones, so you can rebind $(item) to some other color if you want to, for example.

To create custom macros, simply add a "macros" key to your book.json (see [Book JSON Format](https://github.com/Vazkii/Patchouli/wiki/Book-JSON-Format) for more info), and fill it in as follows:

```json
"macros": {
	"key1": "value1",
	"key2": "value2"
}
```
where key is what you want to replace, and value is what you want to replace it with. For example:

```json
"macros": {
	"$(potato)": "$(#F00)POTATO SALAD$()"
}
```
should you do this, whenever you write $(potato), it would replace it with "POTATO SALAD" in red text.

There's no restriction that the left side has to contain the standard $(...) format either, so you can also rewrite the formatting if you want, like as follows:

```json
"macros": {
	"<b>": "$(l)",
	"<i>": "$(o)",
	"</>": "$()"
}
```