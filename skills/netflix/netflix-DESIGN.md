---
version: alpha
name: Netflix
description: "A cinematic dark canvas (#141414) where content artwork is the visual surface and Netflix Red (#E50914) is used with surgical restraint — only on the logo, play buttons, and progress bars. The UI recedes completely so poster art fills every pixel of attention. Content is king."

colors:
  primary: "#E50914"
  on-primary: "#FFFFFF"
  primary-hover: "#F40612"
  ink: "#FFFFFF"
  ink-muted: "#A3A3A3"
  canvas: "#141414"
  surface-1: "#1F1F1F"
  surface-2: "#2D2D2D"
  border: "#333333"
  overlay-gradient: "linear-gradient(to top, rgba(20,20,20,0.95) 0%, rgba(20,20,20,0.4) 60%, transparent 100%)"
  progress-fill: "#E50914"
  success: "#46D369"
  warning: "#F5C518"

typography:
  display:
    fontFamily: "Netflix Sans, Helvetica Neue, Arial, sans-serif"
    fontSize: 56px
    fontWeight: 700
    lineHeight: 1.05
    letterSpacing: -0.02em
  body:
    fontFamily: "Netflix Sans, Helvetica Neue, Arial, sans-serif"
    fontSize: 15px
    fontWeight: 400
    lineHeight: 1.6
    letterSpacing: -0.01em

spacing:
  base: 8px
  scale: [4, 8, 12, 16, 24, 32, 48, 64, 96, 128]

radius:
  sm: 4px
  md: 6px
  lg: 8px
  pill: 9999px

shadows:
  card: "0 2px 8px rgba(0,0,0,0.4)"
  elevated: "0 8px 32px rgba(0,0,0,0.6)"

motion:
  duration-fast: 100ms
  duration-base: 200ms
  easing: cubic-bezier(0.4, 0, 0.2, 1)
---

## Rationale

**Content as surface, UI as vapor** — Netflix's most deliberate design decision is making the chrome invisible. The navigation bar fades to transparent over hero artwork; the only structural color you notice is the red logo. Every pixel that isn't poster art or metadata competes with the content — so Netflix stripped the interface down to what can't be removed. This is a philosophy, not just a color choice: the product's job is to get out of the way.

**Red with surgical restraint** — Netflix Red (#E50914) appears in exactly three contexts: the wordmark, the play button, and the progress bar scrubber. Using the brand accent this sparingly makes each instance land harder. The play button in red says "this is the moment — start watching." A red progress bar tick says "you're here." Diluting that red into backgrounds, hover states, or decorative elements would destroy its signal value.

**Artwork as information architecture** — Because the canvas is #141414 and the UI chrome is minimal, the grid of content cards becomes the actual visual design. Netflix's designers spend enormous effort on artwork sizing, cropping ratios (2:3 portrait for mobile, 16:9 landscape for TV/desktop), and hover state transitions. The thumbnail is the UI atom. Choosing what artwork to show, and at what size, is the primary layout decision.

**Gradient overlays as text legibility infrastructure** — Placing white metadata text directly over photographic poster art would fail accessibility and readability. The signature dark-to-transparent gradient overlay at the bottom of every hero image and content card is a structural pattern, not a decorative flourish. It creates a reliable dark zone where white type can achieve 4.5:1 contrast regardless of the underlying image color.

## 1. Visual Theme & Atmosphere
Netflix lives in perpetual darkness. The #141414 background (not pure black — pure black looks harsh on OLED, slightly lifted dark charcoal reads as "cinematic") creates a theater-like environment that makes every frame of artwork glow. The experience is intentionally immersive: the platform disappears and the content world takes over. When you browse, you're not using an app — you're standing in a video store where every shelf is perfectly lit and the walls are made of movies.

The homepage hero section is a full-viewport still frame or autoplay muted clip from a featured title — the interface starts with content, not navigation. All scrolling is horizontal carousels organized by editorial curation: "Continue Watching," "Top 10 in Your Country," "Because You Watched X." Vertical scroll is progression through categories; horizontal scroll is discovery within one.

## 2. Color System
**Dark canvas**:
- Background: #141414 — warm near-black, avoids harsh pure-black
- Surface 1: #1F1F1F — cards, modals, slightly elevated surfaces
- Surface 2: #2D2D2D — hover state backgrounds, input fields
- Border: #333333 — dividers and structural edges

**The only accent**:
- Netflix Red: #E50914 — logo, play button fill, progress bar fill
- On hover: #F40612 — marginally brighter, confirms active state

**Text**:
- Primary: #FFFFFF — all content metadata and UI labels
- Muted: #A3A3A3 — secondary metadata (year, rating, duration), inactive nav items

**Semantic**:
- Success/Match: #46D369 — the "New" badge, availability indicators
- Rating/Info: #F5C518 — IMDb-style star ratings where shown

Netflix Red is intentionally never used as a background fill for text blocks, as a category header color, or on hover states for cards. Its scarcity is its value.

## 3. Typography
Netflix commissioned Netflix Sans from Dalton Maag in 2018, replacing Gotham and saving millions annually in typeface licensing fees across global advertising. The typeface is a geometric grotesque — clean, legible at small sizes on TV screens, and designed to work equally well across the Latin, Arabic, Hebrew, Thai, Japanese, and Korean scripts that Netflix needs globally.

At display scale (hero titles, featured content names): 56–72px, weight 700, tight −0.02em tracking. Titles need to be bold enough to read on translucent overlays over complex artwork backgrounds.

At UI scale (navigation, metadata): 13–15px, weight 400–500. Run at 400 for secondary info (year, rating, runtime), 500 for active navigation labels. The system never uses weights below 400 in the product UI — thin type disappears on dark backgrounds.

The maturity rating badge ("TV-MA", "PG-13") uses a distinctive monospace-style bounded box — a separate visual token that signals regulatory metadata, not editorial content.

## 4. Components & Patterns
**Content card (the atom)**:
- 16:9 landscape thumbnail (TV/web) or 2:3 portrait thumbnail (mobile)
- On hover: card scales to ~105%, gradient overlay fades in over the bottom third, title + metadata + playback controls appear
- Hover card can expand to a larger preview panel showing trailer autoplay, match percentage, and genre tags
- The scale-on-hover animation is Netflix's signature microinteraction — it signals that content is alive and interactive

**Carousel row**:
- Horizontal scrollable list of cards within a category
- Row title left-aligned in 18px bold white
- "Explore All" link appears on row hover
- Partial card at right edge signals scrollability (affordance without a visible scrollbar)

**Hero billboard**:
- Full-viewport or wide-format featured title
- Autoplay muted video clip loops behind metadata
- Title logo art (the show's custom logotype, not a text heading) bottom-left
- Two CTAs: red "Play" button + white "More Info" button (ghost/outline)

**Progress indicator**:
- Thin red bar at bottom of "Continue Watching" cards — position encoded as percentage
- Scrubber control on the video player uses same red
- Time remaining text appears in muted gray

**Navigation bar**:
- Fixed top, fades from fully transparent over hero to solid #141414 on scroll
- Logo left, nav links center (Home, TV Shows, Movies, New & Popular, My List)
- Right: search, notifications, profile avatar
- Mobile: collapses to hamburger; primary navigation moves to bottom tab bar (Home, Search, Coming Soon, Downloads, More)

**Rating badge**:
- White bordered box with maturity rating text — regulatory signal
- Appears consistently on all content cards and detail pages

## 5. Spacing & Layout
Netflix uses a 4px base grid. Content carousels use 4px gap between cards at mobile, 8px at tablet, and scale to approximately 0.5% of viewport width on large displays to maintain optical spacing as the viewport grows.

Row padding: 4% of viewport width on both sides — this creates breathing room on large TVs while keeping content close to the edge on phone screens. This percentage-based gutter is a key technical pattern for a product that runs on 4-inch phones and 85-inch 4K televisions simultaneously.

The standard grid for the browse page uses approximately 6 cards per row on desktop (16:9 format), 4–5 on tablet, 2–3 on mobile. Card height adapts to maintain aspect ratios — the grid is responsive to viewport, not a fixed column system.

Detail modal overlay: max-width 850px, centered, with a darkened scrim over the browse grid behind it.

## 6. Motion & Interaction
**Card hover scale**: 200ms duration, `cubic-bezier(0.4, 0, 0.2, 1)` — the card expands slightly and surrounding cards push away. The delay before hover animation triggers is ~300ms — prevents accidental triggers while scrolling past.

**Hero video autoplay**: fade in from poster image at 500ms after page load, muted, with captions available. User-initiated sound is a click interaction, not automatic.

**Carousel scroll**: momentum-based horizontal scroll on touch, arrow button navigation on pointer devices. Arrow buttons appear only on hover of the carousel row.

**Intro logo animation**: Netflix's "Ta-dum" sound + red logo animation on app launch — the red N expands from a thin slice to full width in approximately 1 second. This is the brand's most iconic motion moment.

**Loading skeleton**: dark gray (#2D2D2D) placeholder cards fill the grid before content loads — same dimensions as real cards, no spinning indicators. Avoids layout shift.

## Accessibility

### Contrast Ratios
- **White text on #141414 canvas**: 16.1:1 — passes AAA
- **#A3A3A3 muted text on #141414**: 4.9:1 — passes AA, fails AAA
- **#E50914 red on #141414**: 3.2:1 — fails AA for text (Netflix Red is never used as a text color on dark background; it's used as a fill/icon)
- **White text on gradient overlay** (minimum dark zone #141414): 16.1:1 — passes AAA
- **#46D369 green on #141414**: 5.8:1 — passes AA

### Minimum Requirements
- **Touch target**: 44×44px minimum — critical for TV remote navigation (focus targets are even larger on the 10-foot UI)
- **Focus indicator**: white 2px outline, 2px offset — high visibility on dark background
- **Keyboard navigation**: full arrow-key navigation of the carousel grid for TV platform compatibility

### Motion
- Respects `prefers-reduced-motion`: yes — card hover scale, hero autoplay, and intro animation should all be suppressed
- The card hover expand animation is a fundamental part of the Netflix UX; under reduced motion, reveal controls and metadata without scaling

### Notes
- Netflix Red (#E50914) must never be used as a text color on dark backgrounds — 3.2:1 fails AA for text; use only as fill/background with white (#FFFFFF) overlay text
- Autoplay video in the hero and card hover previews must respect `prefers-reduced-motion` and default to static poster image
- The gradient overlay technique for ensuring text legibility over artwork is the correct approach — test every new artwork crop to confirm the gradient dark zone provides ≥4.5:1 for white text
- TV platform (10-foot UI) requires minimum 24px font sizes and oversized focus rings — the web design system should be considered a subset of a larger multi-platform system
