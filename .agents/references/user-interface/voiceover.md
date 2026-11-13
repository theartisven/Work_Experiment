---
title: "screen reader"
description: "screen reader is a screen reader that lets people experience your app’s interface without needing to see the screen. By supporting screen reader, you help people who are blind or have low vision access information in..."

---

# screen reader

screen reader is a screen reader that lets people experience your app’s interface without needing to see the screen.

---

By supporting screen reader, you help people who are blind or have low vision access information in your app and navigate its interface and content when they can’t see the display.

screen reader is supported in apps and games built for platform platforms. It’s also supported in apps and games developed in Unity using platform’s Unity plug-ins. For related guidance, see Accessibility.
## Descriptions

You inform screen reader about your app’s content by providing alternative text that explains your app’s interface and the content it displays.

**Provide alternative labels for all key interface elements.** screen reader uses alternative labels (which aren’t visible onscreen) to audibly describe your app’s interface. System-provided controls have generic labels by default, but you should provide more descriptive labels that convey your app’s functionality. Add labels to any custom elements your app defines. Be sure to keep your descriptions up-to-date as your app’s interface and content change. 

**Describe meaningful images.** If you don’t describe key images in your app’s content, people can’t use screen reader to fully experience them within your app. Because screen reader helps people understand the interface surrounding images too, such as nearby captions, describe only the information the image itself conveys.

**Make charts and other infographics fully accessible.** Provide a concise description of each infographic that explains what it conveys. If people can interact with the infographic to get more or different information, make these interactions available to people using screen reader, too. The accessibility APIs offer ways to represent custom interactive elements so that assistive technologies can help people use them. 

**Exclude purely decorative images from screen reader.** It’s unnecessary to describe images that are decorative and don’t convey useful or actionable information. Excluding these images shows respect for people’s time and reduces cognitive load when they use screen reader. 
## Navigation

**Use titles and headings to help people navigate your information hierarchy.** The title is the first information someone receives from an assistive technology when arriving on a page or screen in your app. Offer unique titles that succinctly describe each page’s content and purpose. Likewise, use accurate section headings that help people build a mental model of each page’s information hierarchy.

**Specify how elements are grouped, ordered, or linked.** Proximity, alignment, and other visible contextual cues help sighted people perceive the relationships between elements. Examine your app for places where relationships among elements are visual only. Then, describe these relationships to screen reader.

screen reader reads elements in the same order people read content in the their active language and locale. For example, in US English, this is top-to-bottom, left-to-right. In the ungrouped example below, screen reader describes each image before moving on to the captions. In the grouped example, screen reader describes each image with its respective caption.

**Inform screen reader when visible content or layout changes occur.** People may find an unexpected content or layout change confusing because it means their mental map of the content is no longer accurate. It’s crucial to report visible changes so screen reader and other assistive technologies can help people update their understanding of the content. 

**Support the screen reader rotor when possible.** People can use an interface element called the screen reader rotor to navigate a document or webpage by headings, links, and other content types. You can help people navigate content in your app by identifying these elements to the rotor. The rotor can also bring up the braille keyboard. 
## Platform considerations

*No additional considerations for mobile, tablet, desktop, TV platform, or watch device.*
