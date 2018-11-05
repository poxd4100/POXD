This page details every key you can have in a book.json file.

* **name** (String, _mandatory_)   
The name of the book that will be displayed in the book item and the GUI. For modders, this can be a localization key.

* **landing_text** (String, _mandatory_)  
The text that will be displayed in the landing page of your book. This text can be [formatted](https://github.com/Vazkii/Patchouli/wiki/Text-Formatting-101). For modders, this can be a localization key.

* **book_texture** (String)  
The texture for the background of the book GUI. You can use any resource location for this, but it is *highly recommended* you use one of the built in ones so that if new elements get added, you have them right away. The ones that Patchouli comes with are the following:
    * patchouli:textures/gui/book_blue.png
    * patchouli:textures/gui/book_brown.png (default value)
    * patchouli:textures/gui/book_cyan.png
    * patchouli:textures/gui/book_gray.png
    * patchouli:textures/gui/book_green.png
    * patchouli:textures/gui/book_purple.png
    * patchouli:textures/gui/book_red.png  

In the advent you want to use a custom one, you can copy any of these and make any modifications you need.

* **filler_texture** (String)  
The texture for the page filler (the cube thing that shows up on entries with an odd number of pages). Define if you want something else than the cube to fill your empty pages.

* **crafting_texture** (String)  
The texture for the crafting entry elements. Define if you want custom backdrops for these. Not really worth defining in most cases but if you want to be cool and stylish, you can.

* **model** (String)  
The model for the book's item. This can be any standard item model you define. Patchouli provides a few you can use:
    * patchouli:book_blue
    * patchouli:book_brown (default value)
    * patchouli:book_cyan
    * patchouli:book_gray
    * patchouli:book_green
    * patchouli:book_purple
    * patchouli:book_red

FOR MODDERS: Do NOT use any of the above models. In the sake of books being distinguishable, having multiple mods using the same base textures is a bad idea, make your own! They're provided for modpack makers. Patchouli automatically takes care of registering any models you pass in to this, so you don't have to mess with any code for them yourself.

A property called "_completion_" is provided for book models, where its value is equal to the fraction of entries unlocked in the book, which allows book models to change their display as they're more completed.

* **text_color** (String)  
The color of regular text, in hex ("RRGGBB", # not necessary). Defaults to "000000".

* **header_color** (String)  
The color of header text, in hex ("RRGGBB", # not necessary). Defaults to "333333".

* **nameplate_color** (String)  
The color of the book nameplate in the landing page, in hex ("RRGGBB", # not necessary). Defaults to "FFDD00".

* **link_color** (String)  
The color of link text, in hex ("RRGGBB", # not necessary). Defaults to "0000EE".

* **link_hover_color** (String)
The color of hovered link text, in hex ("RRGGBB", # not necessary). Defaults to "8800EE".

TODO complete
