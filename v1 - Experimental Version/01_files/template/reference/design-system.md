# New Balance Korea · Mobile Design System
> Platform: iOS/Android mobile e-commerce · Viewport: 390px (iPhone 14/15)  
> Version: 1.0 · ASD-STE100 Simplified English

---

## 1. Design Tokens

Tokens are the single source of truth. Use token names in code. Do not use raw values.

### 1.1 Color Tokens

#### Brand
| Token | Value | Use |
|-------|-------|-----|
| `color.brand.primary` | `#D1122C` | CTA button fill · "Best" badge · selected state |
| `color.brand.primary.dark` | `#B80F26` | CTA button border (depth stroke) |

#### Neutral
| Token | Value | Use |
|-------|-------|-----|
| `color.neutral.0` | `#FFFFFF` | Page bg · card bg · CTA label on red |
| `color.neutral.50` | `#F5F5F5` | Section bg · thumbnail card fill |
| `color.neutral.100` | `#EEEEEE` | Dividers · header border · banner border |
| `color.neutral.150` | `#E9E9E9` | Cart button border |
| `color.neutral.200` | `#E8E8E8` | Empty star fill |
| `color.neutral.300` | `#D1D5DB` | Input / dropdown border |
| `color.neutral.500` | `#767676` | Secondary text · chevron icons |
| `color.neutral.700` | `#595959` | Tertiary text (review count) |
| `color.neutral.900` | `#111111` | Primary text · icons · FAB · active indicator |
| `color.neutral.1000` | `#000000` | Star fill · dropdown text |

#### Indicator
| State | Value | Opacity |
|-------|-------|---------|
| Active | `#111111` | 100% |
| Inactive | `#111111` | 10% |

---

### 1.2 Typography Tokens

#### Font Families
| Token | Family | Use |
|-------|--------|-----|
| `font.latin` | Inter | Headings · prices · button labels · badges · ratings |
| `font.korean` | Noto Sans KR | Korean body text · descriptions · helper labels |

#### Type Scale
| Token | Family | Weight | Size | Line-height | Use |
|-------|--------|--------|------|-------------|-----|
| `type.product-title` | Inter | 700 | 22px | auto | Product name |
| `type.price` | Inter | 700 | 16px | auto | Price number |
| `type.price-currency` | Inter | 600 | 16px | auto | Currency symbol (원) |
| `type.button` | Inter | 700 | 14px | auto | CTA text |
| `type.banner` | Inter | 700 | 14px | auto | Banner message |
| `type.badge` | Inter | 700 | 13px | auto | "Best" label |
| `type.rating-score` | Inter | 600 | 13px | auto | "4.9/5" |
| `type.review-count` | Inter | 400 | 13px | auto | "709개 리뷰 보기" |
| `type.dropdown` | Noto Sans KR | 400 | 14px | auto | "260 mm" |
| `type.body` | Noto Sans KR | 400 | 12px | 19px | Product description |
| `type.helper` | Noto Sans KR | 400 | 12px | auto | Field helper labels |

---

### 1.3 Spacing Tokens

| Token | Value | Use |
|-------|-------|-----|
| `space.1` | 4px | Badge padding (vertical) |
| `space.2` | 8px | Badge padding (horizontal) · banner padding · FAB gap (same group) |
| `space.3` | 12px | Section item gap · action bar button gap |
| `space.4` | 16px | Page horizontal padding · icon gap (header) · banner padding (h) |
| `space.5` | 40px | FAB gap (between groups) |
| `space.bottom-safe` | 104px | Product info bottom padding (thumb scroll clearance) |

---

### 1.4 Radius Tokens

| Token | Value | Use |
|-------|-------|-----|
| `radius.sm` | 4px | Badges · thumbnail cards |
| `radius.md` | 8px | Buttons · dropdowns · banner card |
| `radius.lg` | 20px | FAB circles |
| `radius.full` | 100px+ | Carousel pills · avatar circles |

---

### 1.5 Shadow Tokens

#### `shadow.button` — 5-layer progressive lift
```
0   5px  10px rgba(0,0,0,0.10)
0  19px  19px rgba(0,0,0,0.09)
0  43px  26px rgba(0,0,0,0.05)
0  76px  30px rgba(0,0,0,0.01)
0 119px  33px rgba(0,0,0,0.00)
```

#### `shadow.fab`
```
0 4px 34px rgba(0,0,0,0.25)
```

---

## 2. Layout

| Property | Value |
|----------|-------|
| Frame width | 390px |
| Horizontal gutter | `space.4` (16px) left + right |
| Primary flow | Vertical (top → bottom) |

### Section Spacing Reference
| Section | Top pad | Bottom pad | Internal gap |
|---------|---------|------------|--------------|
| Header | 0px | — | space-between |
| Product Info | 12px | 104px | `space.3` |
| Product Details | 0px | — | `space.4` between subsections |
| Text Block | 0px | — | `space.2` |
| Action Bar | `space.2` | `space.2` | `space.3` |
| Welcome Banner | `space.2` | `space.2` | `space.3` |

---

## 3. Components

### 3.1 Badge
```
bg:            color.brand.primary
text:          color.neutral.0 · type.badge
padding:       space.1 (v) / space.2 (h)
border-radius: radius.sm
```

### 3.2 Thumbnail Card
```
size:          ~113 × 112px
bg:            color.neutral.50
border-radius: radius.sm
gap:           ~9.6px between cards
state/selected: 1px border · color.brand.primary
```

### 3.3 Carousel Indicator
```
shape:   pill — 34 × 4px
radius:  radius.full
gap:     space.2
active:  color.neutral.900 @ 100%
inactive: color.neutral.900 @ 10%
```

### 3.4 Dropdown / Select
```
height:  44px
bg:      color.neutral.0
border:  1px · color.neutral.300
radius:  radius.md
padding: space.4 (h)
chevron: color.neutral.500 · 2px stroke
text:    type.dropdown
```

### 3.5 CTA Buttons (Action Bar)

Two equal-width buttons side by side. Shared: `height 48px · radius.md · shadow.button`.

| Property | Primary (Purchase) | Secondary (Cart) |
|----------|--------------------|------------------|
| Fill | `color.brand.primary` | `color.neutral.0` |
| Border | 1px `color.brand.primary.dark` | 1px `color.neutral.150` |
| Label color | `color.neutral.0` | `color.neutral.900` |
| Label style | `type.button` | `type.button` |

### 3.6 FAB (Floating Action Button)
```
size:    40 × 40px
shape:   circle (radius.lg)
bg:      color.neutral.900
icon:    color.neutral.0
shadow:  shadow.fab
gap (group):    space.2
gap (between groups): space.5
```

### 3.7 Avatar Circle
```
size:    32 × 32px (banner) / 40 × 40px (FAB area)
shape:   full circle (radius.full)
layout:  overlapping stack
```

### 3.8 Header
```
height:  56px
padding: space.4 (h)
layout:  horizontal · space-between
icon-gap: space.4
border:  1px bottom · color.neutral.100
```

### 3.9 Welcome Banner
```
bg:      color.neutral.0
border:  1px · color.neutral.100
radius:  radius.md
padding: space.4 (h)
text:    type.banner · color.neutral.900
```

---

## 4. Iconography

| Property | Value |
|----------|-------|
| Style | Outline (stroke-based) |
| Stroke weight | 2px |
| Color (header) | `color.neutral.900` |
| Color (on dark) | `color.neutral.0` |
| Size range | 17–22px (context-scaled) |
| Icons used | Search · Shopping bag · Hamburger · Chevron down · Arrow up · Share/export |

---

## 5. Design Principles

1. **High contrast, minimal palette.** Near-black text on white. One brand-red accent for CTAs and selections only.
2. **Weight = hierarchy.** Bold for headings and interactive labels. Regular for body. Size range is tight (12–22px).
3. **Elevation = interaction signal.** Multi-layer shadows on buttons and FABs. Page itself stays flat.
4. **Bilingual type pairing.** Inter for Latin text, numbers, UI labels. Noto Sans KR for Korean body copy. Both are sans-serif with matched x-heights.
5. **Compact mobile layout.** 390px width. 16px gutters. Tight vertical rhythm. Horizontal scroll for thumbnail and carousel sections.

---

## 6. Usage Rules (ASD-STE100)

- Use token names in all code and documentation. Do not use raw hex values.
- Do not add new colors. Add new use cases to existing tokens.
- Do not change `shadow.button` layer count. The shadow stack is intentional.
- Maintain bilingual font pairing. Do not substitute either family.
- Do not remove the 1px selected-state border on thumbnail cards. It is the only selection indicator.
