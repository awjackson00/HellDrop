# Web Design & Engineering Playbook
**Version:** 1.0 | **Researched:** November 24, 2026 | **Scope:** HELLDROP and reusable guidance for future websites

This is a working standard for building distinctive, fast, accessible sites. It draws on Emil Kowalski's design-engineering skills, Paul Bakaus's Impeccable, Taste Skill, Linear's design refresh, Vercel's Geist design system, NN/g usability research, W3C WCAG 2.2, Chrome Web Vitals, and Playwright.

**Core rule: Make each project look like itself. Do not apply a universal "AI website" template.**

## 1. Start with an art direction, not components

Before writing CSS:
- Identify users, core jobs, content hierarchy, emotional tone, and context of use.
- Inspect at least 3 relevant reference products. Record **why** each works, not merely what it looks like.
- Define one visual thesis in 2 sentences. Example for HELLDROP: "An efficient deployment desk for a squad member who already knows the game. Actual gear artwork is the star; interface decoration recedes."
- Draft user journeys and four states: first visit, returning user, insufficient data, failed data source.
- Draw responsive compositions before designing buttons.
- Reject generic centered hero + 3 card grid + gradient + oversized badge recipes unless content genuinely warrants them.

Distinguish **marketing**, **productivity tool**, **commerce**, **editorial**, and **game companion** needs. A visually elaborate landing page is not a good default for a high-frequency utility.

## 2. Typography is a system

Choose type for the specific brand and job, not because it is fashionable.
- Usually one expressive display family plus one comfortable text family is enough. Use a third mono family only where technical metadata needs it.
- Define reusable roles: display, H1, H2, H3, body, controls, label, caption, numerical data.
- Set font size, weight, line-height, tracking, width, and contrast together. Font-family alone does not create hierarchy.
- Prefer readable body copy around 15–18 CSS px, line-height around 1.4–1.65, and restrained text widths; treat these as starting points, not universal requirements.
- Avoid body copy at 9–11 px, arbitrary ALL CAPS, exaggerated tracking, excessive font weights, and condensed type for long passages.
- Check long names, localization, text zoom to 200%, and font-fallback metrics. No layout should depend on a font loading successfully.
- Keep the font set small. Prefer WOFF2 and intentional font loading; avoid duplicate Google Fonts imports. Use appropriate font-display behavior and verify layout shifts.

**HELLDROP example:** Reserve display typography for "Mission loadout" and major labels. Keep item names legible at a glance; isolate tiny mono labels to optional metadata, not primary decisions. Authentic game artwork should be more noticeable than the font.

## 3. Information hierarchy and composition

- Put the primary task first, with one clear dominant action.
- Use spacing, alignment, rhythm and type before borders or cards. A relationship between elements does not always need a box.
- Base a coherent spacing scale on steps such as 4/8/12/16/24/32/48 px, with intentional exceptions. Avoid the same gap everywhere.
- Limit surface colors and shadows; establish levels for background, content, elevated dialogs and selected controls.
- Use asymmetry only when it improves emphasis and scanability.
- Avoid repeating identical feature-card patterns for unrelated content.
- Design responsive layouts explicitly rather than only shrinking desktop CSS. Check 320, 390, 768, 1024 and 1440 px; include landscape and zoom.
- Prefer genuine icons and legally usable artwork. Do not invent a branded image when an accurate source asset exists.
- Make error, empty, loading, locked, disabled, selected, keyboard-focus and offline states part of the visual design.

**Evidence:** Linear's 2026 refresh deliberately reduced sidebar prominence, icon use and excessive borders so work content regained focus.

## 4. Motion: meaning before decoration

Motion must accomplish at least one of: feedback, orientation, state change, continuity, or explanation.
- High-frequency input, keyboard shortcuts and repeated utility actions: instant or nearly instant. Never force users to wait for decoration.
- Press/hover: usually 90–160 ms.
- Selection and small state changes: usually 130–220 ms.
- Dialogs, popovers, drawers: usually 180–260 ms.
- Rare onboarding or narrative hero: can be longer, e.g. 300–550 ms, if deliberately designed.
- These are **house starting budgets**, not standards. Test in the browser and adapt.
- Choose eased entrances, sensible transform-origin, and minimal travel; do not animate from scale(0).
- Prefer composited transform and opacity. Avoid animating top, left, width, height or large blurs in frequent interactions.
- Use purposeful spring motion only where its physics suit the control. Do not add bounce everywhere.
- Never animate an entire layout when only one small state changed.
- Respect prefers-reduced-motion; make meaningful state changes readable without animation.
- Test interrupted animations, repeated clicks, keyboard use, 60 Hz and low-performance devices.

**HELLDROP examples:** Category tab selection should feel immediate. Armor/booster toggles must not rerandomize the rest. Equipment rerolls should update only the requested slot. A modal may fade/shift slightly; randomization should not require a lengthy loading theater.

## 5. Real assets and honest content

- Prioritize actual product photography, user-supplied artwork, authentic game assets, or carefully designed original illustrations.
- Document rights, provenance and attribution. A third-party image being accessible by URL does not mean it is freely redistributable.
- Preserve true aspect ratios and focal points; define object-fit by category.
- Use responsive images where appropriate, lazy-load below-the-fold media, preload only genuine critical assets.
- Avoid generic stock, emoji icon patches, invented testimonials, placeholder logos, or misleading screenshots.
- Keep informative alt text where needed and mark purely decorative icons as decorative.
- Verify broken-image fallback behavior both in slow network conditions and when asset hosts are blocked.

## 6. Accessibility is part of craft

Target WCAG 2.2 AA where applicable.
- Normal text contrast at least 4.5:1; large text at least 3:1, subject to WCAG exceptions.
- Target sizes at least 24 x 24 CSS px under WCAG 2.2 AA (with specified exceptions), preferably 44 x 44 px for finger-heavy interfaces.
- Visible focus, sensible tab order, keyboard-equivalent actions, and reachable dialog controls.
- Test focus management when opening and closing overlays.
- Do not communicate state only through color. Ensure selected/unselected and locked/unlocked are verbalized.
- Respect reduced motion, text resizing, and accessible names.
- Automated axe scans are necessary but not sufficient. Include manual keyboard and screen-reader spot checks.

## 7. Performance goals

Measure field data when available, not only an empty local browser profile.
- LCP at the 75th percentile: <= 2.5 seconds.
- INP at the 75th percentile: <= 200 milliseconds.
- CLS at the 75th percentile: <= 0.1.
- Optimize long tasks, image loading, layout stability and font delivery.
- Avoid animation-driven layout work.
- Run Lighthouse / PageSpeed Insights for a laboratory baseline; do not treat one score as proof of real-user performance.
- Check cache cold/warm, throttled mobile, unavailable CDNs, and outdated stored preferences.

## 8. Build and test protocol

For each feature or redesign:
1. Audit existing behavior and make a "must not break" contract.
2. Build 2–3 directions when visual direction is unresolved; pick one.
3. Establish type, color, spacing, radius, icon, and motion tokens.
4. Implement real content and real states. Do not declare completion from a static mock.
5. Run functional tests for all user paths and edge cases.
6. Run browser screenshots at 320 / 390 / 768 / 1024 / 1440. Inspect every screenshot, not only generated dimensions.
7. Check horizontal overflow, clipping, readable type, icons, asset failure, font failure, and long copy.
8. Run keyboard, focus, reduced-motion, and accessible-contrast checks.
9. Compare before/after; reject regressions and template-looking additions.
10. Commit to GitHub; wait for successful deployment; only then say "published". Report any tests not run.

Useful tooling: Product Design for flow and prototype critique where connected; Figma for editable design systems and handoff; Playwright for interaction tests, device emulation and screenshot baselines; axe-core for automated accessibility; Lighthouse for performance and basic quality checks; CI to reject regressions.

## 9. Final shipping gate

A site is not ready simply because it renders.
- [ ] User's main goal is obvious in the first viewport
- [ ] Typography has a rationale and does not resemble a default template
- [ ] Content and imagery are accurate, sourced and legally appropriate
- [ ] Every control has hover, focus, active, disabled and error behavior where relevant
- [ ] Motion is purposeful, responsive and reduced-motion safe
- [ ] Desktop and phone screenshots look composed, not merely functional
- [ ] No unexpected rerolls, data loss, duplicated items, or broken ownership rules
- [ ] No clipping, overflowing text, broken icons, blank images or layout shifts
- [ ] Keyboard/contrast/target-size checks pass or exceptions are documented
- [ ] Performance meets targets or tradeoffs are documented
- [ ] All changes are committed; live deployment and URL verified
- [ ] Explicitly disclose any unavailable tests or network-dependent artwork

## 10. Tool roles and limitations

**Product Design (ChatGPT plugin):** The connected design partner for direction exploration, live-URL user-flow audits and interactive prototypes, when its actions are available in the conversation. It does not replace code review or browser QA.

**Figma integration:** Useful for editable layer design, design systems, components and design-to-code handoff if separately connected. A Figma connector is not the same thing as arbitrary Figma MCP desktop control.

**Emil Kowalski skills:** Source philosophy for deliberate interactions, motion review and craft. Agent skills, not automatic capabilities of this ChatGPT session.

**Impeccable (Paul Bakaus):** Source framework for design vocabulary, critique, accessibility and anti-pattern detection. Its CLI/skills require separate setup in a compatible coding environment.

**Taste Skill:** Art direction, authentic imagery, references and repeatable browser visual checks. Its CLI/skills likewise require separate setup. Apply its ideas selectively, not its marketing-page layouts to every product.

**Playwright:** A real browser testing library. Screenshot comparisons help catch changes, but are not a substitute for visual judgment. Screenshot baselines should be pinned to a consistent browser environment.

## 11. What to avoid

- Treating "AI look" as a single font problem.
- Using dramatic animation to compensate for weak content or confusing hierarchy.
- Rerandomizing state when the user toggles an unrelated option.
- A website "redesign" that changes underlying functionality without tests.
- Claiming official game imagery is license-free.
- Shipping only a screenshot or AI image when the requested deliverable is a functioning website.
- Claiming live performance, real-user test results, or a successful deployment without measuring/verifying them.

## Sources and primary references

- Emil Kowalski: https://github.com/emilkowalski/skills
- Impeccable: https://github.com/pbakaus/impeccable
- Taste Skill: https://github.com/Leonxlnx/taste-skill
- Linear 2026 design refresh: https://linear.app/now/behind-the-latest-design-refresh
- Vercel Geist typography: https://vercel.com/geist/typography
- Nielsen Norman Group visual hierarchy: https://www.nngroup.com/articles/principles-visual-design/
- Nielsen Norman Group scanning: https://www.nngroup.com/articles/text-scanning-patterns-eyetracking/
- Apple Human Interface Guidelines, motion: https://developer.apple.com/design/human-interface-guidelines/motion
- Web.dev font practices: https://web.dev/articles/font-best-practices
- Web.dev animation performance: https://web.dev/articles/animations-guide
- Web.dev Web Vitals: https://web.dev/articles/vitals
- WCAG 2.2: https://www.w3.org/TR/WCAG22/
- Playwright visual regression testing: https://playwright.dev/docs/test-snapshots
- Playwright accessibility testing: https://playwright.dev/docs/accessibility-testing
- Lighthouse: https://developer.chrome.com/docs/lighthouse/overview

**Interpretation rule:** Guidelines and motion durations above are defaults to challenge and refine, not fixed universal requirements. Always adapt to actual users and the specific product.
