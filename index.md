If you’ve got a question regarding Flat Kit, please read through the Frequently Asked Questions, and try searching for the answers here. If the question is not covered, please shoot an email to info@dustyroom.com. If you find a bug, it really helps us if you include steps to reproduce it. Please mind that we get lots of messages daily, be patient - we’re getting to it. Also, if you got a feature you’d like to see implemented, let us know.

# Frequently Asked Questions (FAQs)

Q. Does Flat Kit support URP?  
A. Flat Kit supports URP. There are a few known limitations, please see FlatKit in URP.  Please note, there is no HDRP version of Flat Kit.

Q. There are missing scripts in some demo scenes on the main camera.  
A. Our demo scenes use Unity’s PostProcessing Stack V2. It is not required if you are not using the demo scenes.

Q. Does Flat Kit support PBR (Physically-Based Rendering)?  
A. In Flat Kit indirect sources of light influence the colors of the scene by default, which can be turned off. The shaders do not support parameters required for the photorealistic look such as metallicness and translucency and subsurface scattering.

Q. Does Flat Kit support normal maps?  
A. Yes, it does. It is in Bump map section of the interface.

Q. Does Flat Kit work with Post-processing stack v.2?  
A. Yes, it does. The fog and outline image effects can be added on the same camera as the Post-processing component (Built-in Rendering Pipeline). Post-processing in URP is known as ‘Renderer Features’. See FlatKit in URP if you are willing to know more.

Q. Does it work with Unity version 20XX.x?  
A. As soon as you’ve got a stable Unity version, it does.

Q. What platforms can I build for? What about VR?  
A. Flat Kit shaders work in builds for all platforms listed in Unity Build settings, including VR, WebGL and mobile. Please, note, the Outline image effect currently is not optimized for VR.

Q. Can I use the scenes from Flat Kit in a commercial project?  
A. Yes, you can. As soon as you purchase it, you can use anything from Flat Kit in the private and commercial projects without a need to credit authors of the asset (us). What you can’t do is to re-sell, give away or place on public repositories any part of the asset as it is. More info here — https://unity3d.com/legal/as_terms

Q. I’ve got errors just after importing Flat Kit. Why?  
A. First thing to try would be to restart Unity and check again. Secondly, try re-importing the asset. If none of these helped, shoot a mail to info@dustyroom.com

Q. How do I get projectors to work with the Stylized Surface shader?  
A. Please uncomment this line in the StylizedSurface.shader:
```
#pragma skip_variants POINT_COOKIE DIRECTIONAL_COOKIE
```

Q. What is the Shader Compilation Target Level of Flat Kit shaders?  
A. The object shaders target 3.5 (or es 3.0 and WebGL 2.0).

Q. It takes very long to import Flat Kit into Unity in Built-in RP.  
A. FlatKit Built-in RP uses shader variants to achieve high flexibility and best performance. However it can take time to import the asset and build the game binary. In URP importing takes seconds, so we encourage you to use the URP version of Flat Kit. If you have to use Built-In RP, though, to speed things up, uncheck unneeded elements when importing the asset.


# 1. Quick Overview

Thank you for purchasing Flat Kit. We hope it will bring you some serious streams of inspiration and suit your wide variety of design needs.

We’ve spent hundreds of hours to research, design and implement the right set of assets needed to achieve a slick minimalist look. We hope it works for your project out of the box. If you have questions after reading this guide, let us know at info@dustyroom.com.

To name Flat Kit a set of flat shaders, cel shaders or toon ones, would be a serious underestimation. Yes, these all can be easily done. As well as countless other (maybe unseen before) styles. It can be sharp flat, it can have one, two, nine steps of hard shadow, or soft-shaded, or gradient-shaded — with pale or acid colors, it can have three gradient effects (when you start thinking out of the box, the parameter like ‘Specular’, usual for, well, a specularity or glare, here can act as your fourth shadow, or a gradient etc).

In case you already use any other flat-looking shaders, you will still find a variety of useful tools for quick image processing. Particularly, later in the manual we’ll overview the Height Gradient mode of the Stylized Surface Shader, the Fog Image Effect camera component, LightPlane shader effect etc. They have quite little related to toon or cell shading, but in conjunction with a stylish flat or cel look, they add a whole new life to your scene. Plus, they can be used out of context of non-photorealistic aesthetics. It is a spice that can dramatically make your dish sweeter (tastier).

