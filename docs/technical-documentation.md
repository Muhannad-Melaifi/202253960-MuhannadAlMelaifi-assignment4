# Technical Documentation — Assignment 4

## Overview

This is the final portfolio assignment, building on Assignments 1–3. Assignment 4 brings the site to a production-quality standard by adding new interactive features, a second API integration, visual polish, and comprehensive documentation.

---

## Features Added in Assignment 4

| Feature | Type | File(s) |
|---|---|---|
| Scroll progress bar | Visual / UX | `css/styles.css`, `js/script.js` |
| Floating back-to-top button | UX | `css/styles.css`, `js/script.js` |
| Active nav link highlight | UX / Intersection Observer | `css/styles.css`, `js/script.js` |
| Scroll-reveal animations | Visual / Intersection Observer | `css/styles.css`, `js/script.js` |
| Animated stat counters | Visual / Canvas API | `css/styles.css`, `js/script.js` |
| GitHub Activity API widget | Second API integration | `index.html`, `js/script.js` |
| Difficulty badges on projects | UI | `index.html`, `css/styles.css` |
| Tech stack chips on projects | UI | `index.html`, `css/styles.css` |
| Project GitHub links | UX | `index.html`, `css/styles.css` |
| Contact social links card | UX | `index.html`, `css/styles.css` |
| Textarea character counter | UX | `index.html`, `js/script.js` |
| 2-column About grid | Layout | `css/styles.css` |
| 2-column Contact grid | Layout | `css/styles.css` |
| OG / Twitter meta tags | SEO | `index.html` |

---

## Architecture

The site is a single-page application with no build step:

```
index.html       → HTML structure and semantic markup
css/styles.css   → All styling, design tokens (CSS custom properties), responsive layout
js/script.js     → All interactivity, API calls, DOM manipulation
assets/images/   → Project and profile images (lazy-loaded)
```

### Design Token System

All colors and spacing are defined as CSS custom properties on `:root`, making theme switching trivial:

```css
:root {
  --bg: #070b18;
  --panel: #0b1230;
  --text: #e9eefc;
  --accent: #4798fb;
  /* ... */
}
:root[data-theme="light"] {
  --bg: #f7f8fc;
  --accent: #3b4bff;
  /* ... */
}
```

JavaScript sets `data-theme` on `<html>` and `localStorage` persists the choice.

---

## Feature Details

### Scroll Progress Bar

A `<div id="scrollProgress">` is positioned `fixed` at `top: 0` with `height: 3px`. A scroll event listener calculates `scrollY / (scrollHeight - innerHeight)` as a percentage and sets it as the element's `width`. Uses `{ passive: true }` for performance.

**Files:** `css/styles.css` (`.scroll-progress`), `js/script.js` (`initScrollProgress`)

---

### Intersection Observer — Active Nav & Scroll Reveal

Two separate `IntersectionObserver` instances handle different behaviors:

1. **Active nav** (`initActiveNav`): Observes all `section[id]` elements with `rootMargin: "-30% 0px -60% 0px"` so the active link updates when a section occupies the middle of the viewport. Removes `.active` from all links, then adds it to the matching anchor.

2. **Scroll reveal** (`initScrollReveal`): Applies `.reveal` (opacity 0, translateY 18px) to all `.card` elements via JavaScript. When a card enters the viewport at 8% threshold, `.visible` is added, triggering the CSS transition to full opacity/position. Cards are `unobserve`d after first trigger to avoid re-running.

---

### Animated Stat Counters

The `.hero-stats` container holds three `<span class="hero-stat-num" data-target="N">` elements. An `IntersectionObserver` fires when the container is 50% in view, then runs `animateNum()` for each span.

`animateNum` uses `requestAnimationFrame` with an ease-out quad formula:
```js
const eased = 1 - (1 - progress) * (1 - progress);
el.textContent = String(Math.round(eased * target));
```
This produces a smooth deceleration from 0 to the target number over ~1 second.

---

### GitHub Activity API Widget

**Endpoint:** `GET https://api.github.com/users/Muhannad-Melaifi`

**Response fields used:** `public_repos`, `followers`, `following`

