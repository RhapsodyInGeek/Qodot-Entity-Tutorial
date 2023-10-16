<p align=center>
<a href="../readme.md">Home</a> |
<a href="qodot.md">What <i>IS</i> Qodot?</a> | 
<a href="setup.md">Setting Up Your Project</a> | 
<a href="gamemanager.md">The Game Manager Autoload</a> | 
<a href="entities.md">What's an Entity?</a> | 
<a href="baseclass.md">Base Classes and Property Definitions</a> | 
<a href="solidclass.md">Solid Entities</a> | 
<a href="pointclass.md">Point Entities, Part 1</a> | 
<a href="pointclass2.md">Point Entities, Part 2</a> | 
<a href="gameconfig.md">Game Configuration</a> | 
<a href="fgd.md">Forge Game Data</a> | 
<a href="textures.md">Textures!</a> | 
<a href="trenchbroom.md">Finally. TrenchBroom.</a> | 
<a href="qodotmap.md">Building the QodotMap</a> | 
<a href="resources.md">Helpful Resources</a> |
<a href="faq.md">Frequently Asked Qodots</a> 
</p>

---

# Frequently Asked Qodots

[Why are my textures blurry?](#why-are-my-textures-blurry)<br>

### Why are my textures blurry?

[**Please don't skim through the tutorial.**](textures.md#why-are-my-textures-blurry)

### Can I do...

Yes.

### Why are my new entities not building? Why can't I find them in TrenchBroom?

Double check to make sure you set a [**`Classname`**](entities.md#naming-patterns) in the entity resource before you exported the FGD. If this doesn't exist, Qodot will skip adding it to the FGD file and upon building your map.

### Help! I manually added some nodes to my QodotMap and when I hit build again they all disappeared!

QodotMap nodes will always erase every child they have when rebuilt. There's no practical way for Qodot to confidently differentiate what it built, what was programmatically built as a result of its build, and what was hand placed by the user. This tutorial should have taught you how you can set your game up to easily design every aspect of your levels within TrenchBroom, but if for some reason you still feel the need to manually place nodes you should do so *outside* of the QodotMap node in order to not lose any work.

### How do I split up my map? It only comes out as one big mesh

You're still mapping like you're compiling for the Quake engine. [**You need to map like your target is the Godot Engine.**](solidclass.md#why-not-worldspawn)

### I'm getting a lot of overdraw, why doesn't Qodot get rid of unseen faces?

You're still mapping like you're compiling for the Quake engine. [**You need to map like your target is the Godot Engine.**](trenchbroom.md#mapping-for-quake-godot)

### How do I set multiple model options in one Point Entity, like a `misc_model` or `prop_dynamic`?

TrenchBroom allows you to modify certain meta property options through the use of an entity's own properties. There is a great example of this in [**Quake's FGD file**](https://github.com/jonathanlinat/quake-leveldesign-starterkit/blob/master/trenchbroom/games/Quake/Quake.fgd). Let's look at an example with `item_health`, which uses `spawnflags` to determine if the item becomes a Medkit, a Rotten Medkit, or a Megahealth.

```
@PointClass
    size(0 0 0, 32 32 56)
    base(Appearflags)
    model(
        {{
            spawnflags & 2 ->   ":maps/b_bh100.bsp",
            spawnflags & 1 ->   ":maps/b_bh10.bsp",
                                ":maps/b_bh25.bsp"
        }}
    ) =
    item_health : "Health pack"
[
	spawnflags(flags) =
	[
		1 : "Rotten" : 0
		2 : "Megahealth" : 0
	]
]
```

We can see that the pattern is essentially `property expression -> model path`. While this is fine done via ***flags***, it might be better to use a ***choices*** if you have a lot of models you wish to choose from. A good template might be

```
model(
    {{
        model_id == 1 -> "path": "path/to/model1.glb",
        model_id == 2 -> "path": "path/to/model2.glb",
        model_id == 3 -> "path": "path/to/model3.glb",
        "path": "path/to/model0.glb"    // default value
    }}
) = point_entity : "Example point entity description"
[
    model_id(choices) : "An example model enumerator" : "0" =
    [
        0 : "Model 0"
        1 : "Model 1"
        2 : "Model 2"
        3 : "Model 3"
    ]
]
```

We achieve this with a Dictionary property we can call `model_id` and by adding an element to our `meta_properties` dictionary with the key `model` and the String value `{{ model_id == 1 -> "path": "path/to/model1.glb", model_id == 2 -> "path": "path/to/model2.glb", model_id == 3 -> "path": "path/to/model3.glb", "path": "path/to/model0.glb" }}`.

This doesn't affect the Godot entity that gets built. You'll still need to make your own script that handles the model swaps upon building in Godot. Qodot cannot take care of this for you!

### Why are my textures blurry?

...

---

<p align=center>
<a href="../readme.md">Home</a> |
<a href="qodot.md">What <i>IS</i> Qodot?</a> | 
<a href="setup.md">Setting Up Your Project</a> | 
<a href="gamemanager.md">The Game Manager Autoload</a> | 
<a href="entities.md">What's an Entity?</a> | 
<a href="baseclass.md">Base Classes and Property Definitions</a> | 
<a href="solidclass.md">Solid Entities</a> | 
<a href="pointclass.md">Point Entities, Part 1</a> | 
<a href="pointclass2.md">Point Entities, Part 2</a> | 
<a href="gameconfig.md">Game Configuration</a> | 
<a href="fgd.md">Forge Game Data</a> | 
<a href="textures.md">Textures!</a> | 
<a href="trenchbroom.md">Finally. TrenchBroom.</a> | 
<a href="qodotmap.md">Building the QodotMap</a> | 
<a href="resources.md">Helpful Resources</a> |
<a href="faq.md">Frequently Asked Qodots</a> 
</p>