---
title: "Release Notes"
excerpt: "Notes on Flat Kit updates."
permalink: /release-notes/
toc: false
---

## 4.9.6 <small>(2025-08-24)</small>
- Fixed **Desert Pillar** shader of the **Desert** demo producing errors in **Unity 6.1**.

## 4.9.5 <small>(2025-04-21)</small>
- Improved **baked global illumination** integration for the **Terrain shader** in Unity 6 and later.
- General usability improvements.

## 4.9.4 <small>(2025-03-28)</small>
- Improved **baked light** integration in **Unity 6.0.12** and later.
- Added **support for DOTS** to the **water shader** (enable `FLAT_KIT_DOTS_INSTANCING_ON` in Water.shader).
- Improved **Render Graph** integration for all **image effects**: Outline, Fog, Pixelation.

## 4.9.3 <small>(2025-01-21)</small>
- Fixed an issue with **SRP batching** in Stylized Surface shader.
- Improved the **Pixelation** image effect when using Render Graph.

## 4.9.2 <small>(2024-12-20)</small>
- Improved **compatibility with Unity 6**: proble blending, global illumination.

## 4.9.0 <small>(2024-12-16)</small>
- All **image effects** (Outline, Fog, Pixelation) now **support Render Graph** in **Unity 6.0.16** or later. The effects work with and without the Compatibility Mode (Project Settings -> Graphics).

## 4.8.0 <small>(2024-11-20)</small>
- Improved support for **Adaptive Light Probes** in Unity 6.0.
- Improved support for the **Forward+** rendering path in **Unity 6.0.16** or later.
- Fixed **Override Light Direction** setting on the Terrain shader.

## 4.7.8 <small>(2024-11-07)</small>
- Fixes and improvements to static lightmapping of the Stylized Surface shader.

## 4.7.6 <small>(2024-10-25)</small>
- Fixes and improvements to **per-object outline rendering**.

## 4.7.5 <small>(2024-10-09)</small>
- Added object **dissolve effect** example to the **Room demo scene** (press Play to view).

## 4.7.1 <small>(2024-09-01)</small>
- Improved shader compatibility with **Unity 6.0.12 and later**.

## 4.7.0 <small>(2024-08-01)</small>
- **Per-object Outline feature in Stylized Surface**: outline shader pass is now applied using a custom Renderer Feature (as opposed to additional object shader pass). This significantly **improves performance** of per-object outlines and supports **SRP batching**.
- The migration to the new per-object outlines happens fully automatically when you view the Inspector of a scene object using the Outline feature.
- Improved shader compatibility with **Unity 6.0.12** and later.

## 4.6.1 <small>(2024-07-08)</small>
- Improved **support for Unity 6.0.8** and later (including `OUTPUT_SH4` error).
- Fixed an issue with the **Override Light Direction** setting of the Stylized Surface shader.
- General usability improvements.

## 4.6.0 <small>(2024-05-06)</small>
- Added **Unity 6 Preview** support.

## 4.5.0 <small>(2024-03-23)</small>
- Improved shader support of **DOTS** and the **Hybrid Renderer**.
- Fixed **shader variant stripping** of the Stylized Surface shader.
- Fixed alphatest for **cutout mode** of Stylized Surface shader.
- Added ability to change blending of **vertex colors** to be applied after shading.
- Improved rendering of **baked lightmaps**.
- Fixed flipped baked lighting direction when using **light probes**.
- Improved tooltips throughout the asset.

## 4.4.7 <small>(2024-02-26)</small>
- **BREAKING CHANGE:** We've changed the way **baked lightmaps and light probes** are applied. It now looks much more coherent with the cell shading stylization.

## 4.4.0 <small>(2024-02-06)</small>
- Added shader support for **URP 17** (Unity 2023.3).

## 4.3.0 <small>(2024-01-03)</small>
- *New!* We've added **"Fade With Distance"** feature to the Outline image effect. If enabled, the lines become more transparent the further they are from the camera.

## 4.2.0 <small>(2023-12-19)</small>
- Stylized Water shader now supports multiple lights.
- Decals now correctly receive shadows in URP.
- Fixed image effect materials not being initialized in the Editor in rare circumstances.

## 4.1.5 <small>(2023-12-08)</small>
- Improved UI of all image effect settings, making them editable inline.
- Fixed an issue where image effects are sometimes not included in the project builds.

## 4.1.0 <small>(2023-12-01)</small>
- **Decals** now receive shadows in URP.
- Improved backwards compatibility of **image effects** (Outlines, Fog) with Unity 2021 and prior.
- Inspector UI improvements for the **image effects**.

