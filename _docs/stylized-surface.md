---
title: "Stylized Surface Shader"
permalink: /stylized-surface/
toc: true
---

When you create a material, you’ll choose a shader. By default, Unity has the standard shader picked up. Once installed, all Flat Kit material shaders are located under the Flat Kit sub-menu of the Shader drop-down menu. Please choose the one that would work for your current task. Below is the description of all the shaders.

Our shaders expose shading properties as material features. If a feature toggle is not activated on any materials in the build scenes, the portion of shader code for that feature is not included in the build.
Because of the fact that these shaders are designed for a stylized look as opposed to photorealistic, metallicness and translucency features are not supported. The support for PBR (Physically-Based Rendering) in Flat Kit means that indirect sources of light (e.g. skybox) influence the colors of the material, unless you turn this feature off.

## 'Stylized Surface' Shader

This is a versatile lit shader to be used on rigid object materials. To use it on a material select the shader `FlatKit/Stylized Surface` or `FlatKit/Stylized Surface Cutout` (Built-In RP only). This is your main go-to shader. It works for the vast majority of cases.
Stylized Surface shader consists of the following **main** building blocks:

* Color
* Cel Shading mode (None, Single [Cel], Steps, Gradient)
* Extra Cel layer
* Specular
* Rim
* Height Gradient
* Outline

The **additional** parameters are:

* Advanced Lighting
* Unity Built-in Shadows
* Textures (Albedo, Normal, Emission)
* Rendering Options

Each combination of the features above, used in your project results in generating a **shader variant** during the build process. To limit
the build time and the resulting binary size be careful not to add un-useful feature combinations. On the other hand, this mechanism makes
sure that only the used features are included in the build. More information on shader variants:
<https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html>
{: .notice--info}

![‘Stylized Surface’ shader collapsed view. Single mode. Simple use case](/FlatKit_Manual_Images/stylized-surface-1.png){:.image-fancy}

{:.image-caption}
‘Stylized Surface’ shader collapsed view. Single mode. Simple use case

![‘Stylized Surface’ shader in expanded view. Single mode. More complex use case](/FlatKit_Manual_Images/stylized-surface-2.png){:.image-fancy}

{:.image-caption}
‘Stylized Surface’ shader in expanded view. Single mode. More complex use case with more options engaged, but still, uses only Single mode

### The Main Parameters of the Shader

#### Color

This would be the color of your mesh (applicable to most cases, though you can make the shader's other parameters override or mask this main color, if you wish).

**NOTE.** The flatness and actual representation of colors on the scene depend on the source of lighting in the scene. In the _Lighting_ panel ▶︎ _Environment_ tab, if you select _Color_ as the source of lighting and set _Ambient Color_ to black, the colors you choose inside the materials will look identically to those represented on the scene.  
![](/FlatKit_Manual_Images/environment-lighting-color.png){:.image-simple}
{: .notice--info}

#### Cel Shading Mode

This is where you choose the style (mode) of your shading, the color of the shading and other parameters unique to the modes.

* **None.** Use this to achieve a simple flat look with the color picked in the _Color parameter_ above. If you'd like, you can still make the visuals look complex by adding _Extra Cel Layer_, _Specular_, _Rim_, _Outline_ etc (all described below), while being in _'None'_ _Cel Shading Mode_.

  ![](/FlatKit_Manual_Images/flat-kit-stylized-surface-shading-cel-mode-none.png){:.image-fancy}

  You can select _None_ mode and enable _Extra Cel Layer_ (described below) to get a similar effect to _Single_ mode.
  {: .notice--info}

* **Single.** This mode provides you with one cel layer of chosen color.

  ![](/FlatKit_Manual_Images/flat-kit-stylized-surface-shading-cel-mode-single.png){:.image-fancy}

  * **Color Shaded** is the color of the cel. It is not an HDR parameter.
  * **Self Shading Size** is the size of the cel. Larger values mean larger size of the shadow. 
  * **Shadow Edge Size** controls the sharpness of the cel. The lower the value — the sharper the cel. The higher the value — the more blurry is the shadow. 
  * **Localized Shading** is basically how condensed the shadow is. Higher values represent sharper cel.

* **Steps.** Basically, you choose the shading color and number of steps to blend from main *Color* into the color you pick up in *Steps* mode.
  
  ![](/FlatKit_Manual_Images/flat-kit-stylized-surface-shading-cel-mode-steps.png){:.image-fancy}
  
  * **Color Shaded** is the color of the cel you'd like to blend to. It is not an HDR parameter.
  * **Number of Steps** is the number of steps to blend from main *Color* into the color you pick up in *Color Shaded* parameter.
  * **Save Ramp Texture** is a button to save the texture of the gradient. This is useful if you'd like to use the same gradient in other shaders. The texture will appear red in the editor. This is because internally we use the R8 texture format for efficiency.

    After you click the _Save Ramp Texture_ button, you'll see the prompt to choose where in the project folder you'd like the texture to be saved. You can use it in other materials and shaders.

    The texture will appear in the _Cel steps_ parameter.

    ![](/FlatKit_Manual_Images/flat-kit-stylized-surface-steps-mode.png){:.image-fancy}

    {:.image-caption}
    *Steps* shading mode of Stylized Surface shader


* **Curve.** The gradient, interpolated transition from main *Color* to *Color shaded*.

  ![](/FlatKit_Manual_Images/flat-kit-stylized-surface-shading-cel-mode-curve.png){:.image-fancy}

In order to get Steps and Curve modes to work — as soon as you have a number of steps (*Steps* mode) or curve shape (*Curve* mode) chosen — the shader will ask you to save its utility ramp texture somewhere on the disk. It will write the transition onto it. The texture will appear red in the editor. This is because internally we use the R8 texture format for efficiency.

  * **Color Shaded** is the color of the cel you'd like to blend to. It is not an HDR parameter.
  * **Save Ramp Texture** is a button to save the texture of the gradient. This is useful if you'd like to use the same gradient in other shaders. The texture will appear red in the editor. This is because internally we use the R8 texture format for efficiency.
  * **Shading curve** is the curve of the gradient. You can edit it by clicking on the curve and dragging the points. You can also add new points by clicking on the curve. You can remove points by clicking on them and pressing the _Delete_ button on your keyboard.

    ![](/FlatKit_Manual_Images/flat-kit-stylized-surface-curve-editor.png){:.image-fancy}

    {:.image-caption}
    *Curve Editor* appears when you click on the curve

    After you click the _Save Ramp Texture_ button, you'll see the prompt to choose where in the project folder you'd like the texture to be saved. You can use it in other materials and shaders.

    The texture will appear in the _Ramp_ parameter.

    ![](/FlatKit_Manual_Images/flat-kit-stylized-surface-curve-mode.png){:.image-fancy}

    {:.image-caption}
    *Curve* shading mode of Stylized Surface shader



![](/FlatKit_Manual_Images/stylized_surface_edge_size_flat_smooth.gif){:.image-fancy}
Please note that the models you are working with can be either flat-shaded or smooth-shaded or in a 3D editor (e.g., here is the [reference](https://docs.blender.org/manual/en/4.2/modeling/meshes/editing/face/shading.html) in Blender). If you have a model with smooth-shaded normals, the cel shading will be smooth as well in Unity. If you have a model with flat shading, the cel shading will appear blocky. But you can adjust smoothing in Unity as well — in the _Import Settings_ of the model -→ _Normals_ section.
{: .notice--info}

#### Extra Cel Layer

This is like another instance of *Single* mode of *Cel Shading Mode*. Works independently from the *'Single'* *Cel Shading Mode*. This means, you can set _Cel Shading Mode_ to *None* (flat), and add an *Extra Cel Layer*. The result will be the same as if you would have used the *Single mode*. 
Or choose the *'Single' Cel Shading Mode* and make *Extra Cel Layer* almost identical to it, giving an *Extra Cel Layer* a darker color, and making it smaller. This would result in stepping, similar to _Steps Mode_ with 1 step. Classic toon.


#### Specular

You can make a, well, specular (glare) with this parameter. Also it can be used as another layer of shadow.

* **Specular Color** picks up the color of your glare, the parameter works in HDR.
* **Specular Size** determines how big the specular is. Higher values mean bigger specular.
* **Specular Edge Smoothness** — moving slider to the left decreases blurriness and makes specular sharper.

![Specular. Inspector interface](/FlatKit_Manual_Images/specular_parameters.png){:.image-fancy}

{:.image-caption}
*Specular*. Inspector interface

#### Rim

Rim was designed as one of the ways to make a specific effect of a color 'wrapping' from behind the object (a fresnel effect, in a nutshell). In some cases it can remind an outline effect.

Please, note that the object has to have curvature. A completely flat object wil be completely included in the rim or completely not included, depending on the angle of view.
{: .notice--warning}

* **Rim Color** selects the color of the parameter. It works in HDR.
* **Light Align** parameter rotates the rim.
* **Rim Size** controls how big the Rim is. Very high values can serve you as an unlit effect.
* **Rim Edge Smoothness** — moving slider to the left sharpens the Rim, to the right — makes Rim blurry.

![Rim. Inspector interface](/FlatKit_Manual_Images/rim_parameters.png){:.image-fancy}

{:.image-caption}
*Rim*. Inspector interface

You can think of Rim as some kind of inner shadow and/or as inner glow, if used on smoothened curvy models. In one of the *Fruit Vase* demo scenes, there is an example of extensive use of Rim as an outline. On *Blueprint Grid* demo scene *Rim* is used as a smooth inner glow. This parameter can be used creatively, for example, to substitute *Curve mode* or *Extra Cel parameter*. **Just reminding you that the name like 'Rim', 'Specular' etc should not be perceived literally, they can do more than that.** In the screenshot below, with the help of Suzanne the Blender Monkey, we tried to show a few instances of *Stylized Surface* shader with *None* mode selected (meaning no straightforward shadows are applied), using orange color, and only *Rim* parameter enabled. The results are variations of Rim section only. As you see, the *Rim* alone is quite a creative tool. Imagine adding some creative *Specular* and *Height Gradient*...

![Rim only, usage examples](/FlatKit_Manual_Images/rim_examples_suzanne.png){:.image-fancy}

{:.image-caption}
Variety of uses of *Rim* parameter alone on Suzanne the Blender Monkey. Interface of *Stylized Surface* shader with *‘None’* cel shading mode

Although *Rim* option is creatively useful and sometimes can remind an outline effect, there are two more obvious ways to add an outline using Flat Kit: to use [Stylized Surface with Outline](#stylized-surface-with-outline-shader) shader and/or to use [Outline Image Effect](/image-effects/#outline-image-effect) camera component in Built-In RP/Forward Renderer's Renderer Feature in URP. We’ll talk about both of them later in this manual.

**TIP.** Animate Cel layer size, Specular size or Rim size — to get a neat transition effect.
{:.notice--success}

#### Height Gradient

This effect overlays a gradient from opaque selected color to transparent color onto everything you’ve set before. Height Gradient is global (absolute) per material, it doesn't depend on object's boundaries. If you would like to make a relative gradient (for instance, each object holding one material to contain an entire gradient within itself), duplicate the material and adjust the height gradient. Alternatively, you can use a [Curve mode](/stylized-surface/#cel-shading-mode/) of *Stylized Surface shader*.

![Height Gradient. Inspector interface](/FlatKit_Manual_Images/gradient_height_parameters.png){:.image-fancy}

{:.image-caption}
*Height Gradient.* Inspector interface

* **Gradient Color** picks the parameter’s own color to fade into from transparency.
* **Center X** and **Y** are initial points from where the effect takes effect. Adjust these to move the gradient across the scene. Center X is useful if you engage - *Gradient Angle*, which means the rotation of the Gradient.
* **Size** determines how steep the transition of Gradient is. The further the value is from 0 (zero) — the more gradual the effect is. Negative values flip the Gradient.
* **Gradient Angle** rotates the gradient.

A bit more about the nature and use of *Height Gradient* is covered in the [Terrain Shader](/terrain/) chapter.

#### Enable Vertex Colors

If enabled, the final shading of the object is multiplied by the vertex color values of the mesh. It is a debug parameter, usually this is not used for changing the look.

#### Outline

<!-- In the recent update we made some changes to the _Stylized Surface_ shader responsible for the outlines generation. Now, the shader-based _Outline_ doesn't break the SRP batching and is more performant.
{: .notice--success}
-->

![Outline part of Stylized Surface shader. Inspector interface](/FlatKit_Manual_Images/stylized-surface-outline-interface.png){:.image-fancy}

{:.image-caption}
*Outline* part of Stylized Surface shader. Inspector interface

The *Outline* part of the *Stylized Surface* shader allows you to add pseudo-outlines to your models.

* **Width** determines how thick the outline is.
* **Color** picks up the color of the outline.
* **Scale** adjust this parameter when you have gaps on the vertices (please note, this is not an ultimate solution, the gaps need a complex approach — in modelling, adjusting the normals, adjusting camera distance etc).
* **Smooth Normals** softens the normals of the model. This is useful when you have gaps on the vertices.
* **Depth Offset** moves the outline inwards or outwards an object.
* **Space** determines the space in which the outline is rendered. The options are: _Object_, _Screen_.
  * **Camera Distance Impact** **(this parameter is available in Universal RP only)** if **Space** is set to _Screen_, this parameter appears. It makes outlines that are further from camera appear thinner than outlines closer to the camera.

Please remember that in addition to this shader Flat Kit has also a global *Outline image effect* applied per Renderer (in URP) and per camera (in Built-In RP).
In the [Outline Image Effect](/outline/) chapter in this manual you can find some useful specific and general info.
{: .notice--info}

In some cases it may be useful to manipulate the normals of your model in order to force the shader to render outlines where it wouldn't do so otherwise.
More on this is covered in [Outline Image Effect](/outline/) chapter. But here's one thing you can try without using 3d editor software. Among the other parameters of the import settings of the model, there is a section where is it possible to change the angle detection threshold for normals smoothing. It may come handy in adding or removing some of the outlines where they wouldn't appear normally. Also, slight adjustments to these parameters may resolve some of the visual issues such as outline gaps on the edges. If you have such breaks in the outline, for instance, try tweaking these controls (but remember to backup the project first, it's always a good idea to backup things. In fact, if you are working on something, do it now).

[![Gaps are visible on hard edges](/FlatKit_Manual_Images/outline-gaps-suzanne-1.png){: .image-fancy }](/FlatKit_Manual_Images/outline-gaps-suzanne-1.png)

{:.image-caption}
Gaps are visible on hard edges

So, here are two easy ways to get rid of the outline gaps:

- **Method #1** Select a mesh in the scene that carries the Stylized Surface material with the _Outline_ parameter turned on. Then turn on the **Smooth Normals** parameter in the Inspector panel. 

Important! If the _Smooth Normals_ parameter had already been turned on without the mesh being selected, you'll need to turn it off and then on again, while the mesh is selected. This is because the mesh needs processing, not the material, in order for the _Smooth Normals_ parameter to work.
{: .notice--warning}

[![Smooth Normals parameter](/FlatKit_Manual_Images/styl-surf-outline-smooth-normals.png){: .image-fancy }](/FlatKit_Manual_Images/styl-surf-outline-smooth-normals.png)

{:.image-caption}
Smooth Normals in the Outline section of Stylized Surface shader


- **Method #2** In the Import Settings of the mesh, please, find the _Normals_ parameter and change it from **Import** to **Calculate**. Then, drag the _Smoothing Angle_ slider to the right. By doing so, you make the mesh smooth instead of sharp. The more you move this control to the right the bigger angle Unity will expect to consider it as sharp. Click _Apply_. The gaps should be gone.

[![Stylized Surface Outline on mesh with smoothened normals](/FlatKit_Manual_Images/outline-gaps-suzanne-2.png){: .image-fancy }](/FlatKit_Manual_Images/outline-gaps-suzanne-2.png)

{:.image-caption}
No gaps, Stylized Surface Outline on mesh with smoothened normals

As an extra step, to clean up the result a bit, you go to the material and increase _Depth Offset_ a bit. This will 'push' the outlines away from the camera.

[![Depth Offset parameter](/FlatKit_Manual_Images/outline-gaps-suzanne-3.png){: .image-fancy }](/FlatKit_Manual_Images/outline-gaps-suzanne-3.png)

{:.image-caption}
Using the _Depth Offset_ parameter on the _Stylized Surface_ shader to clean up the result

Please note that this way of doing the outlines is made to be super fast, but unlike in Photoshop it can't produce an ideal outline. This method is called **Inverted hull**, when the vertices of a model are moved along their normals in the image space. There are fundamental limitations to this fast approach of making the outline. For example, the outline itself in not a hollow contour — but rather the modified normals layered on the back of the original model. In most cases it can produce very good results with very fast performance, but the transparency on this model won't work, as reducing the model's opacity will reveal the filled pseudo-outline layer in the background.
{: .notice--warning}

Also, to remedy the gaps issue, you can try using the [Scale parameter](/stylized-surface/#the-outline-part-of-the-stylized-surface-shader-allows-you-to-ad/) of the Outline parameter. By keeping the **Width** low and increasing the **Scale** you can get rid of the gaps. But this is not a perfect solution, as it may make the outline look a bit displaced.
{: .notice--success}

### The Additional Parameters of the Shader

#### Advanced Lighting

**Light Color Contribution.** Light Color Contribution defines how much the color of the light source of the scene impacts the color of the object. The value of 0.0 results in completely ignoring scene lights, the value of 1.0 results in full multiplication between scene light color and the object color. As an example, imagine the winter morning light. Usually it is blue-tinted, thus all the snow around can’t be white but rather blueish.

Please note that the effect is visible only if the color of the light is anything but white.

Light Color Contribution works only with directional light. The point and spot lights are contributing to colors and shading of the material regardless of the Light Color Contribution value.

![Light Color Contribution parameter on Flat Kit shaders Inspector panel](/FlatKit_Manual_Images/light_color_contribution.png){:.image-fancy}

{:.image-caption}
*Light Color Contribution* parameter on Flat Kit shaders Inspector panel

Let’s view it in example.
Three pictures below describe how we change Light Color Contribution values on all (two) used materials: on a sphere and on a plane. Within a picture we change the intensity value of Directional Light as our main source of light.
Additionally, there is a point light on each picture. This way it’s visible how local lights work together with the main Directional Light.
Take the first image (below). At first, we turn down the *Intensity* to the very low value. White sun now has no impact on the scene brightness, resulting in a darker scene.
Then we change the color of Directional Light from white to red. It has no effect because Directional Light is too “weak” to fill the scene.
After raising *Intensity* value back to “1” the scene is now lighter and has a red tint.

[![Light Color Contribution at value 0.5. Changing intensity value and color of Directional Light](/FlatKit_Manual_Images/lighting_2_color_contrib_0.5.png){: .image-fancy }](/FlatKit_Manual_Images/lighting_2_color_contrib_0.5.png)

{:.image-caption}
*Light Color Contribution* at value 0.5. Changing *Intensity* value and color of Directional Light

Once we change *Color Light Contribution* parameter to “0” (pic below), Directional light has no effect light-wise and color-wise. Changing *Intensity* parameter of Directional Light on the Inspector panel has no effect. Both sides of the picture are identical.
This way you can achieve a flat look, in other words, the colors on the scene are exactly the same as you choose in the shader parameters.

[![Light Color Contribution at value 0. Directional Light intensity at max and min values](/FlatKit_Manual_Images/lighting_1_color_contrib_0.png){: .image-fancy }](/FlatKit_Manual_Images/lighting_1_color_contrib_0.png)

{:.image-caption}
*Light Color Contribution* at value 0. Directional Light *Intensity* at max and min values

Now, (on the pic below) we raise *Light Color Contribution* to the max value of “1”. If we set Directional Light *Intensity* parameter low, the scene theoretically has no source of direct light. Local lights now act as the only light sources. If the *Intensity* of Directional Light is at its maximum, it’s too hot now.

[![Light Color Contribution at value 1. Changing intensity value of Directional Light](/FlatKit_Manual_Images/lighting_8.png){: .image-fancy }](/FlatKit_Manual_Images/lighting_8.png)

{:.image-caption}
*Light Color Contribution* at value 1. Changing *Intensity* value of Directional Light

If you use a Particle System and choose your particles to emit light, Flat Kit shaders respect that!

![Particles emitting light on Flat Kit shaders](/FlatKit_Manual_Images/lighting_particles_lights.png){:.image-fancy}

{:.image-caption}
Particles emitting light on Flat Kit shaders

**Override light direction** It is a way to make the material have an independent direction of the light from the Directional Light. This can be useful in cases when you need to align the position of the cels or Rim or Specular. Normally, to adjust these parameters globally, you should rotate the Directional light. Once *Override light direction* parameter is enabled, the material no longer obeys the Directional Light, it now has independent mapping vectors for the light-dependent parameters (e.g. mentioned earlier cels, Rim, Specular) that you can adjust with *Pitch* and *Yaw* parameters. Simply put, you can rotate the the cels, Rim and Specular.

#### Unity Built-in Shadows

If the object has the ‘Receive Shadows’ option turned on in Mesh Renderer, you have an ability to use Unity-processed shadows on it, as you would do in Unity Standard Material shader, with a few extra-options.

![Unity Built-in Shadows mode menu. Inspector interface](/FlatKit_Manual_Images/unity_built_in_shadows_modes.png){:.image-fancy}

{:.image-caption}
Unity Built-in Shadows mode menu. Inspector interface

* **Mode** lets you choose the coloring and blending parameters for the built-in shadows. 
  * **None** mode turns the built-in shadow parameter off.
  * **Multiply** mode lets you cast the shadows as in default material. You don’t have direct control over the color. You can change intensity and sharpness. The blending mode is 'Multiply'. 
  * **Color** mode lets you choose the color of the cast shadow. The blending mode is 'Normal'. The opacity of the shadow is controlled by the alpha parameter in the color chooser.
<!-- * **Power** sets how visible the Unity built-in shadow is. -->
* **Sharpness** defines how blurred or crisp the shadow edge is.
* **Shadow Occlusion** masks received Unity shadows in areas where normals face away from the light. **Useful to remove shadows that 'go through' objects.**

**NOTE.** *Shadow Occlusion* parameter is available in the URP version of Flat Kit only.
{: .notice--warning}

![Unity Built-in Shadows in Color mode. Inspector interface](/FlatKit_Manual_Images/unity_built_in_shadows_mode_color_parameters.png){:.image-fancy}

{:.image-caption}
*Unity Built-in Shadows* in *Color* mode. Inspector interface

#### Texture Maps

If you’ve got a UV-unwrapped mesh, you can add a set of textures to it. The shader supports Albedo, Detail, Normal and Emission maps.

If you work with transparency in textures in Built-In RP, please use *Stylized Shader Cutout* shader. It can use alpha on the texture as transparency. URP supports alpha by default.
{: .notice--warning}


![A set of textures in Stylized Surface shader](/FlatKit_Manual_Images/flat-kit-stylized-surface-textures.png){:.image-fancy}

{:.image-caption}
A set of textures in Stylized Surface shader

**Albedo** Allows to use the albedo, or diffuse texture. In URP this slot supports transparent textures by default. Can be used together with *Alpha Clipping* parameter (explained below).

* **Texture selection slot** lets you pick a texture;
* **Blending Mode** lets you choose between 'Multiply' or 'Add' blending modes. 'Multiply' Blending Mode multiplies the luminosity of the base color by the blend color. Multiplication by white produces no change, while the black pixels remain, making the material darker. 'Add' Blending Mode is a little bit different from 'Multiply' — blending with black color produces no change, while generally it brightens the bright colors.
* **Texture Impact** controls how visible the texture is. Values to the left decrease visibility of the texture up until it is invisible.

**TIP.** If you would like to have a material with a texture with a cel shading on top of this texture, you can set the *Stylized Surface* to *Single* **Cel Shading Mode**, set the base **Color** to white or light grey, set the  **Color Shaded** parameter to a bit darker one, set the Albedo texture (if your texture is not mostly white) to *Multiply* **Blending mode**, Texture Impact to the maximum value. You should get the model filled with a texture and with cel shadows combined.
{:.notice--success}

**Detail** Allows to use a second albedo texture. It is blended with the first one. The blending modes are: _Multiply_, _Add_, _Interpolate_.

* **Texture selection slot** lets you pick a texture;
* **Detail Color** picks the color of the second texture;
* **Blending Mode** lets you choose between 'Multiply', 'Add' or 'Interpolate' blending modes;
* **Detail Impact** controls how visible the second texture is. Values to the left decrease visibility of the texture up until it is invisible.

**Normal Map** To make an impression of a relatively low-poly mesh having many details of a high-poly one, you can use normal maps. Add one to *Normal Map* slot in the Inspector panel.

<!--
![‘Stylized Surface’ shader — normal map applied](/FlatKit_Manual_Images/normalmap-interface.png){:.image-fancy}

{:.image-caption}
‘Stylized Surface’ shader — normal map applied
-->

* **Texture selection slot** lets you pick a texture;


![‘Normal Map Tree’ demo scene, a tree without and with a normal map](/FlatKit_Manual_Images/normalmap-trees.png){:.image-fancy}

{:.image-caption}
[Normal Map Tree](/demo-scenes/#normal-map-tree/) Demo scene, a tree without and with a normal map

**Emission** Enables Emission map part of the shader.

**NOTE.** Emission map support is available in Universal RP version of Flat Kit only, there is no Emission map parameter in Built-In version of Flat Kit.
{: .notice--warning}

**Emission Map** Allows to use custom emission maps to designate the parts of the meshes to have a 'glow' effect.

* **Texture selection slot** lets you pick a texture;
* **Emission Color** chooses the color of the 'glowing' effect.

<!--
![Emission map part of the Stylized Surface interface](/FlatKit_Manual_Images/stylized-surface-emission-interface.png){:.image-fancy}

{:.image-caption}
Emission map part of the Stylized Surface interface
-->

The _tiling_ and _offset_ parameters apply for all the textures simultaneously.
* **Tiling** repeats the texture along X and Y axis;
* **Offset** shifts the texture along X and Y axis within the UV map of the mesh;

#### Rendering options

This section is available in the Universal RP of Unity. Built-In RP doesn't have alpha clipping on the shader level, so you can use the [*Stylized Shader Cutout*](/stylized-surface/#stylized-surface-cutout-shader/) shader instead.
{: .notice--warning}

![](/FlatKit_Manual_Images/flat-kit-stylized-surface-rendering-options-parameters.png){:.image-fancy}

Rendering options part of the Stylized Surface interface
{:.image-caption}

* **Surface Type** — The two options are _Opaque_ and _Transparent_.
  * **Blend Mode** — If **Transparent** _Surface Type_ is selected, the Blend Mode menu becomes available with the following Blend Mode options: Alpha, Premultiply, Additive and Multiply.
* **Sorting Priority** — determines the chronological order of rendering for the Material. Materials with lower value are rendered first.
* **Render Faces** — lets you choose between Front, Back or Both faces of the mesh to be rendered.
* **Alpha Clipping** — Discards pixels based on the Albedo texture’s alpha channel. If enabled, the _Threshold_ parameter appears.
  * **Threshold** — The minimum alpha in the Albedo texture to render a pixel, i.e. determines how soon the transparent portion is ‘transparent enough’ to be cut out.
* **Enable GPU Instancing** — Uses GPU Instancing to render multiple copies of the mesh at once. More information in [Unity’s documentation](https://docs.unity3d.com/Manual/GPUInstancing.html) and in this doc [here](/stylized-surface/#gpu-instancing).

### Setting material values from scripts

The following are the color field names for manipulation via the code for tweening, randomization etc:

* `_BaseColor` (in URP), `_Color` (in Built-in RP): the primary color, “Color” in the inspector. The alpha value controls transparency of the object if `Surface Type` is set to `Transparent`
* `_ColorDim` (and `_ColorDimSteps`, `_ColorDimCurve` in the corresponding cel shading modes): Color Shaded in the Inspector
* `_ColorDimExtra`: the shaded color of the *“Extra Cel Layer”* feature
* `_FlatRimColor`: rim color, requires *“Enable Rim Color”*
* `_FlatSpecularColor`: specular color, requires *“Enable Specular Color”*
* `_ColorGradient`: the gradient color used along with the `_BaseColor` parameter when *“Enable Height Color”* feature is active
* The full list of parameters is at the top of the file `Assets/FlatKit/Shaders/StylizedSurface/StylizedSurface.shader`.

**NOTE.** The outline toggle is implemented as a [shader keyword](https://docs.unity3d.com/Manual/shader-keywords.html), so unfortunately it can't be toggled at runtime. However, you can enable the outline in the material inspector and toggle its visibility in code by setting the outline width (0 will visually disable the outline). Or, you can create two identical materials with the only difference being the outline toggle, and switch between these materials at runtime with `renderer.material = myMaterial`.
{: .notice}

## Stylized Surface Cutout Shader

**NOTE:** '*Stylized Surface Cutout*' shader has been deprecated in Flat Kit 2.1.2 for Universal RP version ('*Stylized Surface Cutout*' is still available in Built-In RP version). Because URP supports transparency by default, there's no need for this separate shader in URP.
The *Stylized Surface* and *Stylized Surface with Outline* shaders can do everything *Stylized Surface Cutout* could — using [*Rendering options*](/stylized-surface/#rendering-options/) part of the shaders in the bottom of the interface. There you can find an option to set the shading in transparency mode (*Surface Type* drop down menu ▶︎ *Transparent*. The default type is *Opaque*).
![](/FlatKit_Manual_Images/flat-kit-stylized-surface-surface-type-dropdown.png)
{: .notice--warning}

This is a version of *Stylized Surface* shader with an option to treat alpha as transparency on a texture. The rest of the shader is the same.

The *Base Alpha cutout* parameter determines how much of the alpha portion of the texture is going to be transparent.

![‘Stylized Surface Cutout’ shader — Valley demo scene, tree branches material. Inspector interface](/FlatKit_Manual_Images/stylized_surface_cutout_screenshot.png){:.image-fancy}

{:.image-caption}
‘Stylized Surface Cutout’ shader — Valley demo scene, tree branches material. Inspector interface

Use this shader if you work with transparency in Built-In RP. In URP you are good to go with the *Stylized Surface* shader instead of this one. It will spare a few cycles from your CPU.

## Stylized Surface with Outline Shader

**NOTE:** *Stylized Surface with Outline* shader has been deprecated in Universal RP version of Flat Kit: the outline functionality has been moved to the [Outline parameters](/stylized-surface/#outline/) of *Stylized Surface* shader. *Stylized Surface with Outline* remains available and working for the sake of compatibility with existing projects, but it is advised to use *Stylized Surface* for the new projects instead. *Stylized Surface with Outline* has not been deprecated in Built-In LTS version of Flat Kit.
{: .notice--warning}

You can use [*Stylized Surface*](/stylized-surface/#outline) shader to outline a particular object. It is a parameter (shader pass) that is built on top of the *Stylized Surface* shader. It has all the features of the *Stylized Surface* shader plus the outline feature.
{: .notice--info}

![‘Stylized Surface with Outline’ shader](/FlatKit_Manual_Images/stylized_surface_with_outline_interface.png){:.image-fancy}

{:.image-caption}
‘Stylized Surface with Outline’ shader

* **Color** picks up the color of the outline.
* **Width** determines how thick the outline is.
* **Scale** adjust this parameter when you have gaps on the vertices (please note, this is not an ultimate solution, the gaps need a complex approach — in modelling, adjusting the normals, adjusting camera distance etc).
* **Depth Offset** moves the outline inwards or outwards an object.
* **Camera Distance Impact** **(this parameter is available in Universal RP only)** makes outlines that are further from camera appear thinner than outlines closer to the camera.

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
