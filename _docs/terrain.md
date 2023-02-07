---
title: "Terrain Shader"
permalink: /terrain/
toc: false
---

Terrains are great in Unity. But it’s not so trivial to work with terrain materials, that is why we added a separate shader that deals with the Unity Terrain system.

If you are not familiar with Unity Terrains, please refer to their documentation. In two words, terrain uses Terrain Layers, something like containers of all textures — diffuse, normal, bump etc. FlatKit *Terrain* shader sees those textures and applies its own colors onto the layers. Since we are talking about the flat look, no normal or bump maps are required. In order to have full control over colors of the terrain, you can load a plain white texture as your terrain layer (on *Valley demo* scene we did so). All the colors will be available from the shader interface, they will be multiplied with your white texture, resulting in the pure color you choose. If you are already familiar with *Stylized Surface* shader, *Terrain* shader interface won’t be news to you. [*Stylized Surface* info is here](#stylized-surface-shader).

This is an appropriate time to talk about Height Gradient parameter Flat Kit offers. You can use it as a part of Stylized Surface, Stylized Surface Cutout and Terrain shaders. Height Gradient works wonders on terrain in context of flat shading.

Usually flat shaded landscape objects lack organic embellishment the real world has. All extra-shadows, small scale details, big and tiny grunge spots etc make the picture nonlinear to our eyes, thus, interesting, engaging. With flat aesthetics — there is a color, there may be a shadow or shadows, maybe a few models for the more natural look. The result — quite a boring scene. If you want a more polished look, you’ll want to fight linearity, with *Height Gradient* coming handy. It stretches the interpolation between transparency and its own color along the vertical axis (by default) and multiplies the gradient over the colors you already have. You can rotate the direction, so that it is no longer vertical but diagonal, horizontal and all in-between.
This effect changes the scene dramatically. Now, the terrain has its shadow work that you set on the interface, and on top of that there is a gradient, subtle or obvious. Immediately, it adds depth and a more professional look to the scene.
If you work on some kind of an environmental landscape object but do not use Unity Terrain, please use the *Stylized Surface* shader instead of *Terrain*. *Height Gradient* is available there, too.

![Height Gradient on Unity Terrain (without on upper image, with — on lower one). Valley Demo Scene](/FlatKit_Manual_Images/height-gradient-example-01.png){:.image-simple}

{:.image-caption}
Height Gradient on Unity Terrain (without on upper image, with — on lower one). Valley Demo Scene
