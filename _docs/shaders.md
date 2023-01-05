---
title: "Shaders. In-Depth Overview"
permalink: /shaders/
excerpt: "Shaders. In-Depth Overview"
toc: true
---

When you create a material, you’ll choose a shader. By default, Unity has the standard shader picked up. Once installed, all Flat Kit material shaders are located under the Flat Kit sub-menu of the Shader drop-down menu. Please choose the one that would work for your current task. Below is the description of all the shaders.

Our shaders expose shading properties as material features. If a feature toggle is not activated on any materials in the build scenes, the portion of shader code for that feature is not included in the build.
Because of the fact that these shaders are designed for a stylized look as opposed to photorealistic, metallicness and translucency features are not supported. The support for PBR (Physically-Based Rendering) in Flat Kit means that indirect sources of light (e.g. skybox) influence the colors of the material, unless you turn this feature off.

At the moment, there are the following shaders included into Flat Kit: *Stylized Surface*, *Stylized Surface Cutout*, *Stylized Surface with Outline*, *Gradient Skybox*, *Water*, *Terrain*, *LightPlane*.

![Collection of shaders in Flat Kit. From a Shader drop-down, hover the FlatKit sub-menu and choose a shader](/FlatKit_Manual_Images/all_shaders.png)
> Collection of shaders in Flat Kit. From a Shader drop-down, hover the FlatKit sub-menu and choose a shader.

## 'Stylized Surface' Shader

This is a versatile lit shader to be used on rigid object materials. To use it on a material select the shader “FlatKit/Stylized Surface” or “FlatKit/Stylized Surface Cutout” (Built-In RP only). This is your main go-to shader. It works for the vast majority of cases.  
Stylized Surface shader consists of the following **main** building blocks:

* Color,
* Cel Shading mode (None, Single [Cel], Steps, Gradient),
* Extra Cel layer,
* Specular,
* Rim,
* Height Gradient,
* Outline.

The **additional** parameters are:

* Advanced Lighting,
* Unity Built-in Shadows,
* Textures (Albedo, Normal, Emission).

> **NOTE:** Each combination of the features above, used in your project results in generating a **shader variant** during the build process. To limit the build time and the resulting binary size be careful not to add un-useful feature combinations. On the other hand, this mechanism makes sure that only the used features are included in the build. More information on shader variants: <https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html>

![‘Stylized Surface’ shader in Single mode. Simple use case](/FlatKit_Manual_Images/stylized-surface-1.png)
> ‘Stylized Surface’ shader in Single mode. Simple use case.  

![‘Stylized Surface’ shader in Single mode. More complex use case](/FlatKit_Manual_Images/stylized-surface-2.png)
> ‘Stylized Surface’ shader in Single mode. More complex use case with more options engaged, but still, uses only Single mode.  

### The Main Parameters of the Shader

#### Color

