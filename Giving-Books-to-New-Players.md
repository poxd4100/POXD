Patchouli does not have native functionality to give books to players as they join. However, this functionality is easily replicated using vanilla advancements.

What we will do is to provide a hidden advancement that triggers for a player immediately (their first tick after logging in). The reward for this advancement will be the book. 

Please check the [vanilla wiki](https://minecraft.fandom.com/wiki/Advancement/JSON_format) for details.

Below is a brief example:

`/data/yourdomain/advancements/grant_book_on_first_join.json`:
```

  "criteria": {
    "tick": {
      "trigger": "minecraft:tick"
    }
  },
  "rewards": {
    "loot": [
      "yourdomain:grant_book_on_first_join"
    ]
  }
}
```

`/data/yourdomain/loot_tables/grant_book_on_first_join.json`:
```
{
  "type": "advancement_reward",
  "pools": [
    {
      "rolls": 1,
      "entries": [
        {
          "type": "item",
          "name": "patchouli:guide_book",
          "functions": [
            {
              "function": "set_nbt",
              "tag": "{\"patchouli:book\": \"YOURBOOKIDHERE\"}"
            }
          ]
        }
      ]
    }
  ]
}
```
Fill in your book ID where it says to. Modders: if you have a custom book item, obviously replace the item id and delete the function.