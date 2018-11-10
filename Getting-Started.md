This entry serves as a quick guide of what to do to get started making your own Patchouli books, read on and follow carefully!

### 0. Install Patchouli
Pretty obvious. For modders, you can load it as a lib to your mod project or just drop it in your workspace's mods folder.

### 1. Locate your patchouli_books directory
Your books and their contents will go in your patchouli_books directory, so you need to find it.
* For modpack makers, it'll be in your instance folder (next to mods, config, etc). Note that you need to run the game with patchouli installed for it to show up (or just make it yourself).
* For modders, it'll be /assets/_YOURMODID_/patchouli_books, you'll have to make it yourself.

### 2. Create your folder structure
Once you found patchouli_books, decide on a name for your book. Only lower case characters and underscores are allowed. This is purely an internal name so feel free to call it whatever you want, or just "book" if you're lazy, nobody's gonna mind. After you have a name, create folders and files inside patchouli_books so that it looks like this:

* patchouli_books
    * _YOURBOOKNAME_ (folder)
        * book.json (empty file)
        * en_us (folder)
            * entries (empty folder)
            * categories (empty folder)
            * templates (empty folder)

You may have as many books as you want, even within the same mod(pack). Naturally each one should have a different ID. For ID'ing purposes ingame, each book is assigned an id in the form of "_YOURMODID:YOURBOOKID_", or "patchouli:_YOURBOOKID_" if you're loading them as a modpack maker.

Note that creating an "en_us" folder means you're creating the "english" version of your book. The contents you put in the "en_us" folder are always the "main" ones loaded, so even if your book isn't meant to be natively in english, you need to put your main stuff there.

Any translators may create folders with their languages and override any files they wish. They're automatically loaded if the game language is changed. For translators: Please don't include in your folder anything you aren't overriding.

### 3. Populate book.json
Open up your book.json using your favorite text editor, and fill it in as follows:

```json
{
	"name": "BOOK NAME",
	"landing_text": "LANDING TEXT",
	"version": 1
}
```

where "BOOK NAME" is the name your book will be displayed as, and "LANDING TEXT" the text that will show up on the left page of your book ingame. The version field specifies which edition your book is. Whenever you update your book, you should also update the edition value. For modders, you can use localization keys in both name and landing_text.

See:  

![](https://i.imgur.com/lsdDrrk.png)

For more customization options, please read [Book JSON Format](https://github.com/Vazkii/Patchouli/wiki/Book-JSON-Format). (highly recommended!)

### 4. Check ingame
Load your game and check if your book is there. Unless you specified otherwise, it should be in the Miscellaneous creative tab, but you can also search for it. 

If you don't see it, check if patchouli is properly loaded and if there's any errors in your log. 

Everything after this can be hot loaded without closing the game, so feel free to keep it open as you do further edits.

### 5. Add Stub Content
Time to add some content to your book. Go to your book's folder and then en_us, and create folders and files so that it looks like this:

* en_us
    * entries (folder)
        * test (folder)
            * test_entry.json (empty file)
    * categories (folder)
        * test_category.json (empty file)
    * templates (empty folder)

Open test_entry.json and test_category.json and fill them in as follows:

**test_entry.json**:
```json
{
    "name": "Test Entry",
    "icon": "minecraft:writable_book",
    "category": "test_category",
    "pages": [
        {
            "type": "text",
            "text": "This is a test entry, but it should show up!"
        }
    ]
}
```

**test_category.json**
```json
{
	"name": "Test Category",
	"description": "This is a test category for testing!",
	"icon": "minecraft:writable_book"
}
```

Save your files, then return ingame and open your book. Shift-click the pencil in the bottom-left corner. When you do so, it will reload the book contents, and you should see the category and entry you just defined appear.

### 6. Learn More!

You're done getting set up, now it's time to learn more about what you can do with Patchouli's book system. Check the following pages out:

* [Locking Content with Advancements](https://github.com/Vazkii/Patchouli/wiki/Locking-Content-with-Advancements)
* [Text Formatting 101](https://github.com/Vazkii/Patchouli/wiki/Text-Formatting-101)
* [Book JSON Format](https://github.com/Vazkii/Patchouli/wiki/Book-JSON-Format)
* [Category JSON Format](https://github.com/Vazkii/Patchouli/wiki/Category-JSON-Format)
* [Entry JSON Format](https://github.com/Vazkii/Patchouli/wiki/Entry-JSON-Format)
    * [Default Page Types](https://github.com/Vazkii/Patchouli/wiki/Default-Page-Types)
* [Using Templates](https://github.com/Vazkii/Patchouli/wiki/Using-Templates)

Lastly, here's a few pointers you should take in mind.

* The patchouli book item's ID is "patchouli:item", the NBT tag for a specific book is `{"patchouli:book": "BOOKMOD:BOOKID"}`
    * For example, a book in /assets/yourmod/patchouli_books/coolbook would be `{"patchouli:book": "yourmod:coolbook"}`
    * Books loaded from the patchouli_books folder in your instance folder have "patchouli" as the mod ID
    * If you need a CraftTweker script, grab your book and do `/mt hand`
* For modpack makers, if you want to use your own images, textures, sounds, or other assets, you'll need a tool to load them in, such as [Resource Loader](https://minecraft.curseforge.com/projects/resource-loader).
* You need to reload the game to load new book.json files, but not the book contents.
* Book contents are purely client sided, whereas book.json files are loaded by the server too.
* You don't have to put your entries in folders corresponding to the categories they belong in, but it helps with organization!
* No dependencies are needed if you're a modder, not even any code. Patchouli automatically finds your files in your assets if you put them in the right place.
