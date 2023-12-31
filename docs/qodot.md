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

# What _IS_ Qodot?

> _Qodot extends the Godot editor to import Quake .map files, and provides a data-driven framework for converting the entities and brushes contained therein into a custom node hierarchy._

<p align=right><a href="https://github.com/QodotPlugin/Qodot/tree/main#overview"><b>Official Qodot Overview</b></a><br>

I know you all came here to learn more about entities but I think it's best to get the right headspace for what Qodot actually does and what it doesn't do. That way we can better understand how to work with it to make our games, and not fall into disappointment or frustration over misunderstandings.

Qodot is, at its core, an **interpreter**.

### *It is not a framework.*
Qodot will not make your game for you. Qodot does not make doors, it does not make players, it does not make buttons.

It comes with a set of example entities and FGD, but these are better viewed as what they were intended: examples to show you what you can do with Qodot. This guide will help you learn how to create your own that work for your specific game needs.

### *It is not a BSP compiler.*
Qodot does not compile maps into BSPs. It has no concept of _vis_, no concept of _lit_, no concept of _bsp_. It will not automatically cull faces and sort out occlusion for you. Godot does not work like the early BSP engines. You cannot use Qodot to map for Godot the same way you map for Quake.

This is ***not*** a weakness of the plugin. This is a ***strength***. What you map is what you get. This makes it more reliable than a compiled BSP, since you get to choose what faces get culled and how your collision is generated. This guide will help teach you how to take advantage of this.

### ***Qodot is an interpreter.***
Qodot builds maps by parsing through **map** files that use the Quake 1 or Half-Life 1 formatting. It does this through a combination of understanding brush construction and Entity Definition resources. What you put in is what you get out.

Understanding this concept will hopefully put you on the right path forward to being able to use this wonderfully flexible tool to make some incredible games.

### [**_Next Chapter: Setting Up Your Project >>>_**](setup.md)

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
