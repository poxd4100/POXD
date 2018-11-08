Entries in your Patchouli books can be locked until certain Advancements are accomplished. This page will give you a quick primer on how to accomplish this.

* First things first, create your advancement. If you're a modder, make it as you usually would ([Minecraft Wiki reference](https://minecraft.gamepedia.com/Advancements)), and place it in /assets/MODID/advancements. If you're a modpack maker, you'll need to create your advancements using the [Triumph](https://minecraft.curseforge.com/projects/triumph)mod.

* Once your advancement is done, grab its ID (which would be in the namespace:path format). For the sake of demonstration, we'll pretend the ID is "mymod:myadv".

* Open the .json file for the entry you want, and fill in the "advancement" field with the ID: `"advancement": "mymod:myadv"`. 
    * See [Entry JSON Format](https://github.com/Vazkii/Patchouli/wiki/Entry-JSON-Format) for more info.

* Open the book.json file for the book that contains the entry you just locked. 
    * If the the "advancement_namespaces" array isn't present yet, create it: `"advancement_namespaces": []`
    * Add the namespace to the "advancement_namespaces" array: `"advancement_namespaces": [ "mymod" ]`
    * Adding the namespace here tells patchouli that it needs to keep track of advancements in that namespace. You only have to do it once per namespace. If you have multiple books that use the namespace, only one needs it, but it's good practice to have it in all of them.
    * See [Book JSON Format](https://github.com/Vazkii/Patchouli/wiki/Book-JSON-Format) for more info.