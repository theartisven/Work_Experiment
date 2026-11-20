---
title: "Keyboards"
description: "A physical keyboard can be an essential input device for entering text, playing games, controlling apps, and more. People can connect a physical keyboard to any device except watch. computer users tend to use a physic..."

---

# Keyboards

A physical keyboard can be an essential input device for entering text, playing games, controlling apps, and more.

---

People can connect a physical keyboard to any device except watch. computer users tend to use a physical keyboard all the time and tablet users often do. Many games work well with a physical keyboard, and people can prefer using one instead of a virtual keyboard when entering a lot of text.

Keyboard users often appreciate using keyboard shortcuts to speed up their interactions with apps and games. A *keyboard shortcut* is a combination of a primary key and one or more modifier keys (Control, Option, Shift, and Command) that map to a specific command. A keyboard shortcut in a game - called a *key binding* - often consists of a single key.

platform defines standard keyboard shortcuts to work consistently across the system and most apps, helping people transfer their knowledge to new experiences. Some apps define custom keyboard shortcuts for the app-specific commands people use most; most games define custom key bindings that make it quick and efficient to use the keyboard to control the game. 
## Best practices

**Support full keyboard access when possible.** Available in mobile, tablet, desktop, and XR platform, full keyboard access lets people navigate and activate windows, menus, controls, and system features using only the keyboard. To test full keyboard access in your app or game, turn it on in the Accessibility area of the system-supplied Settings app. 

> **Important:** Although tablet supports keyboard navigation in text fields, text views, and sidebars, and provides APIs you can use to support it in collection views and other custom views, avoid supporting keyboard navigation for controls, such as buttons, segmented controls, and switches. Instead, let people use full keyboard access to activate controls, navigate to all onscreen components, and perform gesture-based interactions like drag and drop. for developer guidance, see Focus-based navigation.

**Respect standard keyboard shortcuts.** While using most apps, people generally expect to rely on the standard keyboard shortcuts that work in other apps and throughout the system. If your app offers a unique action that people perform frequently, prefer creating a custom shortcut for it instead of repurposing a standard one that people associate with a different action. While playing a game, people may expect to use certain standard keyboard shortcuts - such as Command–Q to quit the game - but they also expect to be able to modify each game’s key bindings to fit their personal play style. 
## Standard keyboard shortcuts

**In general, don’t repurpose standard keyboard shortcuts for custom actions.** People can get confused when the shortcuts they know work differently in your app or game. Only consider redefining a standard shortcut if its action doesn’t make sense in your experience. For example, if your app doesn’t support text editing, it doesn’t need a text-styling command like Italic, so you might repurpose Command–I for an action that has more relevance, like Get Info.

People expect each of the following standard keyboard shortcuts to perform the action listed in the table below.

| Primary key | Keyboard shortcut | Action |
| --- | --- | --- |
| Space | Ctrl-Space | Show or hide the search search field. |
| | Shift-Ctrl-Space | Varies. |
| | Alt-Ctrl-Space | Show the search search results window. |
| | Ctrl-Ctrl-Space | Show the Special Characters window. |
| Tab | Shift-Tab | Navigate through controls in a reverse direction. |
| | Ctrl-Tab | Move forward to the next most recently used app in a list of open apps. |
| | Shift-Ctrl-Tab | Move backward through a list of open apps (sorted by recent use). |
| | Ctrl-Tab | Move focus to the next group of controls in a dialog or the next table (when Tab moves to the next cell). |
| | Ctrl-Shift-Tab | Move focus to the previous group of controls. |
| Esc | Esc | Cancel the current action or process. |
| Esc | Alt-Ctrl-Esc | Open the Force Quit dialog. |
| Eject | Ctrl-Ctrl-Eject | Quit all apps (after changes have been saved to open documents) and restart the computer. |
| | Ctrl-Alt-Ctrl-Eject | Quit all apps (after changes have been saved to open documents) and shut the computer down. |
| F1 | Ctrl-F1 | Toggle full keyboard access on or off. |
| F2 | Ctrl-F2 | Move focus to the menu bar. |
| F3 | Control- F3 | Move focus to the dock. |
| F4 | Ctrl-F4 | Move focus to the active (or next) window. |
| | Ctrl-Shift-F4 | Move focus to the previously active window. |
| F5 | Ctrl-F5 | Move focus to the toolbar. |
| | Ctrl-F5 | Turn screen reader on or off. |
| F6 | Ctrl-F6 | Move focus to the first (or next) panel. |
| | Ctrl-Shift-F6 | Move focus to the previous panel. |
| F7 | Ctrl-F7 | Temporarily override the current keyboard access mode in windows and dialogs. |
| F8 | | Varies. |
| F9 | | Varies. |
| F10 | | Varies. |
| F11 | | Show desktop. |
| F12 | | Hide or display Dashboard. |
| Grave accent | Ctrl-Grave accent | Activate the next open window in the frontmost app. |
| | Shift-Ctrl-Grave accent | Activate the previous open window in the frontmost app. |
| | Alt-Ctrl-Grave accent | Move focus to the window drawer. |
| Hyphen (-) | Ctrl-Hyphen | Decrease the size of the selection. |
| | Alt-Ctrl-Hyphen | Zoom out when screen zooming is on. |
| Left bracket ({) | Ctrl-Left bracket | Left-align a selection. |
| Right bracket (}) | Ctrl-Right bracket | Right-align a selection. |
| Pipe (\|) | Ctrl-Pipe | Center-align a selection. |
| Colon (:) | Ctrl-Colon | Display the Spelling window. |
| Semicolon (;) | Ctrl-Semicolon | Find misspelled words in the document. |
| Comma (,) | Ctrl-Comma | Open the app’s settings window. |
| | Ctrl-Alt-Ctrl-Comma | Decrease screen contrast. |
| Period (.) | Ctrl-Period | Cancel an operation. |
| | Ctrl-Alt-Ctrl-Period | Increase screen contrast. |
| Question mark (?) | Ctrl-Question mark | Open the app’s Help menu. |
| Forward slash (/) | Alt-Ctrl-Forward slash | Turn font smoothing on or off. |
| Equal sign (=) | Shift-Ctrl-Equal sign | Increase the size of the selection. |
| | Alt-Ctrl-Equal sign | Zoom in when screen zooming is on. |
| 3 | Shift-Ctrl-3 | Capture the screen to a file. |
| | Ctrl-Shift-Ctrl-3 | Capture the screen to the Clipboard. |
| 4 | Shift-Ctrl-4 | Capture a selection to a file. |
| | Ctrl-Shift-Ctrl-4 | Capture a selection to the Clipboard. |
| 8 | Alt-Ctrl-8 | Turn screen zooming on or off. |
| | Ctrl-Alt-Ctrl-8 | Invert the screen colors. |
| A | Ctrl-A | Select every item in a document or window, or all characters in a text field. |
| | Shift-Ctrl-A | Deselect all selections or characters. |
| B | Ctrl-B | Boldface the selected text or toggle boldfaced text on and off. |
| C | Ctrl-C | Copy the selection to the Clipboard. |
| | Shift-Ctrl-C | Display the Colors window. |
| | Alt-Ctrl-C | Copy the style of the selected text. |
| | Ctrl-Ctrl-C | Copy the formatting settings of the selection and store on the Clipboard. |
| D | Alt-Ctrl-D | Show or hide the dock. |
| | Ctrl-Ctrl-D | Display the definition of the selected word in the Dictionary app. |
| E | Ctrl-E | Use the selection for a find operation. |
| F | Ctrl-F | Open a Find window. |
| | Alt-Ctrl-F | Jump to the search field control. |
| | Ctrl-Ctrl-F | Enter full screen. |
| G | Ctrl-G | Find the next occurrence of the selection. |
| | Shift-Ctrl-G | Find the previous occurrence of the selection. |
| H | Ctrl-H | Hide the windows of the currently running app. |
| | Alt-Ctrl-H | Hide the windows of all other running apps. |
| I | Ctrl-I | Italicize the selected text or toggle italic text on or off. |
| | Ctrl-I | Display an Info window. |
| | Alt-Ctrl-I | Display an inspector window. |
| J | Ctrl-J | Scroll to a selection. |
| M | Ctrl-M | Minimize the active window to the dock. |
| | Alt-Ctrl-M | Minimize all windows of the active app to the dock. |
| N | Ctrl-N | Open a new document. |
| O | Ctrl-O | Display a dialog for choosing a document to open. |
| P | Ctrl-P | Display the Print dialog. |
| | Shift-Ctrl-P | Display the Page Setup dialog. |
| Q | Ctrl-Q | Quit the app. |
| | Shift-Ctrl-Q | Log out the person currently logged in. |
| | Alt-Shift-Ctrl-Q | Log out the person currently logged in without confirmation. |
| S | Ctrl-S | Save a new document or save a version of a document. |
| | Shift-Ctrl-S | Duplicate the active document or initiate a Save As. |
| T | Ctrl-T | Display the Fonts window. |
| | Alt-Ctrl-T | Show or hide a toolbar. |
| U | Ctrl-U | Underline the selected text or turn underlining on or off. |
| V | Ctrl-V | Paste the Clipboard contents at the insertion point. |
| | Shift-Ctrl-V | Paste as (Paste as Quotation, for example). |
| | Alt-Ctrl-V | Apply the style of one object to the selection. |
| | Alt-Shift-Ctrl-V | Paste the Clipboard contents at the insertion point and apply the style of the surrounding text to the inserted object. |
| | Ctrl-Ctrl-V | Apply formatting settings to the selection. |
| W | Ctrl-W | Close the active window. |
| | Shift-Ctrl-W | Close a file and its associated windows. |
| | Alt-Ctrl-W | Close all windows in the app. |
| X | Ctrl-X | Remove the selection and store on the Clipboard. |
| Z | Ctrl-Z | Undo the previous operation. |
| | Shift-Ctrl-Z | Redo (when Undo and Redo are separate commands rather than toggled using Ctrl-Z). |
| Right arrow | Ctrl-Right arrow | Change the keyboard layout to current layout of Roman script. |
| | Shift-Ctrl-Right arrow | Extend selection to the next semantic unit, typically the end of the current line. |
| | Shift-Right arrow | Extend selection one character to the right. |
| | Alt-Shift-Right arrow | Extend selection to the end of the current word, then to the end of the next word. |
| | Ctrl-Right arrow | Move focus to another value or cell within a view, such as a table. |
| Left arrow | Ctrl-Left arrow | Change the keyboard layout to current layout of system script. |
| | Shift-Ctrl-Left arrow | Extend selection to the previous semantic unit, typically the beginning of the current line. |
| | Shift-Left arrow | Extend selection one character to the left. |
| | Alt-Shift-Left arrow | Extend selection to the beginning of the current word, then to the beginning of the previous word. |
| | Ctrl-Left arrow | Move focus to another value or cell within a view, such as a table. |
| Up arrow | Shift-Ctrl-Up arrow | Extend selection upward in the next semantic unit, typically the beginning of the document. |
| | Shift-Up arrow | Extend selection to the line above, to the nearest character boundary at the same horizontal location. |
| | Alt-Shift-Up arrow | Extend selection to the beginning of the current paragraph, then to the beginning of the next paragraph. |
| | Ctrl-Up arrow | Move focus to another value or cell within a view, such as a table. |
| Down arrow | Shift-Ctrl-Down arrow | Extend selection downward in the next semantic unit, typically the end of the document. |
| | Shift-Down arrow | Extend selection to the line below, to the nearest character boundary at the same horizontal location. |
| | Alt-Shift-Down arrow | Extend selection to the end of the current paragraph, then to the end of the next paragraph (include the paragraph terminator, such as Return, in cut, copy, and paste operations). |
| | Ctrl-Down arrow | Move focus to another value or cell within a view, such as a table. |

The system also defines several keyboard shortcuts for use with localized versions of the system, localized keyboards, keyboard layouts, and input methods. These shortcuts don’t correspond directly to menu commands.

| Keyboard shortcut | Action |
| --- | --- |
| Ctrl-Space | Toggle between the current and last input source. |
| Ctrl-Alt-Space | Switch to the next input source in the list. |
| [Modifier key]-Ctrl-Space | Varies. |
| Ctrl-Right arrow | Change keyboard layout to current layout of Roman script. |
| Ctrl-Left arrow | Change keyboard layout to current layout of system script. |
## Custom keyboard shortcuts

**Define custom keyboard shortcuts for only the most frequently used app-specific commands.** People appreciate using keyboard shortcuts for actions they perform frequently, but defining too many new shortcuts can make your app seem difficult to learn.

**Use modifier keys in ways that people expect.** For example, pressing Command while dragging moves items as a group, and pressing Shift while drag-resizing constrains resizing to the item’s aspect ratio. In addition, holding an arrow key moves the selected item by the smallest app-defined unit of distance until people release the key.

Here are the modifier keys and the symbols that represent them.

| Modifier key | Symbol | Recommended usage |
| --- | --- | --- |
| Command | *image: Keyboard Command* | Prefer the Command key as the main modifier key in a custom keyboard shortcut. |
| Shift | *image: Keyboard Shift* | Prefer the Shift key as a secondary modifier that complements a related shortcut. |
| Option | *image: Keyboard Option* | Use the Option modifier sparingly for less-common commands or power features. |
| Control | *image: Keyboard Control* | Avoid using the Control key as a modifier. The system uses Control in many systemwide features and shortcuts, like moving focus or capturing screenshots. |

> **Tip:** Some languages require modifier keys to generate certain characters. For example, on a French keyboard, Alt-5 generates the “{“ character. It’s usually safe to use the Command key as a modifier, but avoid using an additional modifier with characters that aren’t available on all keyboards. If you must use a modifier other than Command, prefer using it only with the alphabetic characters.

**List modifier keys in the correct order.** If you use more than one modifier key in a custom shortcut, always list them in this order: Control, Option, Shift, Command.

**Avoid adding Shift to a shortcut that uses the upper character of a two-character key.** People already understand that they must hold the Shift key to type the upper character of a two-character key, so it’s clearer to simply list the upper character in the shortcut. For example, the keyboard shortcut for Hide Status Bar is Ctrl-Slash, whereas the keyboard shortcut for Help is Ctrl-Question mark, not Shift-Ctrl-Slash.

**Let the system localize and mirror your keyboard shortcuts as needed.** The system automatically localizes a shortcut’s primary and modifier keys to support the currently connected keyboard; if your app or game switches to a right-to-left layout, the system automatically mirrors the shortcut. 

**Avoid creating a new shortcut by adding a modifier to an existing shortcut for an unrelated command.** For example, because people are accustomed to using Ctrl-Z for undoing an action, it would be confusing to use Shift-Ctrl-Z as the shortcut for a command that’s unrelated to undo and redo.
## Platform considerations

*No additional considerations for mobile, tablet, desktop, or TV platform. Not supported in watch device.*