Flat Kit was made with optimized and fast workflow in mind, so that one could fulfill the picture popped up in the mind — as quickly as possible, in various ways. This means:

* One task could be done in different ways. It is a multi-purpose set of shaders;
* Some outstanding graphical results can be achieved in minutes (given that you have your models ready, there are lots in FlatKit);
* There is always an element of you-didn’t-think-it-can-be-done-this-way surprise thanks to FlatKit deep yet streamlined interface.  
For example, let’s take fog. Fog is usually a big part of any 3D environment, isn’t it? There are lots of methods to implement fog into the scene, often complex and complicated. With Flat Kit, we decided to make it as convenient as possible for the user end. So, the fog can be done in two ways: using **Fog Image Effect** post-effect / camera component or/and using **LightPlane** shader.

    We are going to explain how these work and what they are down in the manual. Both ways suit different needs, but they really do compliment each other.

    Another example of the multi-purpose nature of our shaders is cel shading itself. Now, it’s going to take a whole chapter of this manual to elaborate on cel shading. For now it’s only worth mentioning that the same or similar results can be made using different parameters of the shader’s interface.
It’s important, because apart from the expected ‘Cel Shade parameter’, Flat Kit also has a bunch of additional settings to explore. Each additional parameter of the shader adds an extra dimension of possibilities. It’s like having purple color paint, then you have red, and blue, and yellow. Purple is cool by itself and you already have it, but you can make it up by mixing blue and red. Or you can spare blue to match with yellow — to get green. In any case you get your purple, and also, simultaneously — other combinations, often surprising and inspiring. We’ll talk about the importance of such potential later in the manual.

One of the big advantages of using these shaders is the fact that you don’t have to guess how the colors will look on your scene. If you want precision and accuracy — you have it. Moreover, if you want something unpredictable and you are trying to make your scene look different to spark your inspiration and imagination, but not sure how, you can do this too! Remember, this is a set of shaders selected to complement each other.

![Flat Kit structural view chart](https://github.com/Dustyroom/flat-kit-doc/blob/master/FlatKit_Manual_Images/FlatKit-Structure-Chart.png)

# 2. Quick start. Beginning to work with Flat Kit

Flat Kit is fully self-contained and does not depend on any external assets.  
If you do not need demo scenes, example materials and models you may skip importing the Demos directory in the asset.  
The easiest way to get started with the asset is to dig into the demo scenes.  
For Built-In RP it may take a while for Unity to import the asset — this is normal. Under the hood, Unity needs to generate all shader variants that are used in the demo scenes.  
On the 3D models side, it’s important that you make normals ‘smooth’ for your meshes. If you import someone else's models and can’t edit the object in 3D editor, at least try to calculate normals in Unity — in the import settings of the model. It should work anyway, but sometimes the difference can be obvious, especially on objects with rounded corners.  
**Note:** Our demos were created in **Linear color space** (a setting found in Project Settings). We recommend switching to it if your project is in **Gamma color space**, although this is entirely optional.  

Below are the instructions on how to import Flat Kit.

**Step 1.** It's advised that you imported Flat Kit from Unity Package Manager. Go to Window ▶ Package Manager. On the top left find the My Assets drop down menu. You'll find Flat Kit among your assets. Choose the version you'd like to import. Click Import.  
**Step 2.** Choose which version of Flat Kit to import. If your project is in URP - select [Render Pipeline] Universal (URP).unitypackage. If your project is in Built-In RP, choose [Render Pipeline] Built-In.unitypackage. Click Import. You can re-import any of the versions anytime. The latest imported version overwrites the previously installed one.  
**Step 3.** Once imported, go to Project tab ▶︎ Assets ▶︎ Flat Kit. You'll find the Flat Kit unitypackage file of your preferred RP. Double-click it.  
**Step 4.** Pick what contents of Flat Kit would you like to get unpacked. Click Import. You can import anything at any time while working on your project.

![Flat Kit import instructions.](https://github.com/Dustyroom/flat-kit-doc/blob/master/FlatKit_Manual_Images/flat-kit-import-1-instructions.png)
