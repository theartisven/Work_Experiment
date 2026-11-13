# Figma Combined Tool Reference

> **Rule:** CONSOLE = primary. MCP = fallback when CONSOLE fails. MCP-only tools have no fallback.

---

## Connection & Health

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `figma_get_status` | Figma Console | Checks whether the Figma connection is working. | --- |
| `figma_diagnose` | Figma Console | Looks for common connection or sign-in problems. | Use `figma_diagnose` (MCP) for a friendlier health report with tips. |
| `figma_reconnect` | Figma Console | Tries to reconnect to Figma. | --- |
| `figma_reload_plugin` | Figma Console | Restarts the Figma bridge plugin. | --- |

---

## Reading & Understanding Designs

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `figma_list_open_files` | Figma Console | Shows Figma files currently connected. | --- |
| `figma_get_file_data` | Figma Console | Reads the layers and basic details in a design file. | Use `get_metadata` (MCP) for a quick outline of the design. |
| `figma_get_file_for_plugin` | Figma Console | Reads file structure and extra details used by plugins. | Use `get_metadata` (MCP) as partial fallback. |
| `figma_navigate` | Figma Console | Opens or switches to a Figma file or location. | --- |
| `figma_get_selection` | Figma Console | Tells you what is selected in Figma. | --- |
| `figma_get_annotations` | Figma Console | Reads notes attached to a design object. | --- |
| `figma_get_annotation_categories` | Figma Console | Lists the kinds of design notes available. | --- |
| `figma_capture_screenshot` | Figma Console | Takes a picture of the current design. | Use `get_screenshot` (MCP) to capture selected design area. |
| `figma_take_screenshot` | Figma Console | Takes a screenshot to check how a design looks. | Use `get_screenshot` (MCP) as fallback. |
| `get_design_context` | Figma MCP only | Turns a selected Figma design into code (React/HTML). | --- |
| `get_figjam` | Figma MCP only | Converts a FigJam board into a machine-readable format. | --- |

---

## Node Manipulation

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `figma_set_description` | Figma Console | Adds or changes a design object's description. | --- |
| `figma_set_annotations` | Figma Console | Adds or changes notes attached to a design object. | --- |
| `figma_create_child` | Figma Console | Adds a new object inside another object. | Use `use_figma` (MCP) for general creation. |
| `figma_clone_node` | Figma Console | Makes a copy of a design object. | Use `use_figma` (MCP) for general editing. |
| `figma_delete_node` | Figma Console | Removes a design object. | Use `use_figma` (MCP) as fallback. |
| `figma_move_node` | Figma Console | Moves a design object. | Use `use_figma` (MCP) as fallback. |
| `figma_resize_node` | Figma Console | Changes an object's width or height. | Use `use_figma` (MCP) as fallback. |
| `figma_rename_node` | Figma Console | Changes an object's layer name. | Use `use_figma` (MCP) as fallback. |
| `figma_set_fills` | Figma Console | Changes an object's fill color or image. | Use `use_figma` (MCP) as fallback. |
| `figma_set_strokes` | Figma Console | Changes an object's outline. | Use `use_figma` (MCP) as fallback. |
| `figma_set_image_fill` | Figma Console | Puts an image inside an object's fill. | Use `upload_assets` (MCP) to upload image first, then retry. |
| `figma_set_text` | Figma Console | Changes text and optionally its font settings. | Use `use_figma` (MCP) as fallback. |
| `figma_set_instance_properties` | Figma Console | Changes settings on a component copy. | Use `use_figma` (MCP) as fallback. |
| `figma_execute` | Figma Console | Runs custom JavaScript inside Figma. | Use `use_figma` (MCP) for guided editing without custom JS. |
| `figma_execute_across_files` | Figma Console | Runs custom JavaScript on several connected files. | --- |

---

## Generative & Import

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `create_new_file` | Figma MCP only | Makes a new blank Figma file, FigJam board, or Slides file. | --- |
| `generate_figma_design` | Figma MCP only | Turns a live website into editable Figma design layers. | --- |
| `upload_assets` | Figma MCP only | Uploads images or SVG icons into a Figma file. | --- |
| `generate_diagram` | Figma MCP only | Creates a FigJam diagram from text or Mermaid syntax. | --- |
| `html_to_figma` | Figma MCP only | Converts an HTML page into Figma design layers. | --- |
| `generate_image` | Figma MCP only | Makes a new image from a text prompt and places it in the design. | --- |

---

