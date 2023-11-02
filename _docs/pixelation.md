---
title: "Flat Kit Pixelation"
permalink: /pixelation/
toc: true
---

![](/FlatKit_Manual_Images/flat-kit-pixelation-1.png)

**Flat Kit Pixelation** image effect is a post-processing effect that lets you pixelate the image. It is a global effect and is not selective to objects. It is applied per Renderer (in URP) in screen space.

Please note that Flat Kit Pixelation is the Universal RP effect only.
{:.notice--warning}

![Flat Kit Pixelation. Inspector interface](/FlatKit_Manual_Images/pixelation-image-effect-interface.png){: .image-fancy }


{:.image-caption}
Flat Kit Pixelation. Inspector interface

* In **Universal RP (URP)**: post-processing effects are called ‘Renderer Features’ of the Forward Renderer.
* In **Built-In RP**: Post-processing is made of Camera effects placed onto the camera in the scene as Components.
{% endcapture %}

<div class="notice--info">
  {{ notice-text | markdownify }}
</div>

### Setting up Flat Kit Pixelation

* On your Renderer, please click the **Add Renderer Feature** button and select **Flat Kit Pixelation** from the list.

### Parameters of Flat Kit Pixelation

* **Resolution** lets you set the size of the grain, or 'pixels'. The higher the value, the smaller the pixels are.
* **Render Event** lets you choose a stage at which the Pixelation effect is applied.
* **Apply In Scene View** detrmines whether the effect should be applied in the Scene view as well as in the Game view. Please, keep in mind that Unity always renders the scene with the default Renderer settings of the URP config.

In some cases you'll need to *press 'Play'* to see the effect of *Render Event*.

