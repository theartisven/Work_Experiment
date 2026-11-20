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
| `figma_get_code_layers` | Figma Console | Finds Figma code layers on a page or across the file. | --- |
| `get_design_context` | Figma MCP only | Turns a selected Figma design into code (React/HTML by default; ask for any framework). | --- |
| `get_figjam` | Figma MCP only | Converts a FigJam board into XML (similar to `get_metadata` with screenshots). | --- |
| `get_metadata` | Figma MCP only | Gets a lightweight XML outline of a selection — layer IDs, names, types, positions, sizes. | --- |
| `get_screenshot` | Figma MCP only | Takes a screenshot of a selection so the agent can see the design. | --- |
| `get_variable_defs` | Figma MCP only | Returns variables and styles (colors, spacing, typography) used in a selection. | --- |
| `get_motion_context` | Figma MCP only | Returns keyframe animation data and ready-to-use CSS/Motion code snippets for a selection. | --- |
| `get_libraries` | Figma MCP only (Remote only) | Lists subscribed and available libraries for a Figma file. | --- |
| `download_assets` | Figma MCP only (Remote only) | Downloads exports and original source images for up to 20 nodes per call. | --- |

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
| `figma_set_fills` | Figma Console | Changes an object's fill color or image (supports OKLCH and Display P3). | Use `use_figma` (MCP) as fallback. |
| `figma_set_strokes` | Figma Console | Changes an object's outline (supports OKLCH and Display P3). | Use `use_figma` (MCP) as fallback. |
| `figma_set_image_fill` | Figma Console | Puts an image inside an object's fill. | Use `upload_assets` (MCP) to upload image first, then retry. |
| `figma_set_text` | Figma Console | Changes text and optionally its font settings, text wrap (balance/pretty), and variable-font axes. | Use `use_figma` (MCP) as fallback. |
| `figma_set_instance_properties` | Figma Console | Changes settings on a component copy. | Use `use_figma` (MCP) as fallback. |
| `figma_set_layout` | Figma Console | Sets auto layout or grid layout in one call with CSS-style grid tracks and child placement. | Use `figma_execute` (Console) with Plugin API layout code. |
| `figma_execute` | Figma Console | Runs custom JavaScript inside Figma. | Use `use_figma` (MCP) for guided editing without custom JS. |
| `figma_execute_across_files` | Figma Console | Runs custom JavaScript on several connected files. | --- |

---

## Generative & Import

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `create_new_file` | Figma MCP only (Remote only) | Makes a new blank Figma file, FigJam board, or Slides file. | --- |
| `generate_figma_design` | Figma MCP only (Remote only) | Turns a live website into editable Figma design layers. | --- |
| `upload_assets` | Figma MCP only (Remote only) | Uploads images or SVG icons (up to 60 files per call) into a Figma file. | --- |
| `generate_diagram` | Figma MCP only (Remote only) | Creates a FigJam diagram from a description or Mermaid syntax. | --- |
| `html_to_figma` | Figma MCP only (Remote only) | Converts a self-contained HTML document into Figma design layers. | --- |
| `generate_image` | Figma MCP only (Remote only) | Makes a new image from a text prompt and places it in the design (uses Figma AI credits). | --- |
| `generate_vector_illustration` | Figma MCP only (Remote only) | Generates editable vector graphics (icons or illustrations) from a text prompt (uses Figma AI credits). | --- |
| `send_code_to_figma` | Figma MCP only (Remote only) | Imports a local project into Figma as a Make file or code layer. | --- |
| `use_figma` | Figma MCP only (Remote only) | General-purpose write tool — creates, edits, deletes, or inspects content in Figma Design, FigJam, Slides, and Specs files. | --- |

---

## Motion & Animation

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `figma_apply_animation` | Figma Console | Animates layers using Figma Motion presets, custom animation styles, or keyframes bound to Timing/Easing tokens. | Use `figma_execute` (Console) with Plugin API animation code. |
| `figma_manage_animation_styles` | Figma Console | Creates, updates, or deletes Timing and Easing token libraries for animations. | --- |
| `figma_get_animations` | Figma Console | Reads the animations applied to a layer. | --- |
| `figma_remove_animation` | Figma Console | Removes animations from a layer. | --- |
| `figma_export_animation` | Figma Console | Exports a layer's animation as MP4, GIF, or WebM. | Use `export_video` (MCP) for MP4 export via REST API. |
| `export_video` | Figma MCP only (Remote only) | Exports an animated frame as an MP4 video via the REST API. | Use `figma_export_animation` (Console) as fallback. |

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
| `figma_create_component_set` | Figma Console | Groups component versions together from an axes matrix in one call. | --- |
| `figma_analyze_component_set` | Figma Console | Checks the versions in a component group. | --- |
| `figma_arrange_component_set` | Figma Console | Organizes components in a component group with labels. | --- |
| `figma_add_component_property` | Figma Console | Adds a new setting to a component. | --- |
| `figma_edit_component_property` | Figma Console | Changes a component setting. | --- |
| `figma_delete_component_property` | Figma Console | Removes a component setting. | --- |
| `figma_create_slot` | Figma Console | Adds a slot inside a component (Figma Slots, GA at Config 2026). | --- |
| `figma_add_slot_property` | Figma Console | Adds a setting to a component slot. | --- |
| `figma_append_to_slot` | Figma Console | Puts content into a component slot. | --- |
| `figma_get_slots` | Figma Console | Lists slots on a component, component set, or instance. | --- |
| `figma_reset_slot` | Figma Console | Clears a slot and restores its default. | --- |
| `figma_get_library_components` | Figma Console | Lists reusable parts in a Figma library (requires the library file URL). | Use `search_design_system` (MCP) as fallback. |
| `figma_get_library_component_by_key` | Figma Console | Finds one library component using its key — tries component sets then components. | --- |
| `figma_get_library_variables` | Figma Console | Lists library tokens; filterable by library name, collection name, or resolved type. Works on every Figma plan. | --- |
| `figma_import_library_variable` | Figma Console | Brings a variable from a Figma library into the file. | --- |
| `get_libraries` | Figma MCP only (Remote only) | Lists libraries already added to a file and those available to add. | --- |

---

## Code Connect

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `get_code_connect_map` | Figma MCP only | Shows which Figma components are linked to which code components. | --- |
| `add_code_connect_map` | Figma MCP only | Creates a new link between a Figma component and a code component. | --- |
| `search_design_system` | Figma MCP only (Remote only) | Searches design libraries for components, styles, and variables. | --- |

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
| `figma_setup_design_tokens` | Figma Console | Creates a token group, modes, and variables together (alias values via DTCG brace references). | --- |
| `figma_export_tokens` | Figma Console | Exports Figma variables to DTCG JSON, CSS custom properties, Tailwind, SCSS, TypeScript, Style Dictionary, or Tokens Studio. | --- |
| `figma_import_tokens` | Figma Console | Pushes token edits (DTCG or CSS) back into Figma variables, with dry-run preview support. | --- |

---

## Design System Inspection & Quality

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `figma_get_design_system_summary` | Figma Console | Gives a quick overview of reusable parts and tokens. | --- |
| `figma_get_design_system_kit` | Figma Console | Collects design-system details (tokens, components, styles, resolved values) into one reference. | --- |
| `figma_audit_design_system` | Figma Console | Checks how complete and consistent the design system is (six-category scored audit). | --- |
| `figma_audit_design_system_report` | Figma Console | Creates a scored design-system quality report with per-category drill-down. | --- |
| `figma_lint_design` | Figma Console | Finds possible design-rule problems. | --- |
| `figma_ds_analyze` | Figma Console | Scans a codebase for framework/styling detection, component inventory, and architecture classification. | --- |
| `figma_ds_extract_component` | Figma Console | Pulls component details out of a design system into a porting manifest with a CSF3 story scaffold. | --- |
| `figma_ds_extract_tokens` | Figma Console | Mines styling from a codebase into DTCG tokens with per-token provenance. | --- |
| `figma_ds_scaffold` | Figma Console | Generates the design-system package: token files, showcase pages, and framework peer deps. | --- |
| `figma_ds_setup_storybook` | Figma Console | Wires a fresh Storybook to the extraction with real theme layers and fonts. | --- |
| `figma_ds_status` | Figma Console | Shows the design system's setup and porting progress (persisted across sessions). | --- |
| `figma_ds_verify` | Figma Console | Deterministic fidelity evals and Figma round-trip readiness checks. | --- |
| `figma_check_design_parity` | Figma Console | Compares a Figma component with its built version (visual properties, spacing, tokens, accessibility, parity score). | --- |
| `figma_scan_code_accessibility` | Figma Console | Looks for accessibility problems in code (axe-core, 104 rules). | --- |
| `figma_audit_component_accessibility` | Figma Console | Checks if a component is accessible — state coverage, focus indicators, color-blind simulation. | --- |
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
| `figma_diff_versions` | Figma Console | Compares two saved versions with structured diffs including component property and binding changes. | --- |
| `figma_blame_node` | Figma Console | Shows the change history (who, when, what property) for one design object. | --- |
| `figma_get_comments` | Figma Console | Reads comments on the file. | Use `get_comments` (MCP) as fallback. |
| `figma_post_comment` | Figma Console | Adds a comment to the file. | --- |
| `figma_delete_comment` | Figma Console | Removes a comment. | --- |
| `figma_generate_changelog` | Figma Console | Creates a Markdown changelog from version history (optionally combined with `git log`). | --- |
| `figma_generate_component_doc` | Figma Console | Creates Markdown documentation explaining a component, including parity section. | --- |
| `get_comments` | Figma MCP only (Remote only) | Reads comment threads, reactions, attachments, and read/unread status from any file type. | Use `figma_get_comments` (Console) as fallback. |

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
| `figma_set_slide_transition` | Figma Console | Changes a slide transition (22 styles, 8 easing curves). | --- |
| `figma_set_slides_view_mode` | Figma Console | Changes how the slides are shown while editing. | --- |

---

## FigJam

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `figjam_get_board_contents` | Figma Console | Reads what's on the FigJam board. | Use `get_figjam` (MCP) to convert board to machine-readable format. |
| `figjam_get_connections` | Figma Console | Shows which board objects are connected. | --- |
| `figjam_create_section` | Figma Console | Adds a labeled area to group board items. | --- |
| `figjam_create_sticky` | Figma Console | Adds one sticky note (9 color options). | --- |
| `figjam_create_stickies` | Figma Console | Adds many sticky notes at once. | --- |
| `figjam_create_shape_with_text` | Figma Console | Adds a shape (diamond, ellipse, engineering shape) with words inside. | --- |
| `figjam_create_connector` | Figma Console | Draws a labeled line between board items for flowcharts. | --- |
| `figjam_create_table` | Figma Console | Adds a table to the board. | --- |
| `figjam_create_code_block` | Figma Console | Adds a box for code. | --- |
| `figjam_auto_arrange` | Figma Console | Lines up board items neatly. | --- |
| `generate_diagram` | Figma MCP only (Remote only) | Creates a FigJam diagram from a description or Mermaid syntax. | --- |

---

## Console Debugging

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `figma_get_console_logs` | Figma Console | Shows messages and errors from the Figma bridge. | --- |
| `figma_clear_console` | Figma Console | Clears the bridge's saved messages. | --- |
| `figma_watch_console` | Figma Console | Watches for new bridge messages in real time. | --- |

---

## Generative Plugins & Shaders

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `figma_apply_shader` | Figma Console | Applies a shader effect or fill to a node and sets its properties by name. | Use `figma_execute` (Console) with Plugin API shader code. |
| `figma_list_shaders` | Figma Console | Lists available shader effects and fills by name for use with `figma_apply_shader`. | --- |
| `list_generative_plugins` | Figma MCP only (Remote only) | Lists all generative plugins in your library (paginated). | --- |
| `get_generative_plugin` | Figma MCP only (Remote only) | Reads a generative plugin's source code by ID. | --- |
| `create_generative_plugin` | Figma MCP only (Remote only) | Creates a new generative plugin starter in your library. Requires `figma-generative-plugins` skill. | --- |
| `update_generative_plugin` | Figma MCP only (Remote only) | Updates a generative plugin's source; Figma builds, versions, and deploys. Requires `figma-generative-plugins` skill. | --- |
| `list_shaders` | Figma MCP only | Lists shader effects and fills in your account library (paginated). | --- |
| `get_shader` | Figma MCP only | Reads a shader's source code by ID. | --- |
| `create_shader` | Figma MCP only (Remote only) | Creates a new shader effect or fill starter. Requires `figma-shaders` skill. | --- |
| `update_shader` | Figma MCP only (Remote only) | Updates a shader's source; Figma builds, versions, and deploys. Requires `figma-shaders` skill. | --- |
| `list_file_shaders` | Figma MCP only (Remote only) | Lists shaders used in a specific file — works even for shaders you don't own. | --- |

---

## Figma Weave

> All tools in this section are **Figma MCP only**. They require a paid standalone Figma Weave account; runs use Weave credits. The agent confirms cost before any paid run.

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `weave_list_tools` | Figma MCP only (Remote only) | Lists Weave tools available in your active workspace. | --- |
| `weave_get_tool_inputs` | Figma MCP only (Remote only) | Gets the inputs a Weave tool needs before running. | --- |
| `weave_upload_asset` | Figma MCP only (Remote only) | Uploads an image, video, audio, or 3D model for use as a Weave tool input. | --- |
| `weave_run_tool` | Figma MCP only (Remote only) | Runs a published Weave tool (1–10 runs); confirms cost first. | --- |
| `weave_get_tool_run_output` | Figma MCP only (Remote only) | Gets the status and output of Weave tool runs. | --- |
| `weave_cancel_tool_run` | Figma MCP only (Remote only) | Cancels one or more in-progress Weave tool runs. | --- |
| `weave_find_model` | Figma MCP only (Remote only) | Finds a Weave model by name, returning its cost and required inputs. | --- |
| `weave_run_model` | Figma MCP only (Remote only) | Runs a Weave model directly without a published tool; confirms cost first. | --- |
| `weave_get_model_run_output` | Figma MCP only (Remote only) | Gets the status and output of model runs started with `weave_run_model`. | --- |

---

## Account & Identity

| Tool | Use | What it does | When fails |
| --- | --- | --- | --- |
| `whoami` | Figma MCP only (Remote only) | Shows which Figma account is logged in, all plans, and seat types. Required for creating plugins/shaders (`planKey`). | --- |