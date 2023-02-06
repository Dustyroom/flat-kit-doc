---
title: "Water Shader"
permalink: /water/
toc: true
---

Water shader works in URP only. There is no Built-In version of a Water shader in Flat Kit.
{: .notice--warning}

Water shader lets you create a stylized water surface. That's is primary function. If you feel adventurous, you can make many other wobbling, glittering, weird things with it. It has a lot of parameters to fine-tune the look you want. Although this shader may look a bit complicated at first, it is intuitive and has helping tooltips on the parameters.


![Water shader interface](/FlatKit_Manual_Images/water-shader-interface.png){:.image-simple}

{:.image-caption}
*Water* shader interface

First of all, you'll need a surface to place a material with *Water* shader on. A plane with vertex grid will do fine. The more high resolution the water mesh is the smoother and well-defined the waves will be. For extra interest you can slightly displace the vertices while editing the mesh. With Flat Kit you get a few such models.

The controls are grouped into the logical sections. Let's float through the parameters of the shader.

----------------------------

### Colors

**Source** There are two modes of the color input — *Linear* and *Gradient Texture*.

![Water color source dropdown](/FlatKit_Manual_Images/water-color-source-dropdown.png){:.image-simple}

{:.image-caption}
Water color source dropdown

* **Linear.** This one allows to use just colors for *Shallow* and *Deep* parts of water. This effect is simple one — just two colors.

![Water color source dropdown](/FlatKit_Manual_Images/water-color-source-linear.png){:.image-simple}

{:.image-caption}
Water color source - linear

If *Linear* color source is chosen, two exclusive to this mode parameters appear to select colors:

**Shallow.** Color at the top of the water.

**Deep.** Color below the surface.

* **Gradient Texture.** Use this one if you are looking for something fancy. You can create a depth gradient consisting of several colors. Using a Gradient Editor ramp, you can add up to 8 color stops onto the ramp. Now you have a *Shallow* color, *Deep* color and anything you want in between (see *Pool* demo scene).

![Water color source — gradient](/FlatKit_Manual_Images/water-color-source-gradient.png){:.image-simple}

{:.image-caption}
Water color source - gradient. Clicking on the color window opens the Gradient Editor

When you click on the white color field, the Gradient Editor will show up.

![Gradient Editor](/FlatKit_Manual_Images/water-gradient-editor.png){:.image-simple}

{:.image-caption}
Gradient Editor. Edit the gradient and close the window, then save the texture

After you finished editing the color gradient, click the 'Export' button to save the texture somewhere on the disk. We recommend to name the textures with the names beginning on something like 'water...' or 'awesome_gradient...' because later you'll have these textures stacked up one below another in the texture selection window, and it will be much quicker to scroll through them.
When you have your texture saved, the material will be instantly filled with this gradient.

![Export Button](/FlatKit_Manual_Images/water-gradient-export-button.png){:.image-simple}

{:.image-caption}
Export Button. Click it and save the texture to the disk

**Shallow Depth.** This is a lowest point of *Shallow* part. It is a point where *Shallow* part merges with the top of the gradient.

**Gradient Size.** This is the lowest (deepest) point of the gradient. It is a point where it merges with the *Deep* part.

Below is a little chart, which may came handy for understanding the parameters for the coloring part of the *Water* shader.
![Water Gradient Chart](/FlatKit_Manual_Images/water-gradient-chart.png){:.image-simple}

{:.image-caption}
Water Gradient chart

**Transparency.** How clear (transparent) the color of the water is. The transparency doesn't affect other parameters like foam or refractions. This allows you to achieve awesome weird optical effects.

**Shadow Strength.** How visible the shadow is.

----------------------

### Crest

Crest parameter colors the tips of the waves.

**Color.** The color of the wave. It helps accentuate individual waves.

**Size.** How big of a part of a wave is colored (accentuated).

**Sharp transition.** How smoothly the accentuated wave blends into overall color of the water.

----------------------

### Wave geometry

This section determines the overall shape of the waves. All the controls for the mesh displacement can be found here.

**Shape.** The formula that determine how the displacement of the waves is shaped and distributed across the mesh.

* **None** turns displacement waves off. As no waves are visible, the surface becomes flat.
* **Round** is linear (comb-looking) shape with rounded tips;
![Shape parameter — 'Round'](/FlatKit_Manual_Images/wave_shape_round.png){:.image-simple}

{:.image-caption}
Shape parameter — 'Round'

* **Grid** is grid-like (checkerboard-looking) shape;
![Shape parameter — 'Grid'](/FlatKit_Manual_Images/wave_shape_grid.png){:.image-simple}

