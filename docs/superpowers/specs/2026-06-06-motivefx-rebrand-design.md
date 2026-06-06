# motivefx.com Rebrand — Design Spec

**Date:** 2026-06-06
**Goal:** Rebrand motivefx.com from a web-design/dev *services agency* site into a **product studio** homepage that leads with **ScreenSet** (the flagship Mac app) and frames MotiveFX as the maker behind it.

---

## Positioning

MotiveFX is a **product studio** — it makes its own software (ScreenSet first), and takes on selective client work that fits its philosophy. The old agency framing (services menu, client-site portfolio) is retired.

- **Message register:** impact, not craft-philosophy. MotiveFX builds tools that make work **more efficient and less painful**.
- **Honesty:** ScreenSet is free; **Auto-Switch** is the one paid feature ($5.99 one-time). The site never hides this.

## Architecture (this spec covers item 1 only)

1. **`motivefx.com` homepage** — product-led, ScreenSet-forward, studio as a band near the bottom. ← **THIS BUILD**
2. `motivefx.com/screenset` — deeper ScreenSet product page. **Future / out of scope now.**
3. `screenset.app` → redirect to `/screenset`. **Future** (waits on #2).
4. **vibefly** — deliberately **not** featured yet (business model unsettled). No products section.

## Visual identity

Adopt the **vibefly.ai aesthetic** (the look the owner loves), unifying the brand around the shared yellow DNA:

- Background `#000`; text `#fff`, secondary `#9aa0aa`
- **Accent (primary):** neon-yellow `#f5ff1a` — CTAs, highlights, the payoff half of headlines
- **Accent (secondary):** electric-blue `#3c78ff` — ambient radial glows, card-border hovers
- Glowing translucent card borders (`rgba(100,180,255,.28)`), generous negative space, restraint
- Type: system / SF Pro Display stack, tight letter-spacing, big confident headlines
- Tone: **sparse**. Few words. A calm studio reads calm.

## Page structure & final copy

**Nav:** `motiveFx` wordmark · links: ScreenSet · Work · `Download` pill

**1. Hero (ScreenSet)**
- Eyebrow: `ScreenSet · for macOS`
- H1: **Dock. Undock.** / *Your windows just come back.* (second line in yellow)
- Sub: "Every time your monitors change — **dock, undock, or switch setups** — ScreenSet restores your exact window arrangement automatically. Or recall any saved layout with a hotkey."
- CTAs: **Download for Mac** (yellow) · *See how it works* (ghost → scrolls to features)
- Note: `Free to use · Auto-Switch is $5.99 one-time · macOS 13+`
- Visual: product screenshot (see Screenshots below)

**2. "Set it once. Then forget it." — three cards**
- *Save your layouts* — "Arrange your windows the way you like, name the setup, and save it. Coding, Writing, Design — whatever you run, ScreenSet keeps it."
- *Auto-Switch* `$5.99` badge — "Dock, undock, or swap monitors and your exact arrangement returns on its own — no clicks, no rearranging."
- *Hotkey recall* — "Snap to any saved layout with ⌃⌥⌘ + a number. Save the current one with ⌃⌥⌘S."

**3. Studio band**
- Label: `The studio`
- Statement: **From MotiveFX — a studio for software that makes work more *efficient*, and a lot less *painful*.** (the two adjectives in yellow)

**4. Work with us**
- Label `Work with us` · "Have something worth building?" · "We take on a handful of client projects — the ones that fit how we build. If that sounds like yours, let's talk." · **Get in touch**

**5. Footer**
- `motiveFx` · ScreenSet · Work · Privacy · Terms · © 2026 MotiveFX LLC

## Download flow

- **Download for Mac** → the notarized `ScreenSet.dmg` (from `screenset/dist/ScreenSet.dmg`), hosted as a static asset in this repo (e.g. `htdocs/downloads/ScreenSet.dmg`) or a release URL. The DMG is self-contained (stapled), works regardless of LS test/live mode.

## Contact

- **Get in touch** reuses the existing contact mechanism (Formspree / `/api/submit`) — repurposed for "work with us" inquiries. Keep spam protection (Turnstile).

## Screenshots (the main asset gap)

The CSS "device mock" in the brainstorm mockups is a **placeholder**. Replace with real, polished ScreenSet captures (the actual menu + windows snapping into place) before launch — the single biggest visual upgrade remaining.

## Preserve / don't break

- `privacy-policy.html`, `terms-of-service.html` (footer links)
- Cloudflare Workers hosting; **dev branch → test → main** deploy flow
- Existing protected assets (favicon, etc.)

## Out of scope (later)

- `/screenset` deep product page + `screenset.app` redirect
- vibefly / "other products" section
- Real screenshot production (tracked as the asset gap above)

## Build approach

Static HTML/CSS matching the existing stack. Single `index.html` + styles. Replace the agency homepage; keep legal pages. Build on a branch off `main`, preview on the dev deploy, merge when approved. (One static page — direct build, no separate multi-task plan needed.)
