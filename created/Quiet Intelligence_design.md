## Overview

The system is a restrained enterprise workspace with a softly editorial character. IBM Plex Serif gives page headings a formal, readable presence, while Inter keeps controls, tables, conversations, and metadata clear and operational. The screens feel spacious and highly structured, with near-white surfaces, quiet borders, and purple reserved for actions and selection.

## Colors

- **Primary** (#5833A1): Brand and action color for selected navigation, active pagination, links, and focused states.
- **Heading** (#505050): High-emphasis page titles and major editorial headings.
- **Background** (#FAFAFA): Main application surface.
- **Card Surface** (#FFFFFF): Cards, panels, tables, inputs, and overlays.
- **Neutral** (#52525C): Primary body, table, label, and secondary text.
- **Muted Text** (#71717A): Descriptions, helper text, metadata, and placeholders.
- **Border** (#E4E4E7): Dividers, table borders, input borders, and card outlines.
- **Risk** (#F04438): Risk text and alert status.
- **Opportunity** (#008236): Opportunity text and positive status.
- **Need Review** (#737373): Neutral review and pending status.
- **Custom** (#4F46E5): Custom status and selected labels.

Purple is the primary brand and action color. Red, green, and muted indigo are reserved for meaningful status information rather than decoration.

## Typography

- **Headline Font**: IBM Plex Serif, Regular.
- **Body Font**: Inter, Regular.
- **Label Font**: Inter, Regular or Semi Bold.

Page titles use 48 px with approximately 64 px line height. Supporting headings range from 18 px to 32 px. Body and table text use 14 px at 400 weight, approximately 17 px line height, and 0.28 px letter spacing. Labels use 12 px or 14 px at 400 or 600 weight. Captions use 12 px at 400 weight with approximately 0.24 px letter spacing.

Semi Bold 600 is used for names, row emphasis, active controls, and short labels. The hierarchy relies on serif scale for editorial framing and Inter weight and size for operational scanning.

## Elevation

Depth comes primarily from surface separation and thin outlines rather than shadows.

- Cards and table containers use `#FFFFFF` surfaces, 1 px `#E4E4E7` borders, and 8 px to 12 px radii.
- Inputs use `#FFFFFF` surfaces, 1 px neutral borders, and 8 px to 12 px radii.
- Preset cards use white surfaces with restrained borders and no dominant shadow.
- Overlays and elevated content may use modest shadows, but the canonical product screens remain nearly flat.
- Hover states use surface tint or border emphasis instead of large offsets or exaggerated elevation.

## Components

**Navigation Rail**

The compact navigation rail is approximately 72 px wide. Icons and active items use 32 px to 40 px control areas, with purple surfaces or indicators for selection.

**Buttons**

Primary buttons use 36 px to 40 px heights, 12 px horizontal padding, 8 px radius, and white 14 px Semi Bold text on `#5833A1`. Secondary buttons use white surfaces, `#E4E4E7` borders, 8 px radii, and neutral text. Ghost actions use transparent surfaces with a hover tint.

**Inputs and Search**

Inputs use 40 px heights, 8 px to 12 px radii, `#FFFFFF` surfaces, 1 px borders, 12 px or 14 px text, and 12 px horizontal padding. Search fields use the same surface and border treatment with a trailing search icon. The chat composer is a larger multiline input with a bottom attachment and action row.

**Tabs**

Tabs use 12 px or 14 px Inter labels. The selected tab uses a neutral or purple emphasis, Semi Bold weight, or a text underline.

**Pills**

Pills use 24 px to 32 px heights, 16 px to 20 px horizontal padding, 999 px radii, neutral borders, and 12 px text. Semantic pills use pale tinted surfaces with matching text and icon colors.

**Tables**

Headers use 12 px or 14 px Semi Bold text. Rows use 14 px Inter text and 64 px to 72 px heights. Row separation uses 1 px bottom borders rather than alternating fills. Main text columns are left aligned, while numeric and status columns maintain consistent grid alignment.

**Cards**

Cards use 8 px to 12 px radii, 16 px to 24 px padding, 1 px borders, and white surfaces. Preset cards use a structured preview area followed by a 14 px title and 14 px description.

**Badges and Status**

Status badges use small tinted surfaces, matching semantic text, and 12 px Inter text. They remain compact and appear inline rather than as large alerts.

**Pagination**

Pagination controls use 28 px to 32 px squares with 8 px radii. The selected page uses a purple or dark surface with white text; adjacent controls use neutral text and minimal borders.

## Do's and Don'ts

- Use IBM Plex Serif only for editorial page headings.
- Use Inter for operational interface text, controls, tables, and metadata.
- Use purple for active actions and selected states; avoid it as decorative background.
- Keep surfaces white or near-white and separate content with thin neutral borders.
- Preserve 12 px to 24 px internal spacing and 8 px to 12 px component radii.
- Use 600 weight for names, actions, labels, and key table values.
- Keep body text at 14 px and metadata at 12 px.
- Use semantic red and green only for clearly meaningful status.
- Avoid heavy shadows, large gradients, oversized cards, and decorative dividers.
- Avoid mixing serif typography into tables, controls, or body content.
