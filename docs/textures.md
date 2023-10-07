
# Textures!

***How Textures Work: Trenchbroom***<br>
To get textures to show up in your map file, you need to point TrenchBroom to the game's location. You do this by finding 

***How Textures Work: Qodot***<br>
If you take a look at a _.map_ file, you'll see that it's just a text file describing the makeup of your map and doesn't actually store any other data, including texture images. Let's look at this example of a **Solid Entity** in a map file:<br>

<p align=center><img src="../images/solidEnt00.png" height=250 /><br>

```
// entity 1
{
"classname" "wall"
// brush 0
{
( -32 0 -16 ) ( -32 1 -16 ) ( -32 0 -15 ) special/clip [ 0 -1 0 0 ] [ 0 0 -1 0 ] 0 1 1
( 0 -32 -16 ) ( 0 -32 -15 ) ( 1 -32 -16 ) special/clip [ 1 0 0 0 ] [ 0 0 -1 0 ] 0 1 1
( 0 0 -32 ) ( 1 0 -32 ) ( 0 1 -32 ) base/checkerboard [ -1 0 0 0 ] [ 0 -1 0 0 ] 0 1 1
( 128 128 32 ) ( 128 129 32 ) ( 129 128 32 ) base/checkerboard [ 1 0 0 0 ] [ 0 -1 0 0 ] 0 1 1
( 128 32 16 ) ( 129 32 16 ) ( 128 32 17 ) special/clip [ -1 0 0 0 ] [ 0 0 -1 0 ] 0 1 1
( 32 128 16 ) ( 32 128 17 ) ( 32 129 16 ) base/checkerboard [ 0 1 0 0 ] [ 0 0 -1 0 ] 0 1 1
}
}
```

This is a `wall` entity from the built-in example `Qodot.fgd`. As you can see, the map file structure is pretty straight-forward. This particular map uses the Valve 220 format, having additional options for UV mapping. Each line in a brush definition describes a face on the brush, and within that you can see that our texture is defined as just its location relative to the map's texture folder or WAD file.

_But if that's the case, how does Qodot know what file to use?_<br>
QodotMap nodes have several properties that help define and apply textures to your meshes on build:

| Property | Description |
| --- | --- |
| `Base Texture Dir` | Root folder where your Godot map textures are located |
| `Texture File Extensions` | The extensions to search for if no matching material is found |
| `Texture Wads` | Array of WAD resources to search through |
| `Material File Extension` | Format for custom texture materials, can be _.tres_, _.res_ or _.material_ |
| `Default Material` | The default material that Qodot builds your map's materials from |
<br>

<p align=center><img src="../images/mapNode.png" /><br>

Qodot's first step is to search the `Base Texture Dir` for a prebuilt material as defined by the brush face's texture name in the format defined by `Material File Extension`.

If it does not find this prebuilt material, it will search the `Base Texture Dir` for the _Texture2D_ resource by the brush face's texture name using any one of the extensions defined by `Texture File Extensions`. If it finds the Texture2D, it will create a copy of the `Default Material` and apply the Texture2D as the duplicated material's albedo.

Qodot also has a method to [**automatically build PBR materials**](https://qodotplugin.github.io/docs/materials.html#automatic-pbr-texturing) if your textures are organized a specific way, but that's outside the scope of this tutorial.

_What about WADs?_<br>
I dunno, I don't use them and I don't recommend you use them either.

_What if I really want to use WADs?_<br>
Good luck!

_So what does this expositional onslaught mean for us?_<br>
Well, the neat thing about how Qodot handles map textures is that we can technically use a completely different folder in TrenchBroom and even different image formats than the location and formats we keep them in Godot. This can be useful for advanced users, but for now we'll keep both our TrenchBroom textures and our Godot map textures unified.