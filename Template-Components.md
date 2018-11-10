This page specifies the various template components by Patchouli. These pages should be used in Templates, in the "components" array, via specifying which type you want by using "type" on each object. You can read more in [Using Templates](https://github.com/Vazkii/Patchouli/wiki/Using-Templates).

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