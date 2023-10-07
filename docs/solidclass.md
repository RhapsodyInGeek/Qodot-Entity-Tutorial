
# Solid Entities<br>

Qodot refers to any entity constructed with brush work as a **Solid Entity**. It isn't entirely accurate to call them _solid_ since we don't actually need to provide these entities with collision. We also don't need to provide these entities with meshes from the brush work either. This is cool, because it means we have a lot of flexibility in how to construct our maps.

TrenchBroom refers to these entity types as **Brush Entities**. TrenchBroom can organize and render these brush entities in specific ways based upon the way we name them and the tags we set up in our Game Config file (more on that later). What does that mean for