---
layout: project
title: Glasses CAD Rendering
description: Advanced CAD Project
technologies: [Autodesk Fusion]
image: /assets/images/glasses-render.png
---

In MAE 2250 Introduction to Mechanical Engineering, we were asked to CAD a complex object. I chose a pair of glasses. I identified the basic components of the glasses and began by measuring and physically sketching key lengths and widths.

![Initial Sketch]({{ "/assets/images/glasses-sketch.png" | relative_url }}){: .inline-image-r style="width: 200px"}

In Fusion, I began with modeling the right half from the back forward, starting from the plastic end and ending with constructing half of the middle nose piece. For the frame and arms, I sketched their path, and then added the cross-sectional areas with which to loft or sweep. When possible, I extruded simple geometries to create the pieces. In the case of the lens, which varies in thickness, I could not simply extrude; I worked around this by instead sketching the negative space and extruding that to cut the lens. It was easiest to continually add sketches and thus bodies in their proper positions with respect to the rest of the model, though I did have to move some pieces after construction. This is suboptimal, and if I were to do it again, I would start each sketch at the proper location, instead of making them at the origin and moving them later. I also simplified my model by excluding the screws. Lastly, I took advantage of symmetry and mirrored the glasses across the plane of the middle piece.