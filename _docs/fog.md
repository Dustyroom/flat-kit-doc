---
title: "Fog Image Effect"
permalink: /fog/
toc: true
---

Fog Image Effect camera component can be reviewed as a post-processing effect. It can be subtle, like a mist in the lower part of the valley, or a dominant effect, as in a completely hazed environment. Simply put, it works in the following way. You decide whether you need only length fog or height fog or both. Then you determine the bounds where it would take effect. Then you choose colors along each dimension. And after that, blend between distance and height. This effect starts from camera position up to the Near/Far, Low/High bounds, meaning, your camera is the zero coordinate from where the fog spreads. 

**TIP** In Built-In RP, because of the fact that image effects are usually placed on cameras, each camera on the scene can have a separate independent instance of an effect.
{:.notice--success}

<!-- Because Unity’s MSAA (multi-sample anti-aliasing, which is an option in the Quality Settings of your project) does not apply to depth texture, there may be inconsistencies between the anti-aliased color image and the unprocessed depth image. This may look as aliasing if fog intensity is set to a high value. *Such artefacts may only occur if using MSAA*, so we recommend using screen-space anti-aliasing, such as in Unity’s post-processing stack that you can import by going to Window ▶︎ Package Manager in Unity 2018+. -->

When you click on any of the color ramps (Distance or Height Gradient), the Gradient Editor pops up.

Fog Image Effect is being used in the [**Wanderer** Demo scene](https://flatkit.dustyroom.com/demo-scenes/#valley-and-wanderer) (more subtly) and [**Valley** Demo scene](https://flatkit.dustyroom.com/demo-scenes/#valley-and-wanderer) (more accentuated).

![Fog Image Effect. Inspector panel interface](/FlatKit_Manual_Images/fog_image_effect.png){: .image-fancy style="width: 500px;"}

{:.image-caption}
Fog Image Effect. Inspector panel interface

Gradient editor controls the colors of the gradient. To open it, click on Distance Gradient or Height Gradient. The bottom row of breakpoints (pointing up) is the selection of the colors. The above row (pointing down) controls the opacity of the area it points at; the opacity value of one breakpoint fades into the opacity value of the adjacent one. Same for colors.

> **TIP.** If you want the area close to you to be without fog, apart from increasing Near parameter, you can open up the color ramp(s), add a breakpoint next to the leftmost one on the ramp, select leftmost one, make it transparent (see screenshot of Gradient Editor below). The breakpoint you created (opaque, next to the transparent one) becomes your distance or height control.
{:.notice--success}

![Fog Image Effect. Gradient Editor interface.](/FlatKit_Manual_Images/fog_image_effect_gradient_editor.png){: .image-fancy}

{:.image-caption}
Fog Image Effect. Gradient Editor interface.

{% capture notice-text %}
Both *Fog* and *Outline* image effects can use image-based anti-aliasing, like the one in Unity's Post-processing stack.

* In **Universal RP (URP)**: post-processing effects are called ‘Renderer Features’ of the Forward Renderer.
* In **Built-In RP**: Post-processing is made of Camera effects placed onto the camera in the scene as Components.
{% endcapture %}

<div class="notice--info">
  {{ notice-text | markdownify }}
</div>