## Components & Libraries

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `figma_search_components` | Figma Console | Finds reusable design parts such as buttons or fields. | Use `search_design_system` (MCP) to search across libs. |
| `figma_get_component` | Figma Console | Shows information about a reusable design part. | Use `use_figma` (MCP) as fallback. |
| `figma_get_component_details` | Figma Console | Shows a component's options and settings. | --- |
| `figma_get_component_for_development` | Figma Console | Gets component details that help developers build it. | Use `get_design_context` (MCP) for code-ready output. |
| `figma_get_component_for_development_deep` | Figma Console | Gets more detailed information for building a component. | Use `get_design_context` (MCP) as fallback. |
| `figma_get_component_image` | Figma Console | Shows a picture of a component. | Use `get_screenshot` (MCP) as fallback. |
| `figma_instantiate_component` | Figma Console | Adds a reusable component to a design. | Use `use_figma` (MCP) as fallback. |
| `figma_create_component_set` | Figma Console | Groups component versions together. | --- |
| `figma_analyze_component_set` | Figma Console | Checks the versions in a component group. | --- |
| `figma_arrange_component_set` | Figma Console | Organizes components in a component group. | --- |
| `figma_add_component_property` | Figma Console | Adds a new setting to a component. | --- |
| `figma_edit_component_property` | Figma Console | Changes a component setting. | --- |
| `figma_delete_component_property` | Figma Console | Removes a component setting. | --- |
| `figma_create_slot` | Figma Console | Adds an open area where other content can go. | --- |
| `figma_add_slot_property` | Figma Console | Adds a setting to a component slot. | --- |
| `figma_append_to_slot` | Figma Console | Puts content into a component slot. | --- |
| `figma_get_slots` | Figma Console | Shows the slots in a component. | --- |
| `figma_reset_slot` | Figma Console | Clears a slot and restores its default. | --- |
| `figma_get_library_components` | Figma Console | Lists reusable parts in a Figma library. | Use `search_design_system` (MCP) as fallback. |
| `figma_get_library_component_by_key` | Figma Console | Finds one library component using its ID. | --- |
| `figma_import_library_variable` | Figma Console | Brings a variable from a Figma library into the file. | --- |

---

## Code Connect

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `get_code_connect_map` | Figma MCP only | Shows which Figma components are linked to which code components. | --- |
| `add_code_connect_map` | Figma MCP only | Creates a new link between a Figma component and a code component. | --- |
| `search_design_system` | Figma MCP only | Searches design libraries for components, styles, and variables. | --- |

---

## Variables & Design Tokens

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `figma_get_variables` | Figma Console | Lists design variables, groups, and modes. | Use `get_variable_defs` (MCP) for variable values in selection. |
| `figma_get_token_values` | Figma Console | Reads the values used by design tokens. | Use `get_variable_defs` (MCP) as fallback. |
| `figma_browse_tokens` | Figma Console | Opens a visual browser for design tokens. | --- |
| `figma_create_variable_collection` | Figma Console | Creates a group for design variables. | --- |
| `figma_create_variable` | Figma Console | Creates one design variable. | --- |
| `figma_batch_create_variables` | Figma Console | Creates many design variables at once. | --- |
| `figma_update_variable` | Figma Console | Changes a variable's value or note. | --- |
| `figma_batch_update_variables` | Figma Console | Changes many variable values at once. | --- |
| `figma_delete_variable` | Figma Console | Removes a design variable. | --- |
| `figma_delete_variable_collection` | Figma Console | Removes a whole group of variables. | --- |
| `figma_add_mode` | Figma Console | Adds a mode such as Light or Dark to a group. | --- |
| `figma_rename_mode` | Figma Console | Changes a mode's name. | --- |
| `figma_rename_variable` | Figma Console | Changes a variable's name. | --- |
| `figma_setup_design_tokens` | Figma Console | Creates a token group, modes, and variables together. | --- |
| `figma_export_tokens` | Figma Console | Copies Figma token values into code files. | --- |
| `figma_import_tokens` | Figma Console | Copies token values from code into Figma. | --- |

---

## Design System Inspection & Quality

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `figma_get_design_system_summary` | Figma Console | Gives a quick overview of reusable parts and tokens. | --- |
| `figma_get_design_system_kit` | Figma Console | Collects design-system details into one reference. | --- |
| `figma_audit_design_system` | Figma Console | Checks how complete and consistent the design system is. | --- |
| `figma_audit_design_system_report` | Figma Console | Creates a report about design-system quality. | --- |
| `figma_lint_design` | Figma Console | Finds possible design-rule problems. | --- |
| `figma_ds_analyze` | Figma Console | Examines the design system's structure. | --- |
| `figma_ds_extract_component` | Figma Console | Pulls component details out of a design system. | --- |
| `figma_ds_extract_tokens` | Figma Console | Pulls design tokens out of a design system. | --- |
| `figma_ds_scaffold` | Figma Console | Creates starter files for a design system. | --- |
| `figma_ds_setup_storybook` | Figma Console | Sets up Storybook materials for design components. | --- |
| `figma_ds_status` | Figma Console | Shows the design system's setup status. | --- |
| `figma_ds_verify` | Figma Console | Checks that design-system setup is correct. | --- |
| `figma_check_design_parity` | Figma Console | Compares a design with its built version. | --- |
| `figma_scan_code_accessibility` | Figma Console | Looks for accessibility problems in code. | --- |
| `figma_audit_component_accessibility` | Figma Console | Checks if a component is accessible to people with different needs. | --- |
| `figma_get_styles` | Figma Console | Reads colors, text, effects, and grid styles. | Use `get_variable_defs` (MCP) for variable-based styles. |
| `figma_get_text_styles` | Figma Console | Lists the text styles in a file. | Use `get_variable_defs` (MCP) as fallback. |

---

## History, Reviews & Comments

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `figma_get_file_versions` | Figma Console | Lists saved versions of a file. | --- |
| `figma_get_file_at_version` | Figma Console | Shows what the file looked like at an older version. | --- |
| `figma_get_changes_since_version` | Figma Console | Shows what changed after a chosen version. | --- |
| `figma_get_design_changes` | Figma Console | Summarizes design edits. | --- |
| `figma_diff_versions` | Figma Console | Compares two saved versions. | --- |
| `figma_blame_node` | Figma Console | Shows the change history for one design object. | --- |
| `figma_get_comments` | Figma Console | Reads comments on the file. | --- |
| `figma_post_comment` | Figma Console | Adds a comment to the file. | --- |
| `figma_delete_comment` | Figma Console | Removes a comment. | --- |
| `figma_generate_changelog` | Figma Console | Creates a list of design changes. | --- |
| `figma_generate_component_doc` | Figma Console | Creates notes that explain a component. | --- |

---

## Figma Slides

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `figma_list_slides` | Figma Console | Lists the slides in a presentation. | --- |
| `figma_get_focused_slide` | Figma Console | Shows which slide is selected. | --- |
| `figma_focus_slide` | Figma Console | Selects a slide. | --- |
| `figma_get_slide_content` | Figma Console | Reads the objects and text on a slide. | --- |
| `figma_get_slide_grid` | Figma Console | Shows how slides are arranged. | --- |
| `figma_create_slide` | Figma Console | Adds a blank slide. | --- |
| `figma_duplicate_slide` | Figma Console | Makes a copy of a slide. | --- |
| `figma_delete_slide` | Figma Console | Removes a slide. | --- |
| `figma_reorder_slides` | Figma Console | Changes the order of slides. | --- |
| `figma_skip_slide` | Figma Console | Hides a slide from the presentation or brings it back. | --- |
| `figma_add_text_to_slide` | Figma Console | Adds text to a slide. | --- |
| `figma_add_shape_to_slide` | Figma Console | Adds a shape to a slide. | --- |
| `figma_set_slide_background` | Figma Console | Changes a slide's background. | --- |
| `figma_get_slide_transition` | Figma Console | Checks how a slide changes to the next one. | --- |
| `figma_set_slide_transition` | Figma Console | Changes how a slide changes to the next one. | --- |
| `figma_set_slides_view_mode` | Figma Console | Changes how the slides are shown while editing. | --- |

---

## FigJam

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `figjam_get_board_contents` | Figma Console | Reads what's on the FigJam board. | Use `get_figjam` (MCP) to convert board to machine-readable format. |
| `figjam_get_connections` | Figma Console | Shows which board objects are connected. | --- |
| `figjam_create_section` | Figma Console | Adds a labeled area to group board items. | --- |
| `figjam_create_sticky` | Figma Console | Adds one sticky note. | --- |
| `figjam_create_stickies` | Figma Console | Adds many sticky notes at once. | --- |
| `figjam_create_shape_with_text` | Figma Console | Adds a shape with words inside. | --- |
| `figjam_create_connector` | Figma Console | Draws a line between board items. | --- |
| `figjam_create_table` | Figma Console | Adds a table to the board. | --- |
| `figjam_create_code_block` | Figma Console | Adds a box for code. | --- |
| `figjam_auto_arrange` | Figma Console | Lines up board items neatly. | --- |
| `generate_diagram` | Figma MCP only | Creates a FigJam diagram from text or Mermaid syntax. | --- |

---

## Console Debugging

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `figma_get_console_logs` | Figma Console | Shows messages and errors from the Figma bridge. | --- |
| `figma_clear_console` | Figma Console | Clears the bridge's saved messages. | --- |
| `figma_watch_console` | Figma Console | Watches for new bridge messages. | --- |

---

## Generative Plugins & Shaders

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `list_generative_plugins` | Figma MCP only | Shows all generative plugins available in the library. | --- |
| `create_generative_plugin` | Figma MCP only | Gives a starter kit to build a new generative plugin. | --- |
| `list_shaders` | Figma MCP only | Lists all shader effects and fills in the library. | --- |
| `create_shader` | Figma MCP only | Helps create a new shader effect or fill. | --- |

---

## Account & Identity

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `whoami` | Figma MCP only | Shows which Figma account is logged in and what plan it has. | --- |