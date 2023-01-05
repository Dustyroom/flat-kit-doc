---
title: "Flat Kit in URP"
permalink: /flat-kit-in-urp/
excerpt: "Flat Kit in URP"
toc: true
---

Although many of the features in Flat Kit look identically in URP and in Built-In RP versions, the differences are becoming inevitable for a couple of reasons. Built-in RP is being deprecated by Unity, URP is faster and it is a way to go, URP offers the tools Built-In RP is lacking. One of the differences is in post-processing. Flat Kit Built-In RP uses Post-Processing Stack v.2. Flat Kit URP uses URP's native Volume toolkit. Both of these offer similar post-processing tools but they behave differently. Even when using the same values for Color grading section in Built-In RP and URP, the outcome is slightly different.

Please note, Flat Kit had been initially created for the Built-in Rendering Pipeline. To keep the visual results as close to the original as possible, the URP version of Flat Kit is using HLSL code rather than shader graph. It means you can switch a Flat Kit project between URP and Built-in RP at any point without extra work. However if you’d like to edit the shaders, you'll need some programming skills. Although you can switch between the Rendering Pipelines, we cannot guarantee that all Unity versions will let you do it flawlessly. That is why, to make Flat Kit work out of the box, we highly recommended that you created a Universal RP project to begin with.

## URP Installation

In order to have a working Flat Kit in Universal RP (we've included the URP version alongside the Built-in pipeline version, in a single package), you'll need to have Unity's Universal RP package installed in your project.

After that, you will need to use a Universal RP Asset file. You can either use the one that comes with Flat Kit, called ***[Flat Kit] Example Settings URP***, or you can create your own URP asset file to work with.

* Right click on Assets (in Project tab) ▶︎ Create ▶︎ Rendering ▶︎ URP ▶︎ Pipeline Asset.

Once you do it, the Asset and Forward Renderer are created.

Please refer to the chapter ['Quick start. Beginning to work with Flat Kit'](/quick-start) in the beginning of this manual for more important information about setting up Flat Kit and using URP Pipeline Asset files.  

The last step of the installation shown in the video in a chapter ['Quick start. Beginning to work with Flat Kit'](/quick-start) was pressing *Configure for URP* button in a *[Readme]* file that came with Flat Kit. This automatic step replaces two manual steps of setting up Flat Kit in Universal RP:
* **Manual Step 1.** Navigate to *Project Settings* -> *Graphics* and insert **[FlatKit] Example Settings URP** file into *Scriptable Rendering Pipeline Setting* field.
If you are using your settings file instead, please make sure to have *Opaque texture* and *Depth texture* checkboxes on, which can be found on Inspector tab when you select that URP settings file.  
![Flat Kit import instructions - Step 5](FlatKit_Manual_Images/manual_import_instructions_6.png)

* **Manual Step 2.** Please do this in *Quality* tab's *Rendering* field as well. This Example Settings file comes with Flat Kit — select **[FlatKit] Example Settings URP** file. Do it for all Quality levels.  
![Flat Kit import instructions - Step 6](FlatKit_Manual_Images/manual_import_instructions_7.png)

Here's a video showing setting it up.  

<iframe width="560" height="315" src="https://www.youtube.com/embed/8yiihlFPmGg?start=108" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>  

## Flat Kit Image Effects in URP

In URP, 'Fog' and 'Outline' image effects, included in Flat Kit, are no longer image effects, they have been adapted to become Render Features. Unlike the conventional image effects that are added to the camera game object, Render Features are added as stages to the Forward Renderer.

To use Flat Kit effects, please first update the Universal RP to the version higher than 8.2.0.

Go to Window ▶︎ Package Manager ▶︎ Universal RP ▶︎ Select the version to upgrade to ▶︎ click Upgrade

Our example scenes already include configurations of the Forward Renderer with outline and fog image effects (look for the URP Config folders in the demo directory).

To enable outline and fog, select the ForwardRendererConfig and add the 'outline' or 'fog' stage. In the case of 'outline' effect, you also need to add the DepthNormalsPass stage.

The order of the effects can be managed like this.

![Managing the order of renderer layers in URP](FlatKit_Manual_Images/URP-renderer-layers-01.png)
> Managing the order of renderer layers in URP

It's a default URP thing. What is worth noting is that for Outlines we made an option to choose the order of Renderer Events within Outline Image Effect interface. Please refer to the corresponding chapter of this manual, [Outline Image Effect](/image-effects/#outline-image-effect).

## Post-processing V2 in URP (General Info)

We use PPv2 in our demo scenes for additional image effects. To enable these additional effects you need to:

Go to Assets (in Project tab) ▶︎ Universal Rendering Pipeline asset ▶︎ go to Inspector tab ▶︎ Post-processing Feature Set ▶︎ select Post Processing V2 from the drop-down.

Enable the Post Processing flat on the camera inspector:

![Camera properties. How to enable Post-processing v.2](FlatKit_Manual_Images/enable-post-processing-camera.png)
> Camera properties. How to enable Post-processing v.2
