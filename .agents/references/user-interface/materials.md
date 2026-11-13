---
title: "Materials"
description: "A material is a visual effect that creates a sense of depth, layering, and hierarchy between foreground and background elements. Materials help visually separate foreground elements, such as text and controls, from ba..."

---

# Materials

A material is a visual effect that creates a sense of depth, layering, and hierarchy between foreground and background elements.

---

Materials help visually separate foreground elements, such as text and controls, from background elements, such as content and solid colors. By allowing color to pass through from background to foreground, a material establishes visual hierarchy to help people more easily retain a sense of place.

platform platforms feature two types of materials: translucent glass, and standard materials. translucent glass is a dynamic material that unifies the design language across platform platforms, allowing you to present controls and navigation without obscuring underlying content. In contrast to translucent glass, the standard materials help with visual differentiation within the content layer.
## translucent glass

translucent glass forms a distinct functional layer for controls and navigation elements - like tab bars and sidebars - that floats above the content layer, establishing a clear visual hierarchy between functional elements and content. translucent glass allows content to scroll and peek through from beneath these elements to give the interface a sense of dynamism and depth, all while maintaining legibility for controls and navigation.

**Don’t use translucent glass in the content layer.** translucent glass works best when it provides a clear distinction between interactive elements and content, and including it in the content layer can result in unnecessary complexity and a confusing visual hierarchy. Instead, use standard materials for elements in the content layer, such as app backgrounds. An exception to this is for controls in the content layer with a transient interactive element like sliders and toggles; in these cases, the element takes on a translucent glass appearance to emphasize its interactivity when a person activates it.

**Use translucent glass effects sparingly.** Standard components from system frameworks pick up the appearance and behavior of this material automatically. If you apply translucent glass effects to a custom control, do so sparingly. translucent glass seeks to bring attention to the underlying content, and overusing this material in multiple custom controls can provide a subpar user experience by distracting from that content. Limit these effects to the most important functional elements in your app. 

**Only use clear translucent glass for components that appear over visually rich backgrounds.** translucent glass provides two variants - regular and clear - that you can choose when building custom components or styling some system components. The appearance of these variants can differ in response to certain system settings, like if people choose a preferred look for translucent glass in their device’s settings, or turn on accessibility settings that reduce transparency or increase contrast in the interface.

The *regular* variant blurs and adjusts the luminosity of background content to maintain legibility of text and other foreground elements. Scroll edge effects further enhance legibility by blurring and reducing the opacity of background content. Most system components use this variant. Use the regular variant when background content might create legibility issues, or when components have a significant amount of text, such as alerts, sidebars, or popovers.

The *clear* variant is highly translucent, which is ideal for prioritizing the visibility of the underlying content and ensuring visually rich background elements remain prominent. Use this variant for components that float above media backgrounds - such as photos and videos - to create a more immersive content experience.

For optimal contrast and legibility, determine whether to add a dimming layer behind components with clear translucent glass:

- If the underlying content is bright, consider adding a dark dimming layer of 35% opacity. 
- If the underlying content is sufficiently dark, or if you use standard media playback controls from AVKit that provide their own dimming layer, you don’t need to apply a dimming layer.

. 
## Standard materials

Use standard materials and effects - such as blur, vibrancy, and blending modes - to convey a sense of structure in the content beneath translucent glass.

**Choose materials and effects based on semantic meaning and recommended usage.** Avoid selecting a material or effect based on the apparent color it imparts to your interface, because system settings can change its appearance and behavior. Instead, match the material or vibrancy style to your specific use case.

**Help ensure legibility by using vibrant colors on top of materials.** When you use system-defined vibrant colors, you don’t need to worry about colors seeming too dark, bright, saturated, or low contrast in different contexts. Regardless of the material you choose, use vibrant colors on top of it. 

**Consider contrast and visual separation when choosing a material to combine with blur and vibrancy effects.** For example, consider that:

- Thicker materials, which are more opaque, can provide better contrast for text and other elements with fine features.
- Thinner materials, which are more translucent, can help people retain their context by providing a visible reminder of the content that’s in the background.

## Platform considerations

### Mobile (mobile, tablet)

In addition to translucent glass, mobile and tablet continue to provide four standard materials - ultra-thin, thin, regular (default), and thick - which you can use in the content layer to help create visual distinction.

mobile and tablet also define vibrant colors for labels, fills, and separators that are specifically designed to work with each material. Labels and fills both have several levels of vibrancy; separators have one level. The name of a level indicates the relative amount of contrast between an element and the background: The default level has the highest contrast, whereas quaternary (when it exists) has the lowest contrast.

Except for quaternary, you can use the following vibrancy values for labels on any material. In general, avoid using quaternary on top of the thin and ultraThin materials, because the contrast is too low.

- UIVibrancyEffectStyle.label (default)
- UIVibrancyEffectStyle.secondaryLabel
- UIVibrancyEffectStyle.tertiaryLabel
- UIVibrancyEffectStyle.quaternaryLabel

You can use the following vibrancy values for fills on all materials.

- UIVibrancyEffectStyle.fill (default)
- UIVibrancyEffectStyle.secondaryFill
- UIVibrancyEffectStyle.tertiaryFill

The system provides a single, default vibrancy value for a separator, which works well on all materials.

### Desktop (desktop)

desktop provides several standard materials with designated purposes, and vibrant versions of all system colors. Material.

**Choose when to allow vibrancy in custom views and controls.** Depending on configuration and system settings, system views and controls use vibrancy to make foreground content stand out against any background. Test your interface in a variety of contexts to discover when vibrancy enhances the appearance and improves communication.

**Choose a background blending mode that complements your interface design.** desktop defines two modes that blend background content: behind window and within window. BlendingMode.
