---
title: "Image views"
description: "An image view displays a single image - or in some cases, an animated sequence of images - on a transparent or opaque background. Within an image view, you can stretch, scale, size to fit, or pin the image to a specif..."

---

# Image views

An image view displays a single image - or in some cases, an animated sequence of images - on a transparent or opaque background.

---

Within an image view, you can stretch, scale, size to fit, or pin the image to a specific location. Image views are typically not interactive.
## Best practices

**Use an image view when the primary purpose of the view is simply to display an image.** In rare cases where you might want an image to be interactive, configure a system-provided button to display the image instead of adding button behaviors to an image view.

**If you want to display an icon in your interface, consider using a symbol or interface icon instead of an image view.** system symbols provides a large library of streamlined, vector-based images that you can render with various colors and opacities. An icon (also called a glyph or template image) is typically a bitmap image in which the nontransparent pixels can receive color. Both symbols and interface icons can use the accent colors people choose.
## Content

An image view can contain rich image data in various formats, like PNG, JPEG, and PDF. For more guidance, see Images.

**Take care when overlaying text on images.** Compositing text on top of images can decrease both the clarity of the image and the legibility of the text. To help improve the results, ensure the text contrasts well with the image, and consider ways to make the text object stand out, like adding a text shadow or background layer.

**Aim to use a consistent size for all images in an animated sequence.** When you prescale images to fit the view, the system doesn’t have to perform any scaling. In cases where the system must do the scaling, performance is generally better when all images are the same size and shape.
## Platform considerations

*No additional considerations for mobile or tablet.*

### Desktop (desktop)

**If your app needs an editable image view, use an image well.** An image well is an image view that supports copying, pasting, dragging, and using the Delete key to clear its content.

**Use an image button instead of an image view to make a clickable image.** An image button contains an image or icon, appears in a view, and initiates an instantaneous app-specific action.
