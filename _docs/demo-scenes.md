---
title: "Demo Scenes"
permalink: /demo-scenes/
excerpt: "Demo Scenes"
toc: true
---

We tried to depict the big spectrum of possibilities using various scenes. They are one of ten million examples of possible Flat Kit use
cases. Consider viewing them as starting points or macro-preset objects for your own project.

# Valley
*Valley*, scene is environmental. There we tried to show the work of both fog systems of Flat Kit. Also it is one of the perspectives of displaying the shaders — how these would look in a large scene.
This scene uses [Terrain shader](/terrain/) and cut out transparent textures inside the [Stylized Surface shader](/stylized-surface/).

*Valley* demo scene is also an example of the obvious, rather than subtle, use of [Fog Image Effect](/fog/). Once the scene is loaded, you can scan through the *Fog image effect* presets to
find which one you like more. There is a [Presets](/presets/) chapter in this manual with explanation of how to use them.

In the *Valley* scene, please note that although the ground is made with Unity native terrain, the trees on it are populated manually, not
using the terrain system.
{: .notice--info}

[![](/Screenshots/Valley1.png){: .image-fancy }](/Screenshots/Valley1.png)

# Wanderer
*Wanderer* scene is environmental as well.

You can see how to use [Outline image effect](/outline/), [Fog image effect](/fog) and [Light Plane shader](/light-plane) as an additional fog in this scene.

[![](/Screenshots/Wanderer.png){: .image-fancy }](/Screenshots/Wanderer.png)

# Blueprint Grid (Mugs)
*Blueprint Grid (Mugs)* is an exhibition of the most sought use cases of cel / toon shading.

However, you can find more experimental stuff there, too. It has been a temptation to overpopulate the scenes with content, because while making these included materials — literally dozens of interesting by-product or work-in-progress materials showed up, but we had to discard them to keep the scenes clean.
*Blueprint Grid* scene is a descriptive one, there is a text telling what we used to get the displayed materials.

[![](/Screenshots/Mugs%20-%20Scene1%20-%20OneColorVariousParameters.png){: .image-fancy }](/Screenshots/Mugs%20-%20Scene1%20-%20OneColorVariousParameters.png)

[![](/Screenshots/Mugs%20-%20Scene2%20-%20ColorfulMisc.png)](/Screenshots/Mugs%20-%20Scene2%20-%20ColorfulMisc.png)

# Fruit Vase

There are 7 scene variations in *Fruit Vase* scene. Each scene is dedicated to some specific look, thus uses a different set of materials and two outline methods: [Stylized Surface (Outline parameter)](/stylized-surface/#outline) and [Outline image effect](/outlines/).

[![](/Screenshots/1-FruitVaseScene-CelShadingMode-None-CompletelyFlat.png){: .image-fancy }](/Screenshots/1-FruitVaseScene-CelShadingMode-None-CompletelyFlat.png)

{:.image-caption}
Cel Shading Mode: None, Completely Flat

[![](/Screenshots/2-FruitVaseScene-CelShadingMode-Single.png){: .image-fancy }](/Screenshots/2-FruitVaseScene-CelShadingMode-Single.png)

{:.image-caption}
Cel Shading Mode: Single

[![](/Screenshots/3-FruitVaseScene-CelShadingMode-Steps.png){: .image-fancy }](/Screenshots/3-FruitVaseScene-CelShadingMode-Steps.png)

{:.image-caption}
Cel Shading Mode: Steps

[![](/Screenshots/4-FruitVaseScene-CelShadingMode-Curve.png){: .image-fancy }](/Screenshots/4-FruitVaseScene-CelShadingMode-Curve.png)

{:.image-caption}
Cel Shading Mode: Curve

[![](/Screenshots/5-FruitVaseScene-Var-StylizedSurfaceShaderWithOutlines.png){: .image-fancy }](/Screenshots/5-FruitVaseScene-Var-StylizedSurfaceShaderWithOutlines.png)

{:.image-caption}
Stylized Surface Shader with 'Outline' parameter

[![](/Screenshots/6-FruitVaseScene-Var-TwoColor.png){: .image-fancy }](/Screenshots/6-FruitVaseScene-Var-TwoColor.png)

{:.image-caption}
Two Color shading using Stylized Surface Shader

[![](/Screenshots/7-FruitVaseScene-Var-OutlineImageEffect.png){: .image-fancy }](/Screenshots/7-FruitVaseScene-Var-OutlineImageEffect.png)

{:.image-caption}
Outline Image Effect

# Tree Island
*Tree Island* scene is a showcase of a more cartoony use case. Imagine a 3d-platform game with such a look. Or any other arcade game.

[![](/Screenshots/IslandWithTrees-Scene.png){: .image-fancy }](/Screenshots/IslandWithTrees-Scene.png)

# Room
*Room*. We just had to include a room.

[![](/Screenshots/Room.png){: .image-fancy }](/Screenshots/Room.png)

[![](/Screenshots/Room-2.png){: .image-fancy }](/Screenshots/Room-2.png)

[![](/Screenshots/Room-3.png){: .image-fancy }](/Screenshots/Room-3.png)

# Retro Cars
*Retro Cars*. Retro cars are curvy. A great opportunity to show how shiny (or rough) shaders can be. There are 4 scene sets.

[![](/Screenshots/Car%20-%20Scene%20-%20Set1.png){: .image-fancy }](/Screenshots/Car%20-%20Scene%20-%20Set1.png)

{:.image-caption}
Cars scene — Set 1

[![](/Screenshots/Car%20-%20Scene%20-%20Set2.png){: .image-fancy }](/Screenshots/Car%20-%20Scene%20-%20Set2.png)

{:.image-caption}
Cars scene — Set 2

[![](/Screenshots/Car%20-%20Scene%20-%20Set3.png){: .image-fancy }](/Screenshots/Car%20-%20Scene%20-%20Set3.png)

{:.image-caption}
Cars scene — Set 3

[![](/Screenshots/Car%20-%20Scene%20-%20Set4.png){: .image-fancy }](/Screenshots/Car%20-%20Scene%20-%20Set4.png)

{:.image-caption}
Cars scene — Set 4

# Normal Map Tree
An example of [normal maps](/stylized-surface/#normal-map-to-make-an-impression-of-a-relatively-low-poly-mesh-h) application of [Stylized Surface shader](/stylized-surface/).

[![](/Screenshots/NormalMapsTree%20-%20Scene.png){: .image-fancy }](/Screenshots/NormalMapsTree%20-%20Scene.png)

# Ocean Water
This is a demo scene showcasing the [Water shader](/water/) in a way the game would look like. A non-toon-shading application for [Stylized Surface shader](/stylized-surface/) is showed in this scene, too. You can choose various water looks in the Hierarchy tab by switching different Water objects on.

This scene is in Universal RP only.
{: .notice--warning}

[![](/Screenshots/Ocean%20Islands.png){: .image-fancy }](/Screenshots/Ocean%20Islands.png)

# Pool
*Pool* scene shows more various versions of the [Water shader](/water/). In the Hierarchy tab you can choose between different water objects. Each of these objects has its own *Water* material.

This scene is in Universal RP only.
{: .notice--warning}

[![](/Screenshots/Pool.png){: .image-fancy }](/Screenshots/Pool.png)

{% include video.html url='/FlatKit_Manual_Videos/water-pool-waterobjects-presets.mp4' %}{: .image-fancy}

# Water Vessels
*Water Vessels* is an shows a few simple and more non-obvious [Water shader](/water/) parameters in a single scene. Having these materials, you can use them as starting points in you own projects.

This scene is in Universal RP only.
{: .notice--warning}

[![](/Screenshots/Water%20Vessels%20-%20Various%20Water%20Presets.png){: .image-fancy }](/Screenshots/Water%20Vessels%20-%20Various%20Water%20Presets.png)