## 4.0.0 <small>(2023-11-02)</small> - **HUGE update**
- **Pixelation image effect** (+ new demo scene) for a stylish low-res look
- **Mesh processor** that generates perfectly smooth normals that greatly improve object-based outlines
- **New demo scene "Desert"** showing a Moebius-esque style using the Outline image effect
- Stylized Surface materials now support **Local Space Height Gradients**
- Complete **Inspector UI overhaul** of Stylized Surface and Water shaders (+ tooltips on ALL parameters)

## 3.9.6 <small>(2023-09-26)</small>
- **Stylized Surface** shader now stylizes all additional light sources in **Forward+** rendering path.

## 3.9.2 <small>(2023-09-12)</small>
- Fixed shader error in `'FlatKit/Stylized Surface': 'OUTPUT_SH': Too many arguments for a macro call` in Unity 2023.1.9+.

## 3.9.1 <small>(2023-08-16)</small>
- Fixed an issue where outline image effect would sometimes show the scene as grey.
- Improved SRP Batcher compatibility in the latest versions of Unity.

## 3.9.0 <small>(2023-08-09)</small>
- **Detail Maps!** We've expanded the texture functionality in the stylized rendering to include detail maps. Now you have ability to layer two textures with independent blending settings.
- **Fog effect!** We've added an option for the fog to apply in world space, allowing a nice variety of new styles, a-la Monument Valley.
- We've **changed the blending of the Albedo (Base) map** to mix with the stylized shading in a cleaner, more visually appealing way.
- Reworked the Outline image effect to correctly **render in XR** mode when using recent versions of Unity.

## 3.8.0 <small>(2023-07-01)</small>
- Improved object-based outline effect integration with the **Curved World** asset.
- Various UI fixes and improvements.

## 3.7.0 <small>(2023-06-10)</small>
- Improved **shader variant stripping** of all shaders. This reduces build size and duration.
- **Skybox shader**: added an option to remove color banding when using two similar colors.
- Improved integration with URP **Forward+ rendering path**.
- **Terrain**: Updated rendering layers with the latest version of URP.
- Improved outline integration with the **Curved World asset**.
- **URP decals** are now applied after lighting is calculated.

## 3.6.0 <small>(2023-05-10)</small>
- **BREAKING CHANGE**: We've improved the way base texture is used in stylized rendering. This may change the way your textured objects look.
- Improved support for [Light Layers](https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@12.0/manual/lighting/light-layers.html).
- Improved support for [SSAO](https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@12.0/manual/post-processing-ssao.html) in Deferred rendering path.
- Fixed an issue with emission on textured renderers.
- Improved the water shader inspector.
- Improved shader variant striping for Stylized Surface, Terrain and Water shaders. This results in shorter build times and binary sizes.

## 3.5.0 <small>(2023-03-23)</small>
- Added support for **Unity 2023.1** and **URP 15**.

## 3.4.1 <small>(2023-03-14)</small>
- Fixed a build error that occured in Unity 2021 on Android and iOS. Unexplicably, Unity uses two different URP versions in one Unity version.

## 3.4.0 <small>(2023-03-06)</small>
- Added support for **dynamic lightmaps** and **debug display** in URP.
- Improved **Terrain shader** compatibility with the **Forward+** rendering path.
- Added suport for **screen-space shadows** and **reflection probe blending** in the **Terrain shader**.
- The **Buoyancy** component now supports remmebering the **initial rotation** of the object.
- Water shader UI improvements.
- Improved the appearance of demo scenes **Room** and **Wanderer**.
- Added two water materials to the **Ocean Islands** demo scene.

## 3.3.0 <small>(2023-01-20)</small>
- **BREAKING CHANGE**: If a water material uses foam with a texture, it might look **slightly different** with this update. The foam direction formula had a bug, which caused foam textures to be slightly stretched. This is now fixed.
- Added support for Unity's new **LOD cross-fade** functionality.
- Added support for the **Forward+** rendering path.
- Fixed **depth outlines** in the Outline Renderer Feature.
- Fixed rendering of **shadows on the Water shader**.
- Fixed **tiling of water** when using a foam texture.
- Fixed an issue where sometimes the Outline shader pass was not properly disabled, causing **SRP Batching** to break.

## 3.2.5 <small>(2023-01-02)</small>
- Fixed **water** rendering in **WebGL** builds.
- **URP demo scenes now auto-configure** the URP Asset/Renderer. No maual configuration is needed anymore, removed actions from the Readme config section.

## 3.2.0 <small>(2022-12-15)</small>

- **Water shader** now supports for SRP Batcher.
- **Water shader** now supports DOTS.
- **Terrain shader** now supports *Height-based blending*.
- Fixed an issue where the *Outline* and *Fog* image effects Render Events were not being set correctly.
- Improved compatibility with Unity 2022.2.

## 3.1.0

- Improved emission on the Stylized Surface shader. Now whole-object emission does not require a texture.
- Added assembly definition files. Now Flat Kit scripts are not being recompiled when you change code, saving hot reload time.
- Added an option to apply image effects in Scene view.
- Fixed an issue where image effects were sometimes not included in builds.
- Fixed vertex displacement of the water shader.
Re-organized demo folders structure, now it's much cleaner.

## 3.0.6

- **[URP]** Fixed a bug where image effect shaders did not get included in some game builds.
- **[Water shader]** Improved compatibility with Xbox and PS5.

## 3.0.5

- **[URP]** Improved performance of Fog and Outline image effect initialization.
- **[URP]** Fixed a bug where image effects would stop working when changing Quality Levels at runtime.

## 3.0.1

- **[Built-in RP]** Improved compatibility of the Stylized Surface, Cutout and Outline shaders with the Deferred rendering path.
- Improved support of Unity 2022.1.

## 3.0.0

- **[URP]** Added the "Render Event" setting to the Fog and Outline image effects. This allows excluding transparent ane UI objects from being affected by the effects.
- Outline Image Effect now preserves the alpha channel for better effect stacking.
- Flat Kit Depth Normals Renderer Feature has been deprecated in favor of the pass that has been added in URP 10.
- General UI improvements and code refactoring.

## 2.9.7

- **[Built-in RP]** Fixed outline rendering offset on Android builds.

## 2.9.5

- Improved rendering in the URP deferred rendering path.

## 2.9.0

- **[XR]** The #1 requested XR feature is done - Outline and Fog effects now support Single Pass Stereo rendering. As far as we know, Flat Kit is currently the only asset with image effects that correctly support Single Pass stereo.
- **[XR]** Fixed "Light Plane" and Skybox shaders compatibility with XR.
Updated light sharpness stylization for baked Global Illumination.
Added custom Terrain Material Editor for better integration with Unity terrain.
Improved how image effect shaders are referenced, now these shaders are not included in game builds if not used.
- **[Stylized Surface]** "Receive shadows" toggle now uses the same keywords as Unity's standard shaders, making this setting survive shader replacement.
- **[Image effects]** Outline and Fog image effects now use "Before Rendering Post-Processing" render event. With the new changes to these effects, this should work for all configurations.

## 2.8.1

- Improved integration with the Curved World asset.

## 2.8.0

- Improved compatibility with the Deferred rendering path.
- **[Outline Image Effect]** Added an option for resolution-invariant outlines. If enabled, the line width stays constant regardless of the rendering resolution.

## 2.7.0

- Fixed a shader variant stripping issue that was causing long build times and build sizes on Unity 2020.3-2021.1 and URP 10-11.
- The Readme script now checks the project's color space and suggests a switch to display the demo scenes correctly.

## 2.6.5

- Stylized Surface: the tiling / offset texture properties are now shared between all textures.

## 2.6.0

- Added support for the new URP 12 features: decals and Rendering Debug.

## 2.5.3

- Improved compatibility with the new Unity 2021.2.

## 2.5.2

- Breaking change: The outline pass on the Stylized Lit shader now has an explicit toggle. Please enable it on your existing materials that use the outline.
- The 'Shadow Occlusion' parameter now affects both shadow attenuation and distance attenuation, which means it works for all types of light sources.

## 2.5.1

- Added a new parameter to the 'Stylized Surface' shader - 'Shadow Occlusion' which masks received Unity shadows in areas where normals face away from the light. This is useful to remove shadows that 'go through' objects.

## 2.5.0

- Added outline functionality to the main 'Stylized Surface' shader. The outline pass is activated automatically when an outline is added to the material.
- Deprecated the separate 'Stylized Surface with Outline' shader, please use the 'Stylized Surface'.

## 2.4.0

- Added integration with the Curved World asset.

## 2.3.5

- Fixed a bug where stylized rendering was applied only to the first four terrain layers. Using only four layers is still a good idea for performance.

## 2.2.5

- Added emission map to the stylized surface shaders.

## 2.2.0

- Added render event selection to the Fog and Depth/Normal effects. This allows customizing all image effects to affect or ignore the transparent objects.
- Added a queue offset parameter to the Stylized Surface shader.
- Fixed an issue with using shadowmask in some lighting setups.
- Added ability to check for updates directly from the Flat Kit readme.

## 2.1.8

- Fixed Fog image effect rendering in VR (multi-pass).
- Improved compatibility of the Outline image effect with VR (multi-pass).
- Readme debug information now shows the correct version of URP.
- Fixed asset previews sometimes being rendered incorrectly when a Flat Kit image effect is in use.

## 2.1.6

- Added support for Screen Space Ambient Occlusion in URP.
- Unity fog now affects Flat Kit water.
- Added a parameter that controls scene light contribution to the water color.

## 2.1.5

- Stylized Surface shader now supports SRP batching.
- Added a set of quick actions accessible from the scripted Readme.

## 2.1.4

- Stylized Surface inspector fixes.
- Added a scripted Readme.

## 2.1.3

- Fixed shaders referencing URP 10 passes in Unity 2019.
- Fixed error in the Stylized Surface Editor trying to reference "_Color" field when creating a fresh material.

## 2.1.2

- Added "Scale" parameter to the "Stylized Surface Outline" shader. This parameter controls the scale of the front-face-culled object used for the outline.
- Terrain shader now supportes terrain holes.
- Improved compatibility of the terrain shader with the latest URP versions.
- Deprecated the "Stylized Surface Cutout" shader - all functionality is now present in the "Stylized Surface" and "Stylized Surface Outline" shaders.

## 2.1.1

- Fixed Stylized Surface Outline shader pass (resolved missing "vertex" field).
- Fixed Stylized Surface shaders sometimes missing in the build.

## 2.1.0

- Improved compatibility of the Outline image effect with VR.
- Fixed order of rendering of the outline in full-screen and per-object approaches.

## 2.0.9

- Improved the look of baked light on Flat Kit materials.

## 2.0.8

- Resolved compatibility issues in Unity 2020.2 and URP 10.
- Water shader: Added new rendering options that control the draw order and queue. This lets water layers to be configured to correctly overlap.
- Surface shader outline: improved VR compatibility.
- Outline image effect: improved VR compatibility.

## 2.0.7

Added a workaround shader fix for Unity 2020.2. Please read FAQ: <https://flatkit.dustyroom.com>

## 2.0.6

- Removed dependency on Unity's Post Processing package.
- Improved compatibility with the upcoming Unity 2020.2.
- Fixed terrain splatmap layers in URP.
- Added Unity shadow color shader parameter to GPU Instancing.
- Fixed a bug where water shader was not displayed correctly using orthographic cameras.

## 2.0.5

- **[URP]** Added custom baked light / GI for the surface shaders.

## 2.0.0 - **HUGE update**

- WATER! We've added a stylized water shader with lots of parameters and a few dedicated demo scenes.
- Large refactoring of the core lighting shader code, resulting in increased shader performance.
- Outline render pass now lets you customize the render phase, allowing it to be applied to transparent objects and custom render layers.
- New improved documentation now hosted separately at <https://flatkit.dustyroom.com>.
- Improved Inspector UI of the stylized surface shaders.
- Added tooltips to most parameters of the shaders.

## 1.9.91

- **[URP]** Added a parameter that controls how much outline width depends on distance to the camera.
- **[URP]** The object outlines are now impacted by scene fog.
- **[URP]** Miscellaneous fixes in URP render features.
- **[URP]** Replaced Post-processing Stack V2 with the URP post-processing.
- **[URP]** Refactored the lighting model, resulting in increased shader performance.
- **[Built-in]** The outline image effect now works with isometric cameras.

## 1.9.9

- **[URP]** Added a parameter to control the light attenuation size for the point and spot lights. This lets you achieve either sharp or gradual transition between shaded and lit areas.
- **[URP]** Changed point/spot light attenuation radius to be closer to the standard shaders.
- **[URP/Built-in]** Changed the structure of the project. There is now a unity package for each rendering pipeline.

## 1.9.8

- **[URP]** Added transparency to the Stylized Surface. Multiple blend modes are supported.
- **[URP]** Added alpha cutout option to the main Stylized Surface shader.
- **[URP]** Fixed distance attenuation for spot and point lights.
- **[URP/Built-in]** Fixed an issue where "Override light direction" option was not saved per material.

## 1.9.7

- **[Built-in/URP]** Added an option to override light direction for cel shading. This is especially useful if all light in the scene is baked.
- **[URP]** Fixed "Light color impact" setting.
- **[Built-in]** Significantly reduced package import time.
- **[Built-in]** Now getting light direction from directional lightmaps for scenes with baked lighting.
- **[URP]** Added support for vertex color.

## 1.9.6

- **[URP]** Fixed a problem where depth-controlled outline was displayed differently in Edit and Play modes.
- **[URP]** Fixed normal maps not being correctly applied.
- **[URP]** Improved the Inspector UI of the Stylized Surface shader.

## 1.9.5

- **[URP]** Improved VR compatibility (including Oculus Quest).
- **[URP]** Fixed transparent object handling in the image effects.
- **[URP]** Fixed cutout shader not casting shadows.

## 1.9.0

- **[URP]** Added support for double sided and back-sided face rendering modes.
- **[URP]** Improved terrain shader compatibility with URP.

## 1.8.5

- Improved point light distance attenuation in URP.
- Fixed URP post-processing shaders not being included in Android builds.

## 1.8.0

- Added Deferred rendering passes to the stylized surface shaders. This improves the PBR workflow of Flat Kit.