This would be the color of your mesh (applicable to most cases, though you can make the shader's other parameters override or mask this main color, if you wish).

#### Cel Shading Mode

This is where you choose the style (mode) of your shading, the color of the shading, and other respective parameters of the modes. Depending on the mode you choose the parameters will look differently. So, let’s talk about modes.

* **None.** Use this to achieve a simple flat look or to get any other creative picture not involving cel shading, however, the following parameters of Stylized Surface shader will still let you do this, if you choose so.  
Note, the flatness and actual representation of colors on the scene depend on the lighting of the scene. In our demos we use Skybox as the source of lighting. Conveniently, there is a Dependency slider on the Lighting panel of Unity, which tells how much of the influence the Skybox provides. At minimum, there won’t be any shadows, as well as the colors will be identical to those you would choose in the *Color* block of the shader. At maximum, the Skybox heavily dictates what the colors will look like. For more natural (not necessarily realistic — but natural, organic look of the scene, it’s healthy to let Skybox influence the coloring of the scene).

* **Single.** This mode provides you with one shadow of chosen *Color*. *Self Shading Size* is the size of the cel. Larger values mean larger size of the shadow. *Shadow Edge Size* controls the sharpness of the cel. The lower the value — the sharper the cel. The higher the value — the more blurry is the shadow. *Localized Shading* is basically how condensed the shadow is. Higher values represent sharper cel.

* **Steps.** Basically, you choose the shading color and number of steps to blend from main *Color* into the color you pick up in *Steps* mode.

* **Curve.** The gradient, interpolated transition from one color to another.  
In order to get Steps and Curve modes to work — as soon as you have a number of steps (*Steps* mode) or curve shape (*Curve* mode) chosen — the shader will ask you to save its utility ramp texture somewhere on the disk. It will write the transition onto it. The texture will appear red in the editor. This is because internally we use the R8 texture format for efficiency.

![Curve shading mode of Stylized Surface shader](/FlatKit_Manual_Images/FK-StylizedSurface-Steps-Curves.png)
> *Steps* and *Curve* shading mode of Stylized Surface shader  

#### Extra Cel Layer

This is like another instance of *Single* mode of *Cel Shading Mode*. Works independently from the *main Cel Shading Mode*. It means, you can make main Cel shading as *None* (flat), and add an *Extra Cel Layer*. The result will be the same as if you would have used the *Single mode*. Or, make the *main Cel layer* and *Extra Cel Layer* almost identical, giving an *Extra Cel Layer* a darker color, and making it smaller. This would result in stepping, similar to Steps mode with 1 step. Classic toon.

#### Specular

You can make a, well, specular with this parameter. Also it can be used as another layer of shadow.

* **Specular Color** picks up the color of your glare, the parameter works in HDR.  
* **Specular Size** determines how big the specular is. Higher values mean bigger specular.  
* **Specular Edge Smoothness** — moving slider to the left decreases blurriness and makes specular sharper.

![Specular. Inspector interface](/FlatKit_Manual_Images/specular_parameters.png)
> *Specular*. Inspector interface

#### Rim

Rim was designed as one of the ways to make a specific effect of a color 'wrapping' from behind the object. In some cases it can remind an outline effect.  

* **Rim Color** selects the color of the parameter. It works in HDR.  
* **Light Align** parameter rotates the rim.  
* **Rim Size** controls how big the Rim is. Very high values can serve you as an unlit effect.  
* **Rim Edge Smoothness** — moving slider to the left sharpens the Rim, to the right — makes Rim blurry.

![Rim. Inspector interface](/FlatKit_Manual_Images/rim_parameters.png)
> *Rim*. Inspector interface

You can think of Rim as some kind of inner shadow and/or as inner glow, if used on smoothened curvy models. In one of the *Fruit Vase* demo scenes, there is an example of extensive use of Rim as an outline. On *Blueprint Grid* demo scene *Rim* is used as a smooth inner glow. This parameter can be used creatively, for example, to substitute *Curve mode* or *Extra Cel parameter*. **Just reminding you that the name like 'Rim', 'Specular' etc should not be perceived literally, they can do more than that.** In the screenshot below, with the help of Suzanne the Blender Monkey, we tried to show a few instances of *Stylized Surface* shader with *None* mode selected (meaning no straightforward shadows are applied), using orange color, and only *Rim* parameter enabled. The results are variations of Rim section only. As you see, the *Rim* alone is quite a creative tool. Imagine adding some creative *Specular* and *Height Gradient*...

![Rim only, usage examples](/FlatKit_Manual_Images/rim_examples_suzanne.png)
> Variety of uses of *Rim* parameter alone on Suzanne the Blender Monkey. Interface of *Stylized Surface* shader with *‘None’* cel shading mode

Although *Rim* option is creatively useful and sometimes can remind an outline effect, there are two more obvious ways to add an outline using Flat Kit: to use [Stylized Surface with Outline](#stylized-surface-with-outline-shader) shader and/or to use [Outline Image Effect](/image-effects/#outline-image-effect) camera component in Built-In RP/Forward Renderer's Renderer Feature in URP. We’ll talk about both of them later in this manual.

> **TIP.** Animate Cel layer size, Specular size or Rim size — to get a neat transition effect.

#### Height Gradient

This effect overlays a gradient from opaque selected color to transparent color onto everything you’ve set before. Height Gradient is global (absolute) per material, it doesn't depend on object's boundaries. If you would like to make a relative gradient (for instance, each object holding one material to contain an entire gradient within itself), duplicate the material and adjust the height gradient. Alternatively, you can use a *Curve* mode of *Stylized Surface*.

![Height Gradient. Inspector interface](/FlatKit_Manual_Images/gradient_height_parameters.png)
> *Height Gradient.* Inspector interface

* **Gradient Color** picks the parameter’s own color to fade into from transparency.  
* **Center X** and **Y** are initial points from where the effect takes effect. Adjust these to move the gradient across the scene. Center X is useful if you engage - *Gradient Angle*, which means the rotation of the Gradient.  
* **Size** determines how steep the transition of Gradient is. The further the value is from 0 (zero) — the more gradual the effect is. Negative values flip the Gradient.  
* **Gradient Angle** rotates the gradient.

A bit more about the nature and use of *Height Gradient* is covered in the [*‘Terrain’ Shader*](#terrain-shader) section of this manual.  

#### Enable Vertex Colors

If enabled, the final shading of the object is multiplied by the mesh’s vertex color values. It is a debug parameter, usually this is not used for changing the look.  

#### Outline

![Outline part of Stylized Surface shader. Inspector interface](/FlatKit_Manual_Images/stylized-surface-outline-interface.png)
> *Outline* part of Stylized Surface shader. Inspector interface

The *Outline* part of the *Stylized Surface* shader allows you to add pseudo-outlines to your models.

* **Color** picks up the color of the outline.  
* **Width** determines how thick the outline is.  
* **Scale** adjust this parameter when you have gaps on the vertices (please note, this is not an ultimate solution, the gaps need a complex approach — in modelling, adjusting the normals, adjusting camera distance etc).  
* **Depth Offset** moves the outline inwards or outwards an object.  
* **Camera Distance Impact** **(this parameter is available in Universal RP only)** makes outlines that are further from camera appear thinner than outlines closer to the camera.

Please remember that in addition to this shader Flat Kit has also a global *Outline Image Effect* applied per Forward Renderer (in URP) and per camera (in Built-In RP).  
In the [Outline Image Effect](/image-effects/#outline-image-effect) chapter in this manual you can find some useful specific and general info.

Sometimes it is useful to manipulate the normals of your model in order to force the shader to render outlines where it wouldn't do so otherwise.
More on this is covered in [Outline Image Effect](/image-effects/#outline-image-effect) chapter. But here's one thing you can try without using 3d editor software. Among the other parameters of the import settings of the model, there is a section where is it possible to change the angle detection threshold for normals. It may come handy in adding or removing some of the outlines where they wouldn't appear normally. Also, slight adjustments to these parameters may resolve some of the visual issues. If you have gaps in the outline, for instance, try tweaking these controls (but remember to backup the project first, it's always a good idea to backup things. In fact, if you are working on something, do it now).

![Import settings of the model](/FlatKit_Manual_Images/mesh-import-settings.png)
> Import settings of the model has a section for manipulating the normals, which is useful for the *Stylized Surface with Outline* shader as well as for *Outline* global effect.

Please note that this way of doing the outlines is made to be super fast, but unlike in Photoshop it can't produce an ideal outline. There are fundamental limitations to this fast approach of making the outline. For example, the outline itself in not a hollow contour as such but rather a modified (roughly said, 'expanded') copy of a model layered on the back of the original model. In most cases it can produce very good results with fast performance, but the transparency on this model won't work, as reducing the model's opacity will reveal the filled pseudo-outline layer in the background.

### The Additional Parameters of the Shader

#### Advanced Lighting

**Light Color Contribution.** Light Color Contribution defines how much the color of the light source of the scene impacts the color of the object. The value of 0.0 results in completely ignoring scene lights, the value of 1.0 results in full multiplication between scene light color and the object color. As an example, imagine the winter morning light. Usually it is blue-tinted, thus all the snow around can’t be white but rather blueish.

Please note that the effect is visible only if the color of the light is anything but white.

Light Color Contribution works only with directional light. The point and spot lights are contributing to colors and shading of the material regardless of the Light Color Contribution value.

![Light Color Contribution parameter on Flat Kit shaders Inspector panel](/FlatKit_Manual_Images/light_color_contribution.png)
> *Light Color Contribution* parameter on Flat Kit shaders Inspector panel

Let’s view it in example.  
Three pictures below describe how we change Light Color Contribution values on all (two) used materials: on a sphere and on a plane. Within a picture we change the intensity value of Directional Light as our main source of light.  
Additionally, there is a point light on each picture. This way it’s visible how local lights work together with the main Directional Light.  
Take the first image (below). At first, we turn down the *Intensity* to the very low value. White sun now has no impact on the scene brightness, resulting in a darker scene.  
Then we change the color of Directional Light from white to red. It has no effect because Directional Light is too “weak” to fill the scene.  
After raising *Intensity* value back to “1” the scene is now lighter and has a red tint.  

![Light Color Contribution at value 0.5. Changing intensity value and color of Directional Light](/FlatKit_Manual_Images/lighting_2_color_contrib_0.5.png)
> *Light Color Contribution* at value 0.5. Changing *Intensity* value and color of Directional Light

Once we change *Color Light Contribution* parameter to “0” (pic below), Directional light has no effect light-wise and color-wise. Changing *Intensity* parameter of Directional Light on the Inspector panel has no effect. Both sides of the picture are identical.  
This way you can achieve a flat look, in other words, the colors on the scene are exactly the same as you choose in the shader parameters.

![Light Color Contribution at value 0. Directional Light intensity at max and min values](/FlatKit_Manual_Images/lighting_1_color_contrib_0.png)
> *Light Color Contribution* at value 0. Directional Light *Intensity* at max and min values

Now, (on the pic below) we raise *Light Color Contribution* to the max value of “1”. If we set Directional Light *Intensity* parameter low, the scene theoretically has no source of direct light. Local lights now act as the only light sources. If the *Intensity* of Directional Light is at its maximum, it’s too hot now.

![Light Color Contribution at value 1. Changing intensity value of Directional Light](/FlatKit_Manual_Images/lighting_8.png)
> *Light Color Contribution* at value 1. Changing *Intensity* value of Directional Light

If you use a Particle System and choose your particles to emit light, Flat Kit shaders respect that!

![Particles emitting light on Flat Kit shaders](/FlatKit_Manual_Images/lighting_particles_lights.png)
> Particles emitting light on Flat Kit shaders.

**Override light direction** It is a way to make the material have an independent direction of the light from the Directional Light. This can be useful in cases when you need to align the position of the cels or Rim or Specular. Normally, to adjust these parameters globally, you should rotate the Directional light. Once *Override light direction* parameter is enabled, the material no longer obeys the Directional Light, it now has independent mapping vectors for the light-dependent parameters (e.g. mentioned earlier cels, Rim, Specular) that you can adjust with *Pitch* and *Yaw* parameters. Simply put, you can rotate the the cels, Rim and Specular.  

#### Unity Built-in Shadows

If the object has the ‘Receive Shadows’ option turned on in Mesh Renderer, you have an ability to use Unity-processed shadows on it, as you would do in Unity Standard Material shader, with a few extra-options.

![Unity Built-in Shadows mode menu. Inspector interface](/FlatKit_Manual_Images/unity_built_in_shadows_modes.png)
> Unity Built-in Shadows mode menu. Inspector interface

* **Mode** lets you choose the coloring and blending parameters for the built-in shadows. **None** mode turns the built-in shadow parameter off.
**Multiply** mode lets you cast the shadows as in default material. You don’t have direct control over the color. You can change intensity and sharpness. The blending mode is 'Multiply'. **Color** mode lets you choose the color of the cast shadow. The blending mode is 'Normal'.
* **Power** sets how visible the Unity built-in shadow is.
* **Sharpness** defines how blurred or crisp the shadow edge is.
* **Shadow Occlusion** masks received Unity shadows in areas where normals face away from the light. **Useful to remove shadows that 'go through' objects.**

> **NOTE.** *Shadow Occludion* parameter is available in the URP version of Flat Kit only.

![Unity Built-in Shadows in Color mode. Inspector interface](/FlatKit_Manual_Images/unity_built_in_shadows_mode_color_parameters.png)
> *Unity Built-in Shadows* in *Color* mode. Inspector interface

#### Texture Maps

If you’ve got a UV-unwrapped mesh, you can add a diffuse texture to it. If you work with transparency in textures in Built-In RP, please use *Stylized Shader Cutout* shader. It can see alpha on the texture as transparency. URP supports alpha by default.

**Albedo** Allows to use the albedo, or diffuse texture. In URP this slot supports transparent textures by default. Can be used together with *Alpha Clipping* parameter (explained below).

* **Texture selection slot** lets you pick a texture;  
* **Tiling** repeats the texture along X and Y axis;  
* **Offset** shifts the texture along X and Y axis within the UV map of the mesh;  
* **Blending Mode** lets you choose between 'Multiply' or 'Add' blending modes. 'Multiply' Blending Mode multiplies the luminosity of the base color by the blend color. Multiplication by white produces no change, while the black pixels remain, making the material darker. 'Add' Blending Mode is a little bit different from 'Multiply' — blending with black color produces no change, while generally it brightens the bright colors.  
* **Texture Impact** controls how visible the texture is. Values to the left decrease visibility of the texture up until it is invisible.  

> **TIP.** If you would like to have a material with a texture with a cel shading on top of this texture, you can set the *Stylized Surface* to *Single* **Cel Shading Mode**, set the base **Color** to white or light grey, set the  **Color Shaded** parameter to a bit darker one, set the Albedo texture (if your texture is not mostly white) to *Multiply* **Blending mode**, Texture Impact to the maximum value. You should get the model filled with a texture and with cel shadows combined.

**Normal Map** To make an impression of a relatively low-poly mesh having many details of a high-poly one, you can use normal maps. Add one to *Bump Map* slot in the Inspector panel.

![‘Stylized Surface’ shader — normal map applied](/FlatKit_Manual_Images/normalmap-interface.png)
> ‘Stylized Surface’ shader — normal map applied

* **Texture selection slot** lets you pick a texture;  
* **Tiling** repeats the texture along X and Y axis;  
* **Offset** shifts the texture along X and Y axis within the UV map of the mesh;  

![‘Normal Map Tree’ demo scene, a tree without and with a normal map](/FlatKit_Manual_Images/normalmap-trees.png)
> ‘Normal Map Tree’ demo scene, a tree without and with a normal map

**Emission** Enables Emission map part of the shader.  
> **NOTE.** Emission map support is available in Universal RP version of Flat Kit only, there is no Emission map parameter in Built-In version of Flat Kit.  

**Emission Map** Allows to use custom emission maps to designate the parts of the meshes to have a 'glow' effect.  

* **Texture selection slot** lets you pick a texture;  
* **Tiling** repeats the texture along X and Y axis;  
* **Offset** shifts the texture along X and Y axis within the UV map of the mesh;  
* **Emission Color** chooses the color of the 'glowing' effect.  

![Emission map part of the Stylized Surface interface](FlatKit_Manual_Images/stylized-surface-emission-interface.png)
> Emission map part of the Stylized Surface interface  

### Setting material values from scripts

The following are the color field names for manipulation via the code for tweening, randomization etc:

* `_BaseColor` (in URP), `_Color` (in Built-in RP): the primary color, “Color” in the inspector. The alpha value controls transparency of the object if `Surface Type` is set to `Transparent`
* `_ColorDim` (and `_ColorDimSteps`, `_ColorDimCurve` in the corresponding cel shading modes): Color Shaded in the Inspector
* `_ColorDimExtra`: the shaded color of the *“Extra Cel Layer”* feature
* `_FlatRimColor`: rim color, requires *“Enable Rim Color”*
* `_FlatSpecularColor`: specular color, requires *“Enable Specular Color”*
* `_ColorGradient`: the gradient color used along with the `_BaseColor` parameter when *“Enable Height Color”* feature is active
* The full list of parameters is at the top of the file `Assets/FlatKit/Shaders/StylizedSurface/StylizedSurface.shader`.

> **NOTE.** The outline toggle is implemented as a [shader keyword](https://docs.unity3d.com/Manual/shader-keywords.html), so unfortunately it can't be toggled at runtime. However, you can enable the outline in the material inspector and toggle its visibility in code by setting the outline width (0 will visually disable the outline). Or, you can create two identical materials with the only difference being the outline toggle, and switch between these materials at runtime with `renderer.material = myMaterial`.

## Stylized Surface Cutout Shader

> **NOTE:** '*Stylized Surface Cutout*' shader has been deprecated in Flat Kit 2.1.2 for Universal RP version. Because URP supports transparency by default, there's no need for this separate shader in URP. The *Stylized Surface* and *Stylized Surface with Outline* shaders can do everything *Stylized Surface Cutout* could — using *Rendering options* part of the shaders in the bottom of the interface. There you can find an option to set the shading in transparency mode (*Surface Type* drop down menu ▶︎ *Transparent*. The default type is *Opaque*) '*Stylized Surface Cutout*' is still available in Built-In RP version.
{: .notice--warning}

This is a version of *Stylized Surface* shader with an option to treat alpha as transparency on a texture. The rest of the shader is the same.

The *Base Alpha cutout* parameter determines how much of the alpha portion of the texture is going to be transparent.

![‘Stylized Surface Cutout’ shader — Valley demo scene, tree branches material. Inspector interface](/FlatKit_Manual_Images/stylized_surface_cutout_screenshot.png)
> ‘Stylized Surface Cutout’ shader — Valley demo scene, tree branches material. Inspector interface

Use this shader if you work with transparency in Built-In RP. In URP you are good to go with the *Stylized Surface* shader instead of this one. It will spare a few cycles from your CPU.

## Stylized Surface with Outline Shader

> **NOTE:** *Stylized Surface with Outline* shader has been deprecated in Universal RP version of Flat Kit: the outline functionality has been moved to the *Stylized Surface* shader. *Stylized Surface with Outline* remains available and working for the sake of compatibility with existing projects, but it is advised to use *Stylized Surface* for the new projects instead. *Stylized Surface with Outline* has not been deprecated in Built-In LTS version of Flat Kit.
{: .notice--warning}

*Stylized Surface with Outline* shader, being the same as the regular *Stylized Surface* shader in a nutshell, has an additional option of... outlines. [*Stylized Surface* info is here](#stylized-surface-shader).

![‘Stylized Surface with Outline’ shader](/FlatKit_Manual_Images/stylized_surface_with_outline_interface.png)
> ‘Stylized Surface with Outline’ shader

* **Color** picks up the color of the outline.  
* **Width** determines how thick the outline is.  
* **Scale** adjust this parameter when you have gaps on the vertices (please note, this is not an ultimate solution, the gaps need a complex approach — in modelling, adjusting the normals, adjusting camera distance etc).  
* **Depth Offset** moves the outline inwards or outwards an object.  
* **Camera Distance Impact** **(this parameter is available in Universal RP only)** makes outlines that are further from camera appear thinner than outlines closer to the camera.

## Gradient Skybox Shader

This is a simple method to fill the sky of your scene.

* **Top Color** and **Bottom Color** define two colors to be blended.  
* **Intensity** is a darkness/brightness controller of the skybox.  
* **Exponent** accentuates the effect in favour of either *Top Color* or *Bottom Color*.  
* **Direction X angle** and **Direction Y angle** rotate the effect along the corresponding axis.  

> **TIP.** Make *Top Color* and *Bottom Color* identical colors or move the *Exponent* parameter to one of the extremes if you want a flat background.

![Gradient Skybox. Inspector panel interface](/FlatKit_Manual_Images/gradient-skybox-interface.png)
> Gradient Skybox. Inspector panel interface

## Water Shader

Water shader works in URP only. There is no Built-In version of a Water shader in Flat Kit.

Water shader lets you create a stylized water surface. That's is primary function. If you feel adventurous, you can make many other wobbling, glittering, weird things with it. It has a lot of parameters to fine-tune the look you want. Although this shader may look a bit complicated at first, it is intuitive and has helping tooltips on the parameters.

![Water shader interface](/FlatKit_Manual_Images/water-shader-interface.png)
> *Water* shader interface

First of all, you'll need a surface to place a material with *Water* shader on. A plane with vertex grid will do fine. The more high resolution the water mesh is the smoother and well-defined the waves will be. For extra interest you can slightly displace the vertices while editing the mesh. With Flat Kit you get a few such models.

The controls are grouped into the logical sections. Let's float through the parameters of the shader.

----------------------------

### Colors

**Source** There are two modes of the color input — *Linear* and *Gradient Texture*.

![Water color source dropdown](/FlatKit_Manual_Images/water-color-source-dropdown.png)
> Water color source dropdown

* **Linear.** This one allows to use just colors for *Shallow* and *Deep* parts of water. This effect is simple one — just two colors.

![Water color source dropdown](/FlatKit_Manual_Images/water-color-source-linear.png)
> Water color source - linear

If *Linear* color source is chosen, two exclusive to this mode parameters appear to select colors:

**Shallow.** Color at the top of the water.

**Deep.** Color below the surface.  

* **Gradient Texture.** Use this one if you are looking for something fancy. You can create a depth gradient consisting of several colors. Using a Gradient Editor ramp, you can add up to 8 color stops onto the ramp. Now you have a *Shallow* color, *Deep* color and anything you want in between (see *Pool* demo scene).

![Water color source — gradient](/FlatKit_Manual_Images/water-color-source-gradient.png)
> Water color source - gradient. Clicking on the color window opens the Gradient Editor.

When you click on the white color field, the Gradient Editor will show up.

![Gradient Editor](/FlatKit_Manual_Images/water-gradient-editor.png)
> Gradient Editor. Edit the gradient and close the window, then save the texture.

After you finished editing the color gradient, click the 'Export' button to save the texture somewhere on the disk. We recommend to name the textures with the names beginning on something like 'water...' or 'awesome_gradient...' because later you'll have these textures stacked up one below another in the texture selection window, and it will be much quicker to scroll through them.  
When you have your texture saved, the material will be instantly filled with this gradient.

![Export Button](/FlatKit_Manual_Images/water-gradient-export-button.png)
> Export Button. Click it and save the texture to the disk.

**Shallow Depth.** This is a lowest point of *Shallow* part. It is a point where *Shallow* part merges with the top of the gradient.

**Gradient Size.** This is the lowest (deepest) point of the gradient. It is a point where it merges with the *Deep* part.

Below is a little chart, which may came handy for understanding the parameters for the coloring part of the *Water* shader.
![Water Gradient Chart](/FlatKit_Manual_Images/water-gradient-chart.png)
> Water Gradient chart

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
![Shape parameter — 'Round'](/FlatKit_Manual_Images/wave_shape_round.png)

> Shape parameter — 'Round'

* **Grid** is grid-like (checkerboard-looking) shape;
![Shape parameter — 'Grid'](/FlatKit_Manual_Images/wave_shape_grid.png)

> Shape parameter — 'Grid'

* **Pointy** is more linear (comb-looking) movement with sharp tips.
![Shape parameter — 'Pointy'](/FlatKit_Manual_Images/wave_shape_pointy.png)

> Shape parameter — 'Pointy'

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

![Height Gradient on Unity Terrain (without on upper image, with — on lower one). Valley Demo Scene](/FlatKit_Manual_Images/height-gradient-example-01.png)
> Height Gradient on Unity Terrain (without on upper image, with — on lower one). Valley Demo Scene

## ‘LightPlane’ Shader

This shader is what we are particularly proud of. It looks like a small tool. But it has immeasurable possibilities. Fog, mist, delicate scene boundaries, light beams, glow of magic swords, laser beams. These things are what *LightPlane* is for.

The *Wanderer* demo scene includes *LightPlane* shader implemented not only as fog areas, but also as light beams of so-called pick-up objects and even as planets. The *Valley* demo scene has got the *LightPlane* shader used as floating air particles thanks to the Unity particle system.

![LightPlane Shader. Inspector panel interface](/FlatKit_Manual_Images/light_plane_interface.png)
> LightPlane Shader. Inspector panel interface

The parameters of the *LightPlane* shader are:

* *Depth Fade Distance* controls how quickly the **objects behind light plane** become hidden. Imagine you are looking at a frosted glass window. Any objects that are very close to the window on the other side are clearly visible, but anything that's far behind the window is completely blurred out. *Depth Fade Distance* defines how far the objects need to be from the window to become completely invisible.

* *Camera Distance Fade Close* / *Camera Distance Fade Far* control distance range from the camera at which **the light plane object** transitions from transparent to opaque (see pic below).

![LightPlane — Camera Distance parameters](/FlatKit_Manual_Images/lightplane-camera-dist.png)
> *LightPlane* — *Camera Distance X and Y* parameters

* *UV Fade X* controls transparency on the sides along X axis of the plane/mesh (see pic below);  

![LightPlane — UV Fade X parameter](/FlatKit_Manual_Images/lightplane-uv-fade-dist-x.png)
> *LightPlane* — *UV Fade X* parameter

* *UV Fade Y* controls transparency on the sides along Y axis of the plane/mesh (see pic below);

![LightPlane — UV Fade Y parameter](/FlatKit_Manual_Images/lightplane-uv-fade-dist-y.png)
> *LightPlane* — *UV Fade Y* parameter

When combined, *UV Fade X* and *UV Fade Y* can make a fluffy blob.

![LightPlane — UV Fade X and UV Fade Y parameters combined](/FlatKit_Manual_Images/lightplane-uv-fade-dist-x-y.png)
> *LightPlane* — *UV Fade X* and *UV Fade Y* parameters combined

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