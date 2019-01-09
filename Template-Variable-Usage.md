As explained in [Using Templates](https://github.com/Vazkii/Patchouli/wiki/Using-Templates), variables can be used to pass data in from the entry files into the template render.

If you're not familiar with templates or using variables therein, please read the Using Templates page first, as thus page describes more complex use cases. Note that this page applies only to template design, and not in passing the variables in from the entry json.

## Inline Variables

Variables can be inlined into any strings in the template. You do this by wrapping the variable name in #, as follows:
```
{
	"type": "text",
	"text": "String interpolation with #inline_text# in the middle of the string!",
	"x": 20,
	"y": 30
} 
```

Should you then define the variable "inline_text" in your entry json as such:

```
	"inline_text": "anything you want"
```

The text block you would see displayed ingame would be _"String interpolation with anything you want in the middle of the string!"_.

## String Derivation

Variables can have other data derived from them. For example, a variable you'd fill with an [ItemStack String](https://github.com/Vazkii/Patchouli/wiki/ItemStack-String-Format) can be 