---
title: "Flat Kit Pixelation"
permalink: /pixelation/
toc: true
---

![](/FlatKit_Manual_Images/flat-kit-pixelation-1.png)

**Flat Kit Pixelation** image effect is a post-processing effect that lets you pixelate the image. It is a global effect and is not selective to objects. It is applied per Renderer (in URP) in screen space.

Please note that Flat Kit Pixelation is the Universal RP effect only.
{:.notice--warning}

![Flat Kit Pixelation. Inspector interface.](/FlatKit_Manual_Images/pixelation-image-effect-interface.png){: .image-fancy style="width: 500px;"}

{:.image-caption}
Flat Kit Pixelation. Inspector interface.

<!-- {% capture notice-text %}
Both *Fog* and *Outline* image effects can use image-based anti-aliasing, like the one in Unity's Post-processing stack. -->

* In **Universal RP (URP)**: post-processing effects are called ‘Renderer Features’ of the Forward Renderer.
* In **Built-In RP**: Post-processing is made of Camera effects placed onto the camera in the scene as Components.
{% endcapture %}

<div class="notice--info">
  {{ notice-text | markdownify }}
</div>

### Setting up Flat Kit Pixelation

* On your Renderer, please click the **Add Renderer Feature** button and select **Flat Kit Pixelation** from the list.

### Parameters of Flat Kit Outline

* **Resolution** lets you set the size of the grain, or 'pixels'. The higher the value, the smaller the pixels are.
* **Render Event** lets you choose a stage at which the outlines are applied. It allows to apply outlines over the transparent objects. If you want to exclude transparent objects like Water or UI elements, set this to 'Before Transparent'. Also, it allows you to stack the _Pixelation_ effect with other post effects. This feature is URP only.
* **Apply In Scene View** detrmines whether the effect should be applied in the Scene view as well as in the Game view. Please, keep in mind that Unity always renders the scene with the default Renderer settings of the URP config.

In some cases you'll need to *press 'Play'* to see the effect of *Render Event*.