**Error handling:** A `try/catch` wraps the fetch. If the request fails (network error, rate limit, etc.), a user-friendly message replaces the loading text. No toast is shown for this widget — the inline status message is sufficient.

**No caching** is applied here intentionally: the stats are low-traffic data and showing stale numbers could be misleading. The GitHub public API allows ~60 unauthenticated requests per hour per IP.

---

### Developer Quote Widget (from Assignment 3, enhanced)

**Endpoint:** `GET https://api.github.com/zen`

**Caching strategy:** On success, the quote is saved to `localStorage` (`lastQuoteText`, `lastQuoteAuthor`, `lastQuoteTime`). On subsequent loads, the cached version is shown immediately without a network call. The **New quote** button forces a network fetch (`forceNetwork = true`).

**Fallback chain:**
1. Show cached quote if available and not forcing network
2. Fetch from GitHub Zen API
3. On fetch failure: show cached quote with status message, OR show one of 5 hardcoded fallback quotes

---

### Project Search / Filter / Sort

The `initProjectSearch` function reads three controls: a text search input, a level `<select>`, and a sort `<select>`. On any change:

1. All project cards are sorted using `Array.sort` (by `data-year` or `h3` text).
2. Each card is tested against two conditions: `searchMatch && levelMatch`.
3. Cards are shown/hidden via `style.display`.
4. A dynamic hint string is assembled from current filter state.
5. The empty-state element is shown/hidden based on `shown` count.

---

### Form Validation and Character Counter

**Validation rules:**
- Name: minimum 2 characters
- Email: regex `/^[^\s@]+@[^\s@]+\.[^\s@]+$/`
- Message: minimum 10 characters

All errors are cleared before each validation pass. Errors are written into `<small class="error">` elements next to each field. A toast appears if any field fails.

**Character counter:** The `initCharCounter` function listens to `input` events on `#message` and updates `#charCount` with `len / max`. When `len > max * 0.9` (90% full), the `.warn` class turns the counter red.

---

## State Management

| State | Storage | Scope |
|---|---|---|
| Theme preference | `localStorage` | Persists across sessions |
| Visitor name | `localStorage` | Persists across sessions |
| Visit count | `localStorage` | Persists across sessions |
| Cached dev quote | `localStorage` | Persists across sessions |
| Session timer | Runtime (JS interval) | Lost on page close |

---

## Performance Considerations

- Project images use `loading="lazy"` — they are only fetched when near the viewport.
- Scroll and resize listeners use `{ passive: true }` where applicable.
- The dev quote is cached in localStorage to avoid redundant API calls.
- Scroll-reveal observers call `unobserve` after first trigger — no continuous observation.
- CSS animations use `transform` and `opacity` only, keeping repaints off the main thread (compositor-layer properties).
- No external JS libraries or CSS frameworks are loaded.

---

## Responsive Breakpoints

| Breakpoint | Behavior |
|---|---|
| `> 920px` | 2-column hero, 2-column about, 2-column projects, 2-column contact |
| `≤ 920px` | All grids collapse to single column |
| `≤ 720px` | Hamburger menu replaces horizontal nav |

---

## Accessibility

- Skip-to-content link for keyboard users
- All interactive elements have visible focus styles
- `aria-label` on icon-only buttons
- `aria-live="polite"` on the API widgets and visitor card for screen readers
- `aria-expanded` on the mobile nav toggle
- `role="status"` on the toast element
- Semantic HTML: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`, `<form>`, `<label>`
- `.sr-only` utility for screen-reader-only text

---

## Known Limitations

- Contact form is front-end only. No email is sent; the success toast is a UI simulation.
- GitHub API allows ~60 unauthenticated requests per hour per IP. If rate-limited, both API widgets show graceful fallback messages.
- Profile and project images are not included in this repository. Placeholders are shown instead.

---

## Previously Completed Features (Assignments 1–3)

- Dark / light theme with `localStorage` persistence
- Time-based greeting message
- Mobile hamburger navigation
- Contact form validation with inline errors and toast feedback
- Project search, level filter, and sort
- Developer Quote widget (GitHub Zen API) with caching and fallback
- Visitor Preferences panel (name, session timer, visit counter)
