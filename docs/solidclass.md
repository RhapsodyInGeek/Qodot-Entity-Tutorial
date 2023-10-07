
# Solid Entities<br>

Qodot refers to any entity constructed with brush work as a **Solid Entity**. It isn't entirely accurate to call them _solid_ since we don't actually need to provide these entities with collision. We also don't need to provide these entities with meshes from the brush work either. This is cool, because it means we have a lot of flexibility in how to construct our maps.

TrenchBroom refers to these entity types as **Brush Entities**. If you'll recall, TrenchBroom can render these types of entities in specific ways based upon their [**naming conventions**](entities.md#naming-patterns) and the [**tags we define in our GameConfig**](gameconfig.md#trenchbroom-tags).

Solid Entities can be map geometry, breakable walls, doors and lifts, floating platforms, buttons, trigger volumes, occlusion polygons... pretty much anything you might want to construct out of brush geometry.

## Worldspawn

As mentioned before, Qodot comes with a set of example Entity Definitions, including one for the `worldspawn` class that comes built-in to every map file. But what _is_ **worldspawn**?

Every Quake map file contains a list of entities containing a set of key value pairs. Some optionally include brush definitions. In Quake, the entity's `classname` is also the spawn function that is called upon map start. The very first entity that needs to load is the world, and so entity 0 is always `worldspawn`.

Simply put, _worldspawn_ is just another entity. It's not even a Solid Entity by default. It needs to be defined in your FGD just like any other entity, too, or else it will revert to default behavior.