---
title: "Searching"
description: "People use various search techniques to find content on their device, within an app, and within a document or file. To search for content within an app, people generally expect to use a search field. When it makes sen..."

---

# Searching

People use various search techniques to find content on their device, within an app, and within a document or file.

---

To search for content within an app, people generally expect to use a search field. When it makes sense, you can personalize the search experience by using what you know about how people interact with your app. For example, you might display recent searches, search suggestions, completions, or corrections based on terms people searched earlier in your app.

In some cases, people appreciate the ability to scope a search or filter the results. For example, people might want to search for items by specifying attributes like creation date, file size, or file type. You can also help people find content within an open document or file by implementing ways to find content in a window or page in your mobile, tablet, or desktop app.

In mobile, tablet, and desktop, search helps people find content across all apps in the system and on the web. When you index and provide information about your app’s content, people can use search to find content your app contains without opening it first. 
## Best practices

**If search is important, give it a primary position in your app or view.** For example, in the Notes app, a search field is in the bottom toolbar alongside other important actions. In apps that use tab bars, like Photos and TV, search is a dedicated tab.

**Aim to make your app’s content searchable through a single location.** People appreciate having one clearly identified location they can use to find anything they’re looking for in your app. For apps with clearly distinct sections, it may still be useful to offer a local search. For example, search acts as a filter on the current view when searching your songs and albums in the mobile Music app.

**Clearly display the current scope of a search.** Use a descriptive placeholder text, a scope bar, or a title to help reinforce what someone is currently searching. For example, in the mail app app there is always a clear reference to the mailbox someone is searching.

**Provide suggestions to make searching easier.** When you display a personʼs recent searches before they start typing or offer predictive search suggestions while they’re typing, you can help people search faster and type less. 

**Take privacy into consideration before displaying search history.** People might not appreciate having their search history appear where others might see it. If you do show search history, provide a way for people to clear it if they want.
## Systemwide search

**Make your app’s content searchable in search.** You can share content with search by making it indexable and specifying descriptive attributes known as *metadata*. search extracts, stores, and organizes this information to allow for fast, comprehensive searches.

**Define metadata for custom file types you handle.** Supply a search File Importer plug-in that describes the types of metadata your file format contains. 

**Use search to offer advanced file-search capabilities within the context of your app.** For example, you might include a button that instantly initiates a search search based on the current selection. You might then display a custom view that presents the search results or a filtered subset of them.

**Prefer using the system-provided open and save views.** The system-provided open and save views generally include a built-in search field that people can use to search and filter the entire system. For related guidance, see File management.

**Implement a Quick Look generator if your app produces custom file types.** A Quick Look generator helps search and other apps show previews of your documents. 
## Platform considerations

*No additional considerations for mobile, tablet, desktop, TV platform, XR platform, or watch device.*
