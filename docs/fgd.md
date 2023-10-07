
# Forge Game Data

> _FGD stands for "Forge Game Data", leftover from when the Half-Life 2 level editor Hammer used to be the Half-Life 1 editor Worldcraft, and before that when it was a Quake tool called Forge._

[<p align=right>**The Level Design Book**](https://book.leveldesignbook.com/appendix/resources/formats/fgd#history)

If the Game Config file is what tells TrenchBroom about the existence of your game, then the FGD file is what tells TrenchBroom about all of the stuff that's in it.

Let's get started by creating a new **QodotFGDFile** resource in our _tb/fgd/_ folder.

<p align=center><img src="../images/fgd0.png" width=75%><br>

Now that we have our fresh new FGD resource, let's take a look at all of its properties.

<p align=center><img src="../images/fgd1.png"><br><br>

| Property | Description |
| --- | --- |
| `Export File` | This behaves the same way as the Game Config's _Export_ property, acting more as a button that exports your consolidated FGD resources as a TrenchBroom-compatible FGD file. |
| `Target Folder` | This should be the specific game folder that was created by the Game Config resource (eg: _Trenchbroom/games/Qodot Tutorial/_). Your FGD file will be created in this folder. |
| `Fgd Name` | The filename of your FGD, without the extension. |
| `Base Fgd Files` | Maybe you want to create separate FGD resources for organization or reusability. Any _Base FGD_ resource you add to this array will be compiled together with this FGD resource, ultimately compiling into one FGD file for TrenchBroom. |
| `Entity Definitions` | This is where you will add all of your Base, Solid, and Point Class Entity Definition resources. All of the entity definitions added here will be compiled into the FGD file upon export. |
<br>

For something so important, the FGD resource is pretty simple and straight-forward. Go ahead and set the target folder and FGD name.

### Game Configuration Part 3

Go back to our Game Config resource, we have one last thing we need to do with it: add our newly created FGD resource to the Game Config's `Fgd Files` array. When you've done that, you should have a GameConfig that, aside from personal naming conventions, looks like this. Go ahead and _Export File_ so that the Game Config now points to our new FGD file.

<p align=center><img src="../images/tb_config3.png"><br>

