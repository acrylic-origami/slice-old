## Slice

Using [matter.js](http://brm.io/matter-js/), **Slice** is a block that can be cut to your heart's desire by mouse pointer. The mouse pointer can slice falling blocks while staying totally still. **Try at [slice.lam.io](http://slice.lam.io).**

Soon to be tackled: self-intersecting mouse trajectories in polygons.

### "Wow, that code is kinda long."

Cutting is rife with literal corner and edge cases. This is especially the case handling concave polygons, where the strongest and most expensive cutting procedures have to be used. Each frame updates a cache of mouse cursor positions to track entering and exiting events to polygons. In general, over the course of one frame the mouse cursor could trace any line segment and subdivide many polygons from the same parent polygon. The cutting algorithm here encodes entry and exit cut points as fractions along the boundary and traverses the polygons as they are progressively sliced as a binary tree to transform these cut point coordinates to their new homes in the daughter polygon.

Despite intensive efforts, intersections are still not handled carefully enough, as vertex sets still fail to spawn bodies sometimes when the mouse path goes over an existing vertex.