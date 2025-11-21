---
title: "Frequently Asked Questions (FAQs)"
permalink: /faq/
toc: false
---

#### Q. I have purchased Quibli. How do I get the discount for Flat Kit?

> **A.** Once you log into the account you have purchased Quibli from, and load the Flat Kit Asset Store page, you should see the automatic 50% off discount for Flat Kit.

<!-- #### Q. After importing/updating Flat Kit the shaders failed to compile. 'X' shader is missing from the list. Why?

> **A.** Because of the recent Unity's error, there is a mess going on with the packages in the Package Manager. You see one version of the package but in reality it may be another, unsupported one. Also, this bug won't let you install and change the versions of the assets in the Package Manager (which you need to do in this case — **you need to update the version of Universal RP**). Unity is working on it, here's the [issue tracker](https://issuetracker.unity3d.com/issues/package-manager-doesnt-show-available-updates).  
If you updated to the latest version of Unity, and still haven't resolved it, please restart Unity. If after restart the errors won’t go away, clean the cache of the Package Manager and re-import Flat Kit, as it is another one symptom of this Unity's problem. You can find the cache here  
*Mac OS:* `~/Library/Unity/Asset Store-5.x` (press `Shift+Cmd+G` in any Finder Window or press Go -> Go to Folder on the top bar and paste this path)  
*Windows:* `%APPDATA%\Unity\Asset Store-5.x` (hidden folder, press Win+R to open 'Run' window and paste this path)  
*Linux:* `~/.local/share/unity3d/Asset Store-5.x`  -->

#### Q. What is the difference between Flat Kit and Quibli?

> Flat Kit is a set of tools for bread-and-butter toon shading end effects. Quibli was designed to be more open in regards to non-photorealistic stylization, while including the tools for the anime style works. The detailed comparison can be found [here](https://quibli.dustyroom.com/quibli-flat-kit/).

#### Q. Is it easy to use Flat Kit for a beginner?  

> Yes, there's nothing complicated about it from the user perspective. Even though there are lots of parameters, they all have good default values and well-structured interface. Additionally, there are mouse-over tooltips with little hints on all parameters.

#### Q. Is it possible to apply the Flat Kit look while using my own shaders?  

> The cel shading ([Stylized Surface shader](/stylized-surface/), located in `Flat Kit\Stylized Surface`) is implemented as object shaders, which means that they are used on regular materials. However, the [Outline](/outline/) and [Fog](/fog/) are *image effects* applied globally (as camera components in the Built-In RP and as Render Features in URP).

#### Q. What platforms can I build for? What about VR?  

> Flat Kit works in builds for all platforms listed in Unity Build settings, including VR, WebGL and mobile.

#### Q. There are missing scripts in some demo scenes on the main camera

> Unity has some camera scripts that are available only in a particular RP. Because we use the same scenes for the URP and Built-In RP demos in Flat Kit, it may appear that a script is missing from the camera in our demos. This warning is harmless and can be safely ignored, or you may remove the missing script from the camera.

#### Q. Does Flat Kit support URP? Why is the feature X is available in Universal RP but not in Built-In RP?  

> Flat Kit supports URP as well as Built-In RP, although Built-In RP is not being developed after Flat Kit v.2.0. There are a few known limitations in URP, please see [FlatKit in URP chapter](/flat-kit-in-urp). As Built-In RP is not being actively developed by Unity anymore an it has its drawbacks, we continue to support it but we develop new great features only for URP, instead of supporting an obsolete technology. Please note, there is no HDRP version of Flat Kit yet.

#### Q. What texture maps does Flat Kit support?  

> Flat Kit supports albedo, detail (URP version of Flat Kit only), normal and emission (URP version of Flat Kit only) maps, more info [here](/stylized-surface/#texture-maps).

#### Q. I’ve got errors just after importing Flat Kit. Why?  

> Please read this detailed [guide](/quick-start/#after-importing-flat-kit-gives-errors) on how to resolve errors after importing Flat Kit into your project. If none of those helped, [get in touch](/contact-details).

#### Q. What is the Shader Compilation Target Level of Flat Kit shaders?  

> The object shaders target 3.5 (or es 3.0 and WebGL 2.0).

#### Q. It takes very long to import Flat Kit into Unity in Built-in RP  

>FlatKit Built-in RP uses shader variants to achieve high flexibility and best performance. This comes at a cost of increased time to import the asset and build the game binary. In URP importing is much shorter, so we encourage you to use the URP version of Flat Kit if possible. If you have to use Built-In RP, though, to speed things up, uncheck unneeded elements when importing the asset.

#### Q. Does Flat Kit work with Post-processing stack v.2?  

>Yes, it does. The fog and outline image effects can be added on the same camera as the Post-processing component (Built-in Rendering Pipeline). Post-processing in URP is known as ‘Renderer Features’, so you don't have to install Post-Processing v.2. See [Flat Kit in URP](/flat-kit-in-urp/) chapter for the details.

#### Q. Why is my build getting so many shader variants (and takes long to build)?

>- Chances are you are using Universal RP earlier than v. 10.7. If you are, please update to the latest version of URP. This should reduce the number of shader variants significantly as newer versions have tools that use multi-compilation, which addresses this problem with variants and building times.
>- Another one thing you can try doing is the following:
Go to the 'Graphics' settings (_Edit_ ▶︎ _Project Settings_ ▶︎ _Graphics_). At the bottom you should see a 'Save to asset...' button. Use that to save a compiled shader variants file. Then select the newly created preset file into the 'Preloaded Shaders' list.
If this won't help, delete this preset file, then on the Graphics panel, set 'Instancing Variants' to 'Strip All', create a new preset, add it to the list and try to build. The initial build can take longer than the following ones as the following builds won't be re-calculating it all again.
>- There were numerous reports of the same problem (like [this one](https://github.com/Dustyroom/flat-kit-doc/issues/89)), when the cause on this issue was a 3rd party asset that turned on the compilation of all shader variants. If you have any 3rd party assets in your project, please check if they have such an option to temporarily deactivating/deleting them one by one.
>- To make sure whether it is a problem with Flat Kit shaders, you can try creating a fresh project with only Flat Kit imported into it and building any of the [Demo scenes](/demo-scenes).
>- If nothing helps, please [get in touch](/contact-details).

#### Q. Does Flat Kit support DOTS?

>- Yes, it's described here in [/stylized-surface/#using-dots] of the [Stylized Surface](/stylized-surface) shader's page.

<!-- <details><summary>Why is my build getting so many shader variants (and takes long to build)?</summary><div markdown="1">
>- Chances are you are using Universal RP earlier than v. 10.7. If you are, please update to the latest version of URP. This should reduce the number of shader variants significantly as newer versions have tools that use multi-compilation, which addresses this problem with variants and building times.
>- Another one thing you can try doing is the following:
Go to the 'Graphics' settings (_Edit_ ▶︎ _Project Settings_ ▶︎ _Graphics_). At the bottom you should see a 'Save to asset...' button. Use that to save a compiled shader variants file. Then select the newly created preset file into the 'Preloaded Shaders' list.
If this won't help, delete this preset file, then on the Graphics panel, set 'Instancing Variants' to 'Strip All', create a new preset, add it to the list and try to build. The initial build can take longer than the following ones as the following builds won't be re-calculating it all again.
>- There were numerous reports of the same problem (like [this one](https://github.com/Dustyroom/flat-kit-doc/issues/89)), when the cause on this issue was a 3rd party asset that turned on the compilation of all shader variants. If you have any 3rd party assets in your project, please check if they have such an option to temporarily deactivating/deleting them one by one.
>- To make sure whether it is a problem with Flat Kit shaders, you can try creating a fresh project with only Flat Kit imported into it and building any of the [Demo scenes](/demo-scenes).
>- If nothing helps, please [get in touch](/contact-details).
</div></details> -->