# HELLDROP design principles

This is the standard for future design work on HELLDROP. It translates the design-engineering, Impeccable and Taste ideas into decisions specific to this product, rather than copying any template.

## Product and audience

HELLDROP is a quick utility for Helldivers 2 players. The goal is to choose one piece of equipment and generate a compatible randomized deployment. It should feel like a polished fan-made field tool, not a marketing landing page, admin dashboard or sci-fi movie prop.

## Visual direction

**Deployment Desk.** Dense where useful, spacious where it improves hierarchy. Industrial, functional, editorial, unmistakably inspired by Helldivers without impersonating an official game product.

- **Typography:** Barlow Condensed for purposeful, compact headings; IBM Plex Sans for controls and body text; IBM Plex Mono only for tiny technical metadata and status. Limit unnecessary all-caps and tiny type.
- **Color:** Dark near-neutral olive-charcoal surfaces with off-white text. Yellow is an action/selection color, not generic decoration. Use natural green-gray borders.
- **Composition:** One clear primary action. Keep selection controls on the left and the generated loadout dominant on the right on desktop. Stack them in the same order on mobile.
- **Containment:** Prefer spacing and thin dividers over boxes around boxes. Item thumbnails sit in unobtrusive frames. Stratagem tiles may use a single bounding surface to separate interactive slots.
- **Image handling:** Actual licensed/attributed game-derived artwork where available, with object-fit containment and clear category fallbacks if images fail. Never stretch art.
- **Branding:** Original, clean hellpod and question-mark vector. No third-party watermarks, AI signature marks, or pretended official affiliation.

## Motion and interactions

- Motion must communicate a state change, hover, reveal or selection. Do not animate the page simply to look impressive.
- Default transitions 120–180 ms, restrained easing. Prefer opacity/color/transform; avoid layout-jank transitions.
- Respect `prefers-reduced-motion`.
- Maintain visible focus states, keyboard control and proper minimum touch targets.
- Warbond, Superstore, and individual gear settings must save locally.
- Checkbox changes must not reroll unrelated items. Locked gear remains locked. Keep the generator rules intact.

## Anti-patterns

Avoid glassmorphism, ornamental gradients, overuse of shadows, glowing neon borders, bloated cards, meaningless stock photos, giant empty hero sections, identical repeated tiles, excessive uppercase labels, ornamental badges and complicated animations.

Do not use decorative illustrations in place of actual game art unless the source is unavailable.

## Review checklist for each change

1. Write down the user's actual task and the most important on-screen action.
2. Audit hierarchy, readability, unnecessary containment and dead space.
3. Check the experience at **1440px desktop, ~820px tablet and 390px mobile**.
4. Inspect generated results, item picker, owned Warbonds, Superstore and mobile dialogs.
5. Test generation, locked-item selection, rerolls, armor/booster toggles and saved ownership behavior.
6. Verify there is no horizontal overflow, uncaught browser error or inaccessible control.
7. Keep the pages fast: static HTML/CSS/JS, no unnecessary dependencies, avoid layout shift.

## Inspiration and sources

- Emil Kowalski design-engineering skills: purposeful interactions and motion review.
- Paul Bakaus's Impeccable: craft, visual hierarchy, typography, layout critique and anti-slop audit.
- Taste-style design methods: a distinctive product-specific direction, deliberate trade-offs, and browser validation.

These are principles, not dependencies. We do not claim the named tools are installed or executed unless they actually are.