{:.image-caption}
Shape parameter — 'Grid'

* **Pointy** is more linear (comb-looking) movement with sharp tips.
![Shape parameter — 'Pointy'](/FlatKit_Manual_Images/wave_shape_pointy.png){:.image-simple}

{:.image-caption}
Shape parameter — 'Pointy'

**Speed.** How fast it moves along the Direction parameter.

**Amplitude.** Sets deviation amount, or, how high it is. Use this parameter to set the height of the waves. Positive values 'raise' the waves effect above the base point, negative values make the waves lower than the initial base point.

**Frequency.** Density of the effect.

**Direction.** Direction of the motion. This parameter works tightly with *Speed*. Using these two you can make ponds, pools, seas etc (static water) and rivers, waterfalls etc (streaming water). Please note, there's an independent set of parameters *Speed* and *Direction* for foam as well, described a bit further.

**Noise.** Adds nonlinearity to the *Shape*. Use it to make *Grid*, for example, more chaotic.

----------------------

### Foam

**NOTE:** In order to see the foam, the model must be UV-unwrapped.

**Source.** How the foam is being made — from texture or generated from noise. Please select one of the following parameters:

* **None.** Turns off the foam.
* **GradientNoise.** The foam shape comes from generative noise.
* **Texture.** If you choose *Texture* source, you'll have an option to import your own, preferably seamlessly tiling, texture, or use one of the included ones — we shortlisted the best from dozens of originally pre-generated .png textures to come with Flat Kit. If you are planning to use your own textures, we suggest you to put them into a single (red) color in the import settings to save memory.

**Color.** Color value of the foam. Can be opaque or transparent.

**Shore Depth.** The maximum point where the water is detecting the edges to create a foam 'outline'.

**Amount.** How often 'grains' occur.

**Scale.** How big the foam 'chunks' are.

**Sharpness.** How smooth or sharp the foam is.

**Stretch X.** How stretched the foam is along X axis.

**Stretch Y.** How stretched the foam is along Y axis.

> **TIP.** Sometimes we find it useful to generously stretch the foam along one of the axis, so that the foam becomes a set of straight lines. This effect definitely can have its use.

**Speed.** How fast it moves along the Direction parameter.

**Direction.** Direction of the motion. This parameter works tightly with *Speed*. Using these two you can make ponds, pools, seas etc (static water) and rivers, waterfalls etc (streaming water)

----------------------

### Refraction

Use these parameters to control the optical distortion of the water.

**Frequency.** The frequency of noise that creates the refraction.

**Amplitude.** The deviation from the initial point.

**Speed.** How fast the refraction moves on the water.

**Scale.** How big is the noise that creates the refraction.

