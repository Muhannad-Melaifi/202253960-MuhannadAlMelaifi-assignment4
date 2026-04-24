# Muhannad Portfolio (Assignment 3)

A responsive personal portfolio website built with HTML, CSS, and JavaScript.
It includes About, Projects, and Contact sections with interactive behavior and clear user feedback.

## Features

- Responsive layout for mobile, tablet, and desktop
- Sections: About, Projects, Contact
- JavaScript interactivity:
  - Theme toggle (saved in localStorage)
  - Greeting message based on time of day
  - Smooth scrolling navigation
  - Contact form validation with multi-step checks and toast feedback (front-end only)
  - Live project search/filter with empty-state message
  - Project level filter (Beginner/Advanced)
  - Project sorting (Newest/Oldest/Name A-Z)
  - Dynamic guidance text based on selected filters
  - Public API widget using fetch with loading, success, and error states
  - Visitor state panel:
    - Save and clear visitor name using localStorage
    - Session timer showing time spent on the site
    - Browser visit counter

## Assignment 3 Requirement Coverage

- API Integration: Developer Quote widget connected to GitHub Zen API with fallback and caching.
- Complex Logic: Combined search + level filter + sorting with conditional feedback text.
- State Management: Theme preference, visitor name, and visit count stored in localStorage.
- Performance: Lazy-loaded project images, lightweight animations, and minimal DOM updates.
- Code Quality: Organized HTML/CSS/JS structure with readable functions and comments.

## Compatibility

- Designed for modern evergreen browsers such as Chrome, Edge, Firefox, and Safari.
- Uses responsive layouts for mobile, tablet, and desktop screens.
- Navigation, filtering, and form validation work without a backend.

## Setup Instructions

1. Clone or download this repository.
2. Open the project folder in VS Code.
3. Run `index.html` using Live Server.

## How to Use the Website (Step-by-Step)

1. Start at the top navigation bar and click About to read profile information.
2. Click Projects to jump to the projects section.
3. In Projects:

- Type a keyword in the search field (example: `js`, `api`, `ui`).
- Pick a level filter (All, Beginner, Advanced).
- Pick a sorting mode (Newest, Oldest, Name A-Z).
- Matching project cards remain visible while non-matching cards are hidden.
- If no match is found, an empty-state message appears to guide the user.
- Use the clear search control to reset and view all projects again.

4. In the API widget:

- Wait for loading text while data is fetched.
- Review the loaded content.
- Click the refresh button to request new data.
- If the API is unavailable, a friendly fallback message is shown.

5. Click Contact to open the form.
6. Enter your name, email, and message, then submit.
7. If fields are invalid, inline validation explains what to fix.
8. After valid input, a toast confirms successful submission flow (UI-only, no backend send).
9. Use the theme toggle at any point to switch appearance; your preference is remembered.
10. In Visitor Preferences:

- Enter your name and click Save name for personalized state.
- Track live session time while browsing.
- Review visit count for this browser.

## Navigation Guidance Summary

- Main path for first-time users: About -> Projects -> API widget -> Contact.
- Main path for recruiters/instructors: Projects first, then Contact.
- All major interactions provide immediate on-screen feedback.

## AI Documentation

- Detailed AI usage report: docs/ai-usage-report.md
- Technical documentation: docs/technical-documentation.md

## Live Deployment

Live Site: <https://muhannad-melaifi.github.io/202253960-MuhannadAlMelaifi-assignment3/>
