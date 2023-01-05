---
title: "Frequently Asked Questions (FAQs)"
permalink: /faq/
toc: false
---

#### Q. I have purchased Quibli. How do I get the discount for Flat Kit?

> **A.** Once you log into the account you have purchased Quibli from, and load the Flat Kit Asset Store page, you should see the automatic 50% off discount for Flat Kit.

#### Q. After importing/updating Flat Kit the shaders failed to compile. 'X' shader is missing from the list. Why?

> **A.** Because of the recent Unity's error, there is a mess going on with the packages in the Package Manager. You see one version of the package but in reality it may be another, unsupported one. Also, this bug won't let you install and change the versions of the assets in the Package Manager (which you need to do in this case — **you need to update the version of Universal RP**). Unity is working on it, here's the [issue tracker](https://issuetracker.unity3d.com/issues/package-manager-doesnt-show-available-updates).  
If you updated to the latest version of Unity, and still haven't resolved it, please restart Unity. If after restart the errors won’t go away, clean the cache of the Package Manager and re-import Flat Kit, as it is another one symptom of this Unity's problem. You can find the cache here  
*Mac OS:* `~/Library/Unity/Asset Store-5.x` (press `Shift+Cmd+G` in any Finder Window or press Go -> Go to Folder on the top bar and paste this path)  
*Windows:* `%APPDATA%\Unity\Asset Store-5.x` (hidden folder, press Win+R to open 'Run' window and paste this path)  
*Linux:* `~/.local/share/unity3d/Asset Store-5.x` 

#### Q. What is the difference between Flat Kit and Quibli?

> **A.**Flat Kit is a set of tools for bread-and-butter toon shading end effects. Quibli was designed to be more open in regards to non-photorealistic stylization, while including the tools for the anime style works. The detailed comparison can be found [here](https://quibli.dustyroom.com/quibli-flat-kit/).

#### Q. Is it easy to use Flat Kit for a beginner?  

> **A.** Yes, there's nothing complicated about it from the user perspective. Even though there are lots of parameters, they all have good default values and well-structured interface. Additionally, there are mouse-over tooltips with little hints on all parameters.

#### Q. Is it possible to apply the Flat Kit look while using my own shaders?  

> **A.** The cel shading (`Flat Kit\Stylized Surface`) is implemented as object shaders, which means that they are used on regular materials. However, the *Outline* and *Fog* are *image effects* applied globally (as camera components in the Built-In RP and as Render Features in URP).

#### Q. What platforms can I build for? What about VR?  

> **A.** Flat Kit shaders work in builds for all platforms listed in Unity Build settings, including VR, WebGL and mobile.

#### Q. There are missing scripts in some demo scenes on the main camera

> **A.** Unity has some camera scripts that are available only in a particular RP. Because we use the same scenes for the URP and Built-In RP demos in Flat Kit, it may appear that a script is missing from the camera in our demos. This warning is harmless and can be safely ignored, or you may remove the missing script from the camera.

#### Q. Does Flat Kit support URP? Why is the feature X is available in Universal RP but not in Built-In RP?  

> **A.** Flat Kit supports URP as well as Built-In RP, although Built-In RP is not being developed after Flat Kit v.2.0. There are a few known limitations in URP, please see [FlatKit in URP chapter](/flat-kit-in-urp). As Built-In RP is not being actively developed by Unity anymore an it has its drawbacks, we continue to support it but we develop new great features only for URP, instead of supporting an obsolete technology. Please note, there is no HDRP version of Flat Kit yet.

#### Q. Does Flat Kit support PBR (Physically-Based Rendering)?  

> **A.** In Flat Kit indirect sources of light influence the colors of the scene by default, which can be turned off. The shaders do not support parameters required for the photorealistic look such as glossiness, metallic or subsurface scattering.

#### Q. Does Flat Kit support normal maps?  

> **A.** Yes, it does. It is in Normal map section of the interface.

#### Q. Does Flat Kit support emission maps?  

> **A.** Yes, the URP version. There is no support for emission maps in Built-In RP version of Flat Kit.

#### Q. I’ve got errors just after importing Flat Kit. Why?  

> **A.** First thing to try would be to restart Unity and check again. Secondly, try re-importing the asset. If none of these helped, [get in touch](/contact).

#### Q. What is the Shader Compilation Target Level of Flat Kit shaders?  

> **A.** The object shaders target 3.5 (or es 3.0 and WebGL 2.0).

#### Q. It takes very long to import Flat Kit into Unity in Built-in RP  

> **A.** FlatKit Built-in RP uses shader variants to achieve high flexibility and best performance. This comes at a cost of increased time to import the asset and build the game binary. In URP importing is much shorter, so we encourage you to use the URP version of Flat Kit if possible. If you have to use Built-In RP, though, to speed things up, uncheck unneeded elements when importing the asset.

#### Q. Does Flat Kit work with Post-processing stack v.2?  

> **A.** Yes, it does. The fog and outline image effects can be added on the same camera as the Post-processing component (Built-in Rendering Pipeline). Post-processing in URP is known as ‘Renderer Features’, so you don't have to install Post-Processing v.2. See FlatKit in URP for the details.
