# WIREFRAME-CONVERSION-HANDOFF.md

## Purpose

Use this checklist when handing a wireframe, screenshot, Figma export, or visual reference to an agent for implementation.

The goal is to reduce first-pass mismatch by making the visual target explicit before coding starts.

This does not guarantee true pixel perfection from an incomplete wireframe. It does give the agent the information needed to make a close first-shot implementation and to know what must not be guessed.

## When To Use

Use this before:

- `*wireframe` planning
- starter homepage or page builds
- client page implementation from a screenshot or Figma export
- visual QA against an approved reference

For starter-system work, store the completed handoff inside the relevant mission-control wireframe package:

```txt
docs/wireframes/starter/<page-or-flow>-vN/
```

For client work, store it under:

```txt
docs/wireframes/clients/<client-name>/<page-or-flow>-vN/
```

## Minimum Handoff

If you want a fast but useful handoff, provide at least:

- visual reference file or Figma frame
- target page or route
- desktop reference viewport
- mobile reference viewport, if available
- match level: exact, close, or directional
- required font family
- known colors or brand palette
- page margin and section spacing expectations
- real assets versus placeholders
- must-match items
- what may be interpreted by the agent

## Pixel-Perfect Handoff Checklist

### 1. Reference Source

Provide:

- image, screenshot, Figma frame, or exported PNG
- exact file name or URL
- version number, such as `homepage-v1`
- whether the reference is approved or exploratory
- whether the image includes browser chrome, crop margins, or extra canvas

Helpful notes:

- If the reference is a screenshot, state the capture viewport.
- If the reference is a Figma export, state the frame size.
- If the reference is low fidelity, say which parts are intentional and which are rough placeholders.

### 2. Target Repo And Page

Provide:

- target repo
- target route
- operating mode
- whether this is starter-safe, client-specific, or registry-candidate work
- whether implementation should modify existing sections or create new ones

Example:

```txt
Target repo: paw-starter-kit
Route: /
Mode: Starter Governance Mode
Implementation type: reusable starter homepage section work
```

### 3. Viewports And Breakpoints

Provide:

- desktop reference size, such as `1440x1024`
- mobile reference size, such as `390x844`
- tablet reference size, if provided
- whether desktop or mobile is the primary source of truth
- expected max content width
- page side margins at each viewport
- whether sections should fill viewport height

Example:

```txt
Desktop reference: 1440x1024
Mobile reference: 390x844
Primary source of truth: desktop
Page margin: 16px desktop, 12px mobile
Hero: full viewport height minus page margins
```

### 4. Match Level

Choose one:

| Match Level | Meaning                                                                           |
| ----------- | --------------------------------------------------------------------------------- |
| Exact       | Treat measurements, spacing, colors, and typography as strict unless impossible   |
| Close       | Match the visual result closely while using existing system tokens and components |
| Directional | Preserve hierarchy, structure, and intent, but allow system-led interpretation    |

Also list:

- must-match elements
- flexible elements
- known wireframe artifacts to ignore

Example:

```txt
Match level: close
Must match: hero height, CTA placement, transparent eyebrow, logo strip spacing
Flexible: exact testimonial card copy length and image placeholders
Ignore: gray boxes are placeholders, not final image crops
```

### 5. Typography

Provide:

- font family
- fallback font, if important
- heading sizes
- body sizes
- weights
- line heights
- letter spacing
- text transform rules, such as uppercase eyebrow labels

If exact sizes are unknown, describe relative intent:

```txt
Font: Poppins
H1: very large, bold, tight line-height
Section headings: strong but clearly smaller than hero
Body: readable, medium contrast
Eyebrows: uppercase, medium weight
Letter spacing: normal
```

### 6. Color And Theme

Provide:

- background colors
- text colors
- accent colors
- button colors
- border colors
- inverse/dark section colors
- hover state expectations, if visible or known
- whether colors should map to existing starter tokens or define a client theme

Useful format:

```txt
Page background: #f8f7f4
Dark panels: #0b0a08
Primary text: #0b0a08
Muted text: #3f3b35
Primary CTA: white background, dark text
Accent: #214f6f
```

### 7. Spacing And Layout

Provide:

- page side margins
- section vertical padding
- grid columns
- grid gaps
- card padding
- content max widths
- whether content aligns to top, center, bottom, left, or right
- whether elements should overlap
- whether whitespace is intentional

Example:

```txt
Hero layout: two columns on desktop
Hero content: bottom aligned
Hero gap: large gap between title column and CTA column
Cards: 24px inner padding
Section gap: generous, editorial spacing
```

### 8. Sizing And Shape

Provide:

