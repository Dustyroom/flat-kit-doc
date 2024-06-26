---
title: "Additional Scripts"
permalink: /additional-scripts/
excerpt: "Additional Scripts"
toc: true
---

## UV Scroller

Used in the [Wanderer demo scene](/demo-scenes/#wanderer/). It scrolls waterfall texture along the Y axis. Also used in [Ocean Water demo scene](/demo-scenes/#ocean-water/) under the waterfall.

## Linear Motion

Linear Motion is a simple script that translates (moves) and rotates any object. We used it heavily on cameras to prepare promo video footage. There is an option to translate or rotate along the X, Y, Z axis.

![Linear motion script. Inspector interface](/FlatKit_Manual_Images/ConstantMotion.png){: .image-fancy style="width: 500px;"}

{:.image-caption}
*Linear motion* script. Inspector interface

**TIP.** Use a couple of instances of this component if you want to translate and rotate along more than one axis and make more complex automations.
{:.notice--success}

## Buoyancy

This script is used with [Water shader](/water/) specifically when there is an object on the water surface, and you want it to physically flow on this surface. The object will replicate the water's shape, while water is being deformed. This scripts is added on the object as a component. You'll need to point to the water object mesh this object is interacting with (in _Water_ field of the script interface).

![Buoyancy script interface](/FlatKit_Manual_Images/buoyancy_interface.png){: .image-fancy style="width: 500px;"}

{:.image-caption}
*Buoyancy* script interface

* *Water* field is where you choose the mesh of the water surface. The object holding this script will be afloat on this mesh.
* *Size* parameter sets the definition of the movement, meaning, how many of the _Water_ object's vertices it takes into account.
* *Amplitude* is how far the object travels from its initial point on the water while floating.
* *Override Water Material* an optional parameter which allows you to use a separate water material for buoyancy effect. Specifically, it overrides the [Wave Geometry](/water/#wave-geometry) group of parameters from the original [Water](/water/) material.

## Floating Motion

This script is used in [Desert Demo scene](/demo-scenes/#desert) on the transparent bulb with the robot Kyle.

![Floating Motion script interface](/FlatKit_Manual_Images/flat-kit-floating-motion-component.png){: .image-fancy style="width: 500px;"}

{:.image-caption}
*Floating Motion* script interface

## Auto Load Pipeline Asset

This script is set on Camera as a Component. It automatically loads a URP Asset file ([what's this?](https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@11.0/manual/universalrp-asset.html)) for this scene only. This way there is no need to create the single URP Asset file for the whole Unity project — every scene can have its own one, which makes each scene in the project portable and easy to move, duplicate, A/B test etc.

![Auto Load Pipeline Asset interface](/FlatKit_Manual_Images/flat-kit-auto-load-pipeline-asset-component.png){: .image-fancy style="width: 500px;"}

{:.image-caption}
*Auto Load Pipeline Asset* script interface