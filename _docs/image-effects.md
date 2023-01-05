---
title: "Image Effects"
permalink: /image-effects/
excerpt: "Image Effects"
toc: true
---

Both *Fog* and *Outline* image effects rely on image-based anti-aliasing, like the one in Unity's Post-processing stack.

* In Universal RP (URP) — post-processing effects are called ‘Renderer Features’ of the Forward Renderer.
* In Built-In RP: Post-processing is made of Camera effects placed onto the camera in the scene as Components.
  
## Fog Image Effect

Fog Image Effect camera component can be reviewed as a post-processing effect. It can be subtle, like a mist in the lower part of the valley, or a dominant effect, as in a completely hazed environment. Simply put, it works in the following way. You decide whether you need only length fog or height fog or both. Then you determine the bounds where it would take effect. Then you choose colors along each dimension. And after that, blend between distance and height. This effect starts from camera position up to the Near/Far, Low/High bounds, meaning, your camera is the zero coordinate from where the fog spreads. Each camera on the scene can have a separate independent instance of an effect.

Because Unity’s MSAA (multi-sample anti-aliasing, which is an option in the Quality Settings of your project) does not apply to depth texture, there may be inconsistencies between the anti-aliased color image and the unprocessed depth image. This may look as aliasing if fog intensity is set to a high value. *Such artefacts may only occur if using MSAA*, so we recommend using screen-space anti-aliasing, such as in Unity’s post-processing stack that you can import by going to Window ▶︎ Package Manager in Unity 2018+.

When you click on any of the color ramps (Distance or Height Gradient), the Gradient Editor pops up.

Fog Image Effect is being used in the *Wanderer* demo scene (more subtly) and *Valley* Demo scene (more accentuated).

![Fog Image Effect. Inspector panel interface](FlatKit_Manual_Images/fog_image_effect.png)
> Fog Image Effect. Inspector panel interface

Gradient editor controls the colors of the gradient. To open it, click on Distance Gradient or Height Gradient. The bottom row of breakpoints (pointing up) is the selection of the colors. The above row (pointing down) controls the opacity of the area it points at; the opacity value of one breakpoint fades into the opacity value of the adjacent one. Same for colors.

> **TIP.** If you want the area close to you to be without fog, apart from increasing Near parameter, you can open up the color ramp(s), add a breakpoint next to the leftmost one on the ramp, select leftmost one, make it transparent (see screenshot of Gradient Editor below). The breakpoint you created (opaque, next to the transparent one) becomes your distance or height control.

![Fog Image Effect. Gradient Editor interface.](FlatKit_Manual_Images/fog_image_effect_gradient_editor.png)
> Fog Image Effect. Gradient Editor interface.

## Outline Image Effect

Outline Image effect is, essentially, a contour on the objects on the scene. It can draw outer outlines, inner ones or both outer and inner outlines of the objects.

![Outline Forward Renderer in URP. Inspector interface.](FlatKit_Manual_Images/outline-image-effect-interface.png)
> Outline Forward Renderer in URP. Inspector interface.

### Setting up Flat Kit Outline (URP)

If you are working in a Universal Rendering Pipeline (URP) project, the post processing components you used to put on the camera in the old Built-In RP ('Standard', '3D' project) — they are called 'Renderer Features' in URP and can be found in the settings of the Forward Renderer.  

Please make sure that you installed Flat Kit properly as described [in this manual above](/quick-start).  

After that you'll be able to load, for example, *Wanderer* demo scene that comes with Flat Kit, launch the scene (press Play) and see the outlines displayed.  

To be able to use Flat Kit's Outline in your own scene, you can either go from scratch:  

1. Create a new **Forward Renderer**. To avoid further confusion, name it, for example, *MyNewAwesomeForwardRenderer*. (Go to Assets menu on top ▶︎ Create ▶︎ Rendering Universal Rendering Pipeline ▶︎ Forward Renderer).
2. Add it to the **Renderer List** of the **[Flat Kit] Example Settings URP** file in the Inspector panel. To do this, go to **Project panel ▶︎ Flat Kit ▶︎ ExampleSettings ▶︎ [FlatKit] Example Settings URP**. Select it, look at the Inspector panel, see the **Renderer List** section, press **'+'** button and drag *MyNewAwesomeForwardRenderer* Forward Renderer you created in step 1 — into the created line of the **Renderer List**.  
3. Select that newly created *MyNewAwesomeForwardRenderer* Forward Renderer, press **'Add Renderer Feature'** and Select **Flat Kit Outline**. This will add the Outline Renderer feature. But to be able to adjust parameters, like width, color of the outlines, you'll need to create the Outline Settings file.  
4. Go **Assets menu on top ▶︎ Create ▶︎ FlatKit ▶︎ Outline Settings**. This creates an Outline settings file. Name it *MyNewOutlinesSettings*.  
5. Add this *'MyNewOutlinesSettings'* settings file to **Flat Kit Outline** Renderer Feature you created in step 3 — into the **Settings** field.  
6. In your scene select the camera (Main Camera) in Hierarchy panel, look at Inspector panel, find **Rendering** section and in the **Renderer** drop down menu select *MyNewAwesomeForwardRenderer* Forward Renderer you created in step 1.  
7. You may need to launch the scene by pressing Play.  

Or, you can do it the easy way.  

1. In your scene select the camera (Main Camera) in Hierarchy panel, look at Inspector panel, find **Rendering** section and in the **Renderer** drop down menu select *[FlatKit] Wanderer-ForwardRenderer* or *[FlatKit] FruitVaseScene-Var-ForwardRenderer*. They both have outlines already engaged.  
2. You may need to press Play.  

To change the parameters of the outlines then, please:

* Press *Ctrl + F (Windows)* or *Cmd + F (macOS)* and type *[FlatKit] Wanderer-Var-OutlineSettings* in the search field that becomes active in Project Panel. Select the found file and change the parameters in the Inspector panel.

### Parameters of Flat Kit Outline

**Main settings** are the following.

* *Edge Color* lets you choose the color of the outline.  
* *Thickness* makes the outline thicker or thinner. It controls how wide or narrow the line of the outline is.
* *Resolution Invariant* if enabled, the line width will stay constant regardless of the rendering resolution. However, some of the lines may appear blurry.  
* *Use Depth* enables or disables taking the scene's depth data into calculating the outlines. This parameter outlines the outer contour of the objects with depth threshold control.  
* *Use Normals* creates outlines for “inner” parts of the objects, meaning, for those that are inside the boundaries of the object, for every given camera perspective. The effect depends on the geometry of an object. So, having proper normals here is important. There is a Normals Threshold control. It's discussed a bit more a little further down.  
* *Use Color* enables or disables taking all color difference data on the scene when calculating the outlines. This feature is URP only.

**NOTE:** If you see that *Use Depth* and *Use Normals* have no effect in your project, please navigate to Project Settings -> Graphics and insert **[FlatKit] Example Settings URP** file into *Scriptable Rendering Pipeline Setting* field. If you are using your own settings file instead, please make sure to have *Opaque texture* and *Depth texture* checkboxes on, which can be found on Inspector tab when you select that URP settings file.

**Advanced settings** section hosts the parameters to adjust the tools above as well as a few more controls. The thresholds parameters are basically the limits that determine the ranges in which the effects take places. For example, the higher Min Depth value is, the further away from camera the outline will be generated. The lower Max Depth value is, the sooner outlines stop occurring.  

* *Min Depth Threshold* and *Max Depth Threshold* determine the range of depth differences where outline should be applied. Lower values draw lines “inside” the scene resulting in a more beveled image. Higher values have more flat effect.  
* *Min Normals Threshold* and *Max Normals Threshold* determine the range of normals edges to be outlined. Lower values increase the amount of affected normals, leading to more stroked effect. Higher values decrease the amount of affected normals, leading to flatter look. Basically, it determines min and max angles of the normals for the outlines to occur.  
* *Min* and *Max Color Thresholds* let you set the least and the strongest differences in color of the mesh to make the outline appear. This feature is URP only.  
* *Outline Only* renders the outlines without meshes themselves, making it a kind of wireframe renderer. This feature is URP only.
* *Render Event* This is one quite powerful feature available on the interface. It lets you choose a stage at which the outlines are applied. It allows to apply outlines over the transparent objects. If you want to exclude transparent objects like Water or UI elements, set this to 'Before Transparent'. Also, it allows you to stack the *Outline Image Effect* with other post effects. This feature is URP only.

You'll need to *press 'Play'* to see the effect of *Render Event*.

![Outline Image Effect Render Event list](FlatKit_Manual_Images/outline-image-effect-render-events.png)
> Outline Image Effect Render Event list

Here is an example of choosing when to render the outlines. We took *Wanderer* demo scene and applied an example *Outline* Image Effect. After that we tried a few different items from the *Render Event* list.

!['After Rendering Skybox' chosen in Render Event list](FlatKit_Manual_Images/after_rendering_skybox.png)
> *'After Rendering Skybox'* chosen in Render Event list. *Wanderer* demo scene

!['Before Rendering Post Processing' chosen in Render Event list, 'Outlines Only' parameter ticked](FlatKit_Manual_Images/before_rendering_post_processing_outlines_only.png)
> *'Before Rendering Post Processing'* chosen in *Render Event* list, *'Outlines Only'* parameter ticked

Also, in URP you have an ability to chain and change the orders of Image effects, but it's a general Unity information. More info in the chapter [Flat Kit Image Effects in URP](/flat-kit-in-urp/#flat-kit-image-effects-in-urp)

Please note that *Outline Image Effect* is a global effect, as it is used as the camera component in Built-In RP and as a scene's Renderer Feature in URP, which is suitable for a consistent look of your project. If you would like to outline a particular object on your scene, you can engage the shader instead — [Stylized Surface with Outline](/shaders/stylized-surface-with-outline-shader) shader.

If you would like to exclude an object from an outline pass, considering that you are using one of the Stylized Surface shaders, and you are in a URP project, please go to the interface of the shader and switch rendering to 'Transparent'. It won't change the look of the shader but will exclude it from the outline pass. You can control this too as described a few paragraphs above in Render Event list part.

![Flat Kit Depth Normals renderer feature](FlatKit_Manual_Images/flat-kit-depth-normals.png)
> Flat Kit Depth Normals Renderer Feature

> **NOTE:** The *Flat Kit Depth Normals* is no longer needed starting Unity 2021.1 and will soon be removed.

Some general info. Manipulating the normals of the mesh can be a very efficient way to control the behavior of the outlines. It can be done in a 3d editor. For example, here's how to do it in Blender.

![Rotating normals in Blender](FlatKit_Manual_Images/normals-rotation1.png)
> Rotating normals in Blender. Manipulating the normals angle is one of the ways to make Flat Kit generate outlines where you want them

> **TIP:** Combinations of the settings in Outline Image Effect let you control the behavior of the outlines quite widely already. You can get even more control on the outlines using *‘Stylized Surface with Outline’* shader in addition to the global Outline effect. Also, *Rim* parameter of *Stylized Surface* and *Stylized Surface with Outline* shaders can accentuate object's edges, often it looks like a partial outline, which can be helpful.

> **TIP:** One of the commonly asked questions is if some of the objects can be rendered without the Outline Renderer Feature applied. Outline image effect is global and is not designed to be selective to objects — it is applied per Renderer (in URP). However, moving object to be rendered in the transparent pass can solve this problem. In Flat Kit Stylized Surface there is such an option. If you are using non-Flat Kit shaders, please refer to their documentation to see whether it is possible — to enable transparency without affecting the look. In Flat Kit there is an option of Render Event. It lets you choose when to render the lines. Take a look at [this chapter](#outline-image-effect) in our manual.  
Another way of excluding something from rendering outlines on — is to render it with a separate camera in a camera stack: one camera is for non-outlined objects and another one is for everything else (outlined). Please refer to Unity documentation on camera stacking to get to know more about this general Unity technique.