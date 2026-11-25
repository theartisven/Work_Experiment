name: html-to-figma
tools:
  - Figma Agent
  - Figma MCP
  - Figma Console MCP

procedure:
1. Examine the HTML file.
2. Check the first 10 text elements.
3. If the text is not in English, make a copy of the file and translate the text into English.
4. Plan how a UI/UX designer creates this layout in Figma.
   - Separate the design by main screens.
   - Separate layered elements, such as overlays or drawers.
   - Separate major state changes, such as tabs.
5. Show the plan as a list to the user, and ask for confirmation.
6. Build the Figma design in stages:
   - First, create one screen to test the Figma output.
   - If the user approves the test screen, create the remaining screens in groups of three.