- hero min height
- image aspect ratios
- logo sizes
- icon sizes
- card widths/heights
- button height
- border radius
- shadow/elevation
- border widths

Example:

```txt
Hero panel radius: 32px
CTA height: about 48px
Social icons: 32px circle, 16px icon
Blog image placeholder: 4:3 ratio
```

### 9. Assets

Provide:

- real assets
- placeholder assets
- logo files
- social icons
- image crop expectations
- alt text requirements
- whether assets are starter-safe or client-private
- where assets are stored

Asset classification:

| Asset Type          | Store In                                                              | Notes                                   |
| ------------------- | --------------------------------------------------------------------- | --------------------------------------- |
| Starter placeholder | `paw-starter-kit/public/`                                             | Must be brand-neutral                   |
| Client approved     | client repo                                                           | Client-safe only                        |
| Internal reference  | `paw-mission-control/docs/wireframes/.../assets/references/`          | Do not copy to client repos             |
| Crops/exports       | `paw-mission-control/docs/wireframes/.../assets/crops/` or `exports/` | Planning/reference only unless approved |

### 10. Copy And Content

Provide:

- final copy or placeholder copy
- character length constraints
- required line breaks
- CTA labels and destinations
- nav labels
- testimonial names and roles, if approved
- whether copy can be rewritten to fit layout

Example:

```txt
Copy status: placeholder
CTA labels must match the wireframe
Agent may shorten body copy to preserve layout
Do not rewrite headline without approval
```

### 11. Component And Section Expectations

Provide:

- sections visible in order
- whether each section should reuse an existing starter section
- whether a new section is expected
- known component variants to use
- sections that should become reusable starter patterns
- sections that are client-only

Example:

```txt
Sections:
1. SiteHeader: existing
2. HeroSection: existing panel variant, needs full viewport polish
3. ServicesSection: existing programCards variant
4. AuthorityBioSection: existing
5. LeadMagnetSection: existing
```

### 12. Responsive Behavior

Provide:

- mobile stacking order
- mobile spacing changes
- hidden/shown elements
- whether full-height sections remain full-height on mobile
- menu behavior
- image crop changes
- text wrapping requirements

Example:

```txt
Mobile:
Hero stacks title above description and CTAs
Keep small page margin
Do not allow horizontal scroll
Logo strip can wrap
Nav can collapse to existing starter mobile behavior
```

### 13. Interaction States

Provide:

- hover behavior
- focus state expectations
- active/current nav state
- form states
- animation or transition expectations
- what should remain static

If unknown, say:

```txt
Use existing starter interaction states.
No new animation required.
```

### 14. Accessibility Requirements

Provide:

- heading order expectations
- image alt text
- color contrast requirements
- keyboard navigation requirements
- form labels and error text
- reduced motion expectations

Default expectation:

```txt
Use semantic HTML, preserve heading order, keep CTA text readable, and avoid color-only meaning.
```

### 15. Implementation Constraints

Provide:

- allowed write scope
- files or folders that should not change
- whether docs/inventories should be updated
- whether new primitives are allowed
- whether new dependencies are allowed
- validation command
- commit/push expectation

Example:

```txt
Allowed write scope: app/, components/, data/, public/, styles/, docs/
Do not add dependencies.
Run pnpm check.
Commit and push when complete.
```

### 16. QA Acceptance Criteria

Provide:

- exact URLs to check
- required viewport checks
- visual match priorities
- known acceptable differences
- post-build commands
- whether to run `*qa-visual` and `*qa-design`

Example:

```txt
Check:
- desktop 1440x1024
- mobile 390x844
- no horizontal overflow
- no runtime errors
- hero, logo strip, CTA, and footer must visually match the wireframe closely
Run pnpm check.
Run *qa-visual and *qa-design after implementation.
```

## Copy/Paste Handoff Template

Use this template when starting a wireframe conversion request.

```md
# Wireframe Conversion Handoff

Target repo:
Operating mode:
Target route/page:
Allowed write scope:
Validation:
Promotion impact:

## Reference

Wireframe file or URL:
Version:
Reference status: approved / exploratory
Reference viewport:
Mobile reference viewport:
Primary source of truth: desktop / mobile / both

## Match Target

Match level: exact / close / directional
Must-match items:
Flexible items:
Wireframe artifacts to ignore:

## Visual System

Font family:
Heading sizes/weights:
Body sizes/weights:
Line-height:
Letter spacing:
Colors:
Page background:
Dark/inverse surfaces:
CTA colors:
Border/radius/shadow:

## Layout

Page margins:
Section spacing:
Content max width:
Grid/columns:
Element alignment:
Hero height:
Card/image sizes:
Logo/icon sizes:

## Assets

Real assets:
Placeholder assets:
Asset storage path:
Image crop/aspect rules:
Alt text notes:
Private/client asset restrictions:

## Content

Copy status: final / placeholder
CTA labels and links:
Nav labels:
Required line breaks:
Copy that must not change:
Copy that may be adjusted:

## Sections

Ordered section list:
Existing starter sections to reuse:
New sections/components expected:
Client-only sections:
Reusable starter candidates:

## Responsive

Mobile layout:
Tablet layout:
Hidden/shown elements:
Stacking order:
Mobile spacing:

## Interactions

Hover states:
Focus states:
Forms:
Animation/motion:

## Accessibility

Heading order:
Alt text:
Contrast:
Keyboard/focus requirements:
Reduced motion:

## QA

URLs to check:
Desktop viewport:
Mobile viewport:
Known acceptable differences:
Required validation:
Post-implementation hooks:
```

## Good Example

```md
# Wireframe Conversion Handoff

Target repo: paw-starter-kit
Operating mode: Starter Governance Mode
Target route/page: /
Allowed write scope: app/, components/, data/, public/, styles/, docs/
Validation: pnpm check; browser check desktop and mobile
Promotion impact: none yet

## Reference

Wireframe file or URL: docs/wireframes/starter/homepage-v1/home-wireframe-v1.png
Version: homepage-v1
Reference status: approved for starter direction
Reference viewport: 1440x1024
Mobile reference viewport: not provided
Primary source of truth: desktop

## Match Target

Match level: close
Must-match items: full-height hero, small page margins, transparent eyebrow, white CTA with dark text, section order
Flexible items: exact placeholder image crop, final testimonial copy length
Wireframe artifacts to ignore: gray media blocks are placeholders

## Visual System

Font family: Poppins
Heading sizes/weights: large bold hero, smaller bold section headings
Body sizes/weights: readable body copy, normal letter spacing
Line-height: tight headings, relaxed body
Colors: neutral warm page, dark inverse panels, white CTAs
Page background: #f8f7f4
Dark/inverse surfaces: #0b0a08
CTA colors: white background, #0b0a08 text
Border/radius/shadow: rounded panels around 32px, subtle shadows only

## Layout

Page margins: 16px desktop, 12px mobile
Section spacing: generous editorial spacing
Content max width: use starter wide container unless hero specifies full width
Grid/columns: hero two columns on desktop
Element alignment: hero content bottom aligned
Hero height: full viewport minus page margins
Card/image sizes: keep cards stable and avoid layout shift
Logo/icon sizes: social icons 32px circle, 16px glyph

## Assets

Real assets: none
Placeholder assets: social SVGs and logo strip placeholders
Asset storage path: paw-starter-kit/public/
Image crop/aspect rules: preserve visible ratios from wireframe when possible
Alt text notes: neutral example alt text
Private/client asset restrictions: no client assets in starter

## Content

Copy status: placeholder
CTA labels and links: match wireframe labels
Nav labels: use starter nav unless wireframe differs
Required line breaks: hero title may wrap naturally
Copy that must not change: CTA labels
Copy that may be adjusted: body copy length

## Sections

Ordered section list: header, hero, services, proof quote, authority bio, logos, testimonials, lead magnet, blog, final CTA, footer
Existing starter sections to reuse: all listed sections where possible
New sections/components expected: none unless required by QA
Client-only sections: none
Reusable starter candidates: any repeated media placeholder pattern

## Responsive

Mobile layout: stack hero content and CTAs
Tablet layout: allow section grids to collapse naturally
Hidden/shown elements: use existing starter nav behavior
Stacking order: content before media where unclear
Mobile spacing: keep small page margin and avoid horizontal scroll

## Interactions

Hover states: use existing starter states
Focus states: use existing starter focus ring
Forms: no real submission required
Animation/motion: none

## Accessibility

Heading order: one H1, section H2s
Alt text: neutral descriptive alt text
Contrast: CTA and inverse section text must be readable
Keyboard/focus requirements: preserve focus-visible behavior
Reduced motion: no required motion

## QA

URLs to check: http://localhost:3000/
Desktop viewport: 1440x1024
Mobile viewport: 390x844
Known acceptable differences: placeholder copy and media may differ
Required validation: pnpm check
Post-implementation hooks: *qa-visual, then *qa-design
```

## Agent Handling Rules

When using this handoff:

- Treat `must-match` items as acceptance criteria.
- Ask before changing anything marked final or must-not-change.
- If a value is unknown, use starter tokens and existing primitives first.
- If a wireframe conflicts with accessibility, keep accessibility and report the difference.
- If the handoff is incomplete, list assumptions before implementation.
- After implementation, run `*qa-visual` and `*qa-design` unless the user explicitly scopes them out.
