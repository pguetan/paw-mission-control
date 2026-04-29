# Section Map V1

Wireframe: `home-wireframe-v1.png`
Target system: `paw-starter-kit`

## Section Inventory

| Order | Wireframe Block | Starter Section Candidate | Reusable? | Notes |
| --- | --- | --- | --- | --- |
| 1 | Floating rounded header | `SiteHeader` or `HeaderSection` | Yes | New navigation component needed; should use `data/navigation.ts` and social links from site data. |
| 2 | Dark split hero panel | `HeroSection` | Yes | Existing hero can be extended with a dark contained-panel preset if current variants cannot match. |
| 3 | "Start your journey here" offer cards | `ServicesSection` or `OffersSection` | Yes | Existing services model is close; needs dark cards, pill labels, arrow actions, and 3-card layout. |
| 4 | Centered quote proof | `QuoteProofSection` or testimonial variant | Yes | Could be a lightweight testimonial variant for single quote plus author avatar. |
| 5 | Media, metrics, and bio card | `AuthorityBioSection` | Yes | New section family; combines media placeholder, social links, stat grid, bio text, and CTA. |
| 6 | "Worked with" logo strip | `LogoStripSection` | Yes | New section family; should support text logos and future image logos. |
| 7 | Client testimonial rail | `TestimonialsSection` | Yes | Existing testimonials section needs a rail/video-card variant and carousel controls/dots. |
| 8 | Free download opt-in | `LeadMagnetSection` | Yes | New section family; includes dark panel, copy, form fields, button, and privacy text. |
| 9 | Blog preview grid/list | `BlogPreviewSection` | Yes | New section family; featured post plus stacked secondary posts and view-more link. |
| 10 | Final CTA band | `CtaSection` | Yes | New reusable CTA section; centered copy and primary action on dark surface. |
| 11 | Oversized footer | `SiteFooter` or `FooterSection` | Yes | New footer component; includes social icons, oversized wordmark, nav, copyright, and legal links. |

## Component Needs

| Component | Existing Starter Component? | Action |
| --- | --- | --- |
| `Button` | Yes | Reuse for CTAs; may need icon/arrow support if not already available. |
| `Container` | Yes | Reuse for section width and gutters. |
| `Section` | Yes | Reuse for vertical rhythm and tones. |
| `Card` | Yes | Reuse or extend for dark offer/testimonial cards. |
| `Badge` | Yes | Reuse for offer labels and section eyebrows. |
| `SectionHeader` | Yes | Reuse for intro blocks. |
| Social icon links | No | Add shared component or data-driven pattern. |
| Arrow icon button | No | Add small reusable icon-button pattern or section-local control. |
| Media placeholder panel | No | Add reusable placeholder/media frame pattern if repeated. |
| Metric/stat item | No | Add shared component if used in multiple sections. |
| Form field/input | No | Add primitives before `LeadMagnetSection`. |
| Carousel controls/dots | No | Add only if implementing interactive carousel behavior now; static rail can defer. |

## Data Needs

| Data Source | Purpose | Notes |
| --- | --- | --- |
| `data/site.ts` | Logo, brand/name, social links, footer metadata | Replace wireframe-specific "Robert Jenkins" with neutral starter example data. |
| `data/navigation.ts` | Header and footer nav | Existing source likely reusable. |
| `data/home.ts` | Homepage composition and section content | Expand or split into example data as homepage grows. |
| `data/services.ts` | Offer/program cards | Existing source likely reusable with added labels. |
| `data/testimonials.ts` | Quote proof and testimonial rail | May need video/featured fields. |
| `data/logos.ts` | Worked-with proof strip | New data source if logo strip is built. |
| `data/blog.ts` or `content/blog/` | Blog preview cards | Use current content approach if available; otherwise starter-safe example data. |
| `data/lead-magnet.ts` | Free download content and form copy | New data source if lead magnet is built. |

## Build Decisions

- Build this as a reusable starter homepage, not as a client-specific page.
- Keep monochrome styling as a preset/art direction, not as hardcoded brand identity.
- Preserve large dark rounded panels and bold typography, but express spacing/radius/color through tokens.
- Start with static, responsive sections before adding carousel interactivity.
- Implement missing primitives before section-specific one-offs when the pattern repeats.
- Update starter inventories when new sections/components are added.
- Run `pnpm check` before any starter implementation is marked complete.
