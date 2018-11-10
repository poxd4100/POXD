In the purposes of allowing generalization and reusing of common elements, templates can be nested within other templates. This page explains you how to this.

To include templates in another template, you simply add an "include" array to your template .json file. Inside this array, you can specify as many "Template Inclusions" as you want. 

For obvious reasons, circular inclusions aren't allowed. This means if template A includes template B, template B can't include template A. If you do this, stuff is going to break.

## Template Inclusion Format

* **template** (String, _mandatory_)

The ID of the template you wish to include.

* **as** (String, _mandatory_)

The name that you want to reference this inclusion by. Each inclusion should have a different name or weird things are gonna happen. This must be a non-empty value.

* **using** (Object)

A mapping of variables to bind in this template. See the following category on Variable Binding on what this means and how to use them.

* **x** (integer)

The horizontal offset of this template within the one including it. All elements in the template will be shifted horizontally by this value. Defaults to 0.

* **y** (integer)

The horizontal offset of this template within the one including it. All elements in the template will be shifted horizontally by this value. Defaults to 0.

## Variable Binding

Variables in an included template can be resolved in the entry that is using the main template, just like any other variable. The referenced by "#as.name". For example, say the main template includes a template with the "as" value set to "incl", and the included template has some text with the variable "#text". To set the value of this variable in your entry, you'd use "#incl.text".

But what if you want a different name? That's doable as well! Open up a "using" object inside your inclusion object, it should look something like this, for our case:

``` 
"include": [
    {
        "template": "sometemplate",
        "as": "incl",
        "using": {
             
        }
    }
]
``` 
