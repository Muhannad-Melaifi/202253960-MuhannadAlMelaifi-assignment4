# Technical Documentation (Assignment 3)

## Overview

This Assignment 3 builds on Assignment 1+2 by adding more interactivity and modern JavaScript behavior:

### New features added in Assignment 3

1. **Live project search/filter** (dynamic content)
2. **API widget** (data handling using `fetch()`)
3. **Project sorting + level filtering** (multi-condition logic)
4. **Visitor state panel** (localStorage + timer + visit counter)
5. **Improved user feedback**:
   - Empty state when no projects match
   - Loading indicator while fetching API data
   - Friendly error message if API fails

The Assignment 1+2 features remain (theme toggle saved in localStorage, greeting message, form validation + toast notifications).

---

## User Journey Example (Step-by-Step)

1. User opens the page and reads About information.
2. User saves their name in the Visitor Preferences card (optional).
3. User sees session timer and visit count update.
4. User navigates to Projects from the main navigation.
5. User enters a keyword in the project search input.
6. User chooses level filter and sorting mode.
7. Matching cards remain visible; non-matching cards are hidden.
8. If no result is found, the empty-state message appears.
9. User views the API widget and waits for loading to finish.
10. User can refresh API content or see fallback/error messaging when needed.
11. User navigates to Contact, fills the form, and receives validation or success feedback.

---

## Dynamic Content: Project Search/Filter

### What it does

- A search input allows users to filter projects live while typing.
- Projects are shown/hidden based on whether the query matches:
  - The visible text content of the project card, OR
  - A `data-tags` attribute attached to each project.

### Files involved

- `index.html`
  - Search input: `#projectSearch`
  - Level filter: `#projectLevel`
  - Sort control: `#projectSort`
  - Dynamic hint: `#projectHint`
  - Clear button: `#clearSearch`
  - Empty state message: `#projectsEmpty`
  - Project cards: `.project.card` with `data-tags="..."`
  - Project metadata attributes: `data-level`, `data-year`

- `js/script.js`
  - Listens to `input` and `change` events on search/filter/sort controls
  - Sorts cards by year or alphabetical order
  - Shows/hides project cards by setting `style.display`
  - Toggles empty state when zero projects match
  - Updates conditional guidance text based on selected rules

### User feedback

- If there are no matches:
  - Displays: “No projects found. Try a different keyword.”

---

## Data Handling: Public API Widget

### What it does

- Fetches dynamic content from a public API using `fetch()`.
- Displays:
  - Loading text while waiting
  - The returned content on success
  - A friendly error message on failure
- Includes a button to refresh/reload the data.

### Files involved

- `index.html`
  - Widget elements:
    - `#quoteStatus` (loading/error/success hint)
    - `#quoteText` (content output)
    - `#quoteAuthor` (source/author text)
    - `#refreshQuote` (reload button)

- `js/script.js`
  - Uses `async/await` and `try/catch` for error handling
  - Updates the UI based on:
    - loading → success → error states

### Error handling

- If the API fails:
  - Shows a friendly message on the page
  - Also triggers a toast message for additional feedback

---

## Complex Logic Implementation

The projects section demonstrates chained decision logic:

1. Read three inputs (search query, level filter, sort mode).
2. Sort full project list based on selected rule.
3. Evaluate each project against two matching conditions:
   - search text/tags
   - selected level
4. Render only matching cards.
5. Update guidance text and empty-state visibility.

This provides a clear multi-step flow that goes beyond a single click action.

---

## State Management

State is managed through localStorage and runtime memory:

- Theme mode is persisted in localStorage.
- Visitor name is saved/loaded from localStorage.
- Visit counter increments on each page load and is stored in localStorage.
- Session timer is runtime state updated every second.

### Files involved

- `index.html`
  - `#visitorName`, `#saveVisitorName`, `#clearVisitorName`
  - `#visitorWelcome`, `#sessionTimer`, `#visitCount`
- `js/script.js`
  - Handles save/clear actions
  - Restores stored values on load
  - Runs timer interval updates

---

## Performance and Optimization

- Project images use `loading="lazy"`.
- API quote is cached to reduce repeated network requests.
- DOM updates are grouped inside reusable rendering functions.
- CSS/JS are separated and loaded once (simple static architecture).

## Compatibility

- The layout is responsive and adapts to mobile, tablet, and desktop breakpoints.
- The site is intended for modern evergreen browsers that support ES6, fetch, localStorage, and CSS grid/flexbox.
- Native form controls, select menus, and the navigation drawer are styled to remain usable in both light and dark themes.

Recommended final check before submission:

1. Run a Lighthouse audit and record key metrics.
2. Compress any large images in `assets/images` if needed.
3. Re-test mobile navigation and project controls on small screens.

---

## Animations / Transitions

- Button hover effects and card styling are handled via CSS.
- Toast messages use CSS transitions for a smooth appearance.
- The API widget loading state includes a subtle shimmer animation on the loading text (lightweight and non-distracting).

---

## Previously Completed Features 

- **Theme toggle** with preference saved in `localStorage`
- **Greeting message** based on time of day
- **Contact form validation** with inline error messages
- **Toast notifications** for user feedback

---

## Known Limitations

- Contact form is front-end only (no backend submission).
- API content depends on network availability and the API uptime.

## API Reliability Note

- The quote widget caches the last successful quote in localStorage and falls back to an offline quote if the API is unavailable or rate-limited.