----------------------
We included a component called *Buoyancy*. The *Water* shader deforms the water mesh, which in its turn moves the objects that have *Buoyancy* component on them. More info can be found in the [Buoyancy](/additional-scripts/#buoyancy) part of Additional Scripts section of this manual.

> **TIP.** Place the plane somewhere behind or in front of your scene objects. Place the *Water* shader on it. Set *Clearness* to max, set foam *scale* to very high, lower the *frequency*, as well as opacity. With fine-tuning, it is possible to achieve something like a film grain effect.

## ‘Terrain’ Shader

Terrains are great in Unity. But it’s not so trivial to work with terrain materials, that is why we added a separate shader that deals with the Unity Terrain system.

If you are not familiar with Unity Terrains, please refer to their documentation. In two words, terrain uses Terrain Layers, something like containers of all textures — diffuse, normal, bump etc. FlatKit *Terrain* shader sees those textures and applies its own colors onto the layers. Since we are talking about the flat look, no normal or bump maps are required. In order to have full control over colors of the terrain, you can load a plain white texture as your terrain layer (on *Valley demo* scene we did so). All the colors will be available from the shader interface, they will be multiplied with your white texture, resulting in the pure color you choose. If you are already familiar with *Stylized Surface* shader, *Terrain* shader interface won’t be news to you. [*Stylized Surface* info is here](#stylized-surface-shader).

This is an appropriate time to talk about Height Gradient parameter Flat Kit offers. You can use it as a part of Stylized Surface, Stylized Surface Cutout and Terrain shaders. Height Gradient works wonders on terrain in context of flat shading.

Usually flat shaded landscape objects lack organic embellishment the real world has. All extra-shadows, small scale details, big and tiny grunge spots etc make the picture nonlinear to our eyes, thus, interesting, engaging. With flat aesthetics — there is a color, there may be a shadow or shadows, maybe a few models for the more natural look. The result — quite a boring scene. If you want a more polished look, you’ll want to fight linearity, with *Height Gradient* coming handy. It stretches the interpolation between transparency and its own color along the vertical axis (by default) and multiplies the gradient over the colors you already have. You can rotate the direction, so that it is no longer vertical but diagonal, horizontal and all in-between.
This effect changes the scene dramatically. Now, the terrain has its shadow work that you set on the interface, and on top of that there is a gradient, subtle or obvious. Immediately, it adds depth and a more professional look to the scene.
If you work on some kind of an environmental landscape object but do not use Unity Terrain, please use the *Stylized Surface* shader instead of *Terrain*. *Height Gradient* is available there, too.

![Height Gradient on Unity Terrain (without on upper image, with — on lower one). Valley Demo Scene](/FlatKit_Manual_Images/height-gradient-example-01.png){:.image-simple}

{:.image-caption}
Height Gradient on Unity Terrain (without on upper image, with — on lower one). Valley Demo Scene

## ‘LightPlane’ Shader

This shader is what we are particularly proud of. It looks like a small tool. But it has immeasurable possibilities. Fog, mist, delicate scene boundaries, light beams, glow of magic swords, laser beams. These things are what *LightPlane* is for.

The *Wanderer* demo scene includes *LightPlane* shader implemented not only as fog areas, but also as light beams of so-called pick-up objects and even as planets. The *Valley* demo scene has got the *LightPlane* shader used as floating air particles thanks to the Unity particle system.

![LightPlane Shader. Inspector panel interface](/FlatKit_Manual_Images/light_plane_interface.png){:.image-simple}

{:.image-caption}
LightPlane Shader. Inspector panel interface

The parameters of the *LightPlane* shader are:

* *Depth Fade Distance* controls how quickly the **objects behind light plane** become hidden. Imagine you are looking at a frosted glass window. Any objects that are very close to the window on the other side are clearly visible, but anything that's far behind the window is completely blurred out. *Depth Fade Distance* defines how far the objects need to be from the window to become completely invisible.

* *Camera Distance Fade Close* / *Camera Distance Fade Far* control distance range from the camera at which **the light plane object** transitions from transparent to opaque (see pic below).

![LightPlane — Camera Distance parameters](/FlatKit_Manual_Images/lightplane-camera-dist.png){:.image-simple}

{:.image-caption}
*LightPlane* — *Camera Distance X and Y* parameters

* *UV Fade X* controls transparency on the sides along X axis of the plane/mesh (see pic below);

![LightPlane — UV Fade X parameter](/FlatKit_Manual_Images/lightplane-uv-fade-dist-x.png){:.image-simple}

{:.image-caption}
*LightPlane* — *UV Fade X* parameter

* *UV Fade Y* controls transparency on the sides along Y axis of the plane/mesh (see pic below);

![LightPlane — UV Fade Y parameter](/FlatKit_Manual_Images/lightplane-uv-fade-dist-y.png){:.image-simple}

{:.image-caption}
*LightPlane* — *UV Fade Y* parameter

When combined, *UV Fade X* and *UV Fade Y* can make a fluffy blob.

![LightPlane — UV Fade X and UV Fade Y parameters combined](/FlatKit_Manual_Images/lightplane-uv-fade-dist-x-y.png){:.image-simple}

{:.image-caption}
*LightPlane* — *UV Fade X* and *UV Fade Y* parameters combined

* *Allow Alpha Overflow* makes alpha more than '1', used for HDR, looks nice with some bloom.

## GPU Instancing

When the `Enable Instancing` option is enabled on a material, the shaders can perform [GPU Instancing](https://docs.unity3d.com/Manual/GPUInstancing.html) of the following fields that are common across all Flat Kit shaders:

1. *Color* value (property name `_Color`),
1. Parameters of the cel shading mode *“Single”*
    * *Shaded Color* value (property name `_ColorDim`),
1. Specular parameters, active when *“Enable Specular”* is checked
    * *Specular Color* value (property name `_FlatSpecularColor`),
    * *Specular Size* value (property name `_FlatSpecularSize`),
    * *Edge Smoothness* value (property name `_FlatSpecularEdgeSmoothness`),
1. Rim light parameters, active when *“Enable Rim”* is checked
    * *Rim color* value (property name `_FlatRimColor`),
    * *Rim size* value (property name `_FlatRimSize`),
    * *Edge Smoothness* value (property name `_FlatRimEdgeSmoothness`),
    * *Light Align* value (property name `_FlatRimLightAlign`),
1. Unity shadow parameters, located in the *“Unity Built-in Shadows”* section
    * *Color* value (property name `_UnityShadowColor`).
