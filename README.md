# Muhannad — Personal Portfolio (Assignment 4)

A responsive, production-quality personal portfolio website built with HTML, CSS, and JavaScript.
This is the final assignment deliverable — a polished, fully featured web application ready to share publicly.

---

## Project Overview

This portfolio showcases my background, technical skills, and software projects as a Software Engineering student at KFUPM. It combines clean design, interactive JavaScript features, two live API integrations, and accessibility best practices into a single deployable application.

---

## Live Deployment

Live Site: <https://muhannad-melaifi.github.io/202253960-MuhannadAlMelaifi-assignment4/>

---

## Features

### Layout and Design
- Responsive layout adapting to mobile, tablet, and desktop
- Dark and light themes with preference saved in `localStorage`
- Smooth scroll reveal animations on all cards (Intersection Observer API)
- Animated scroll progress bar at the top of the page
- Floating back-to-top button that appears after scrolling

### Navigation
- Sticky glassmorphism header
- Mobile hamburger menu with accessible toggle
- Active section highlighting: the nav link for the visible section is highlighted automatically

### Hero Section
- Time-based greeting (morning / afternoon / evening)
- Animated stat counters (Projects, Technologies, Years Coding) that count up on load

### About Section
- Personal bio card
- Technical skills chips (Java, Python, HTML/CSS/JS, Flutter, MySQL, Git)
- Visitor Preferences panel: save your name, track session time, count browser visits
- Developer Quote widget: fetches from the GitHub Zen API with caching and offline fallback
- **GitHub Activity widget**: fetches live public repo count, followers, and following from the GitHub API

### Projects Section
- Three project cards with difficulty badges, tech stack chips, and GitHub links
- Real-time search filtering by text and tags
- Level filter (All / Beginner / Advanced)
- Sort options (Newest / Oldest / Name A–Z)
- Dynamic hint text and empty-state message
- Lazy-loaded images with emoji fallback

### Contact Section
- Contact form with multi-field validation (name, email, message)
- Character counter on the message field (max 500)
- Toast notifications for user feedback
- Social links card (GitHub, LinkedIn) alongside the form

### Footer
- Dynamic copyright year
- GitHub link and back-to-top link

---

## Setup Instructions

### Run Locally

1. Clone or download this repository:
   ```
   git clone https://github.com/Muhannad-Melaifi/202253960-MuhannadAlMelaifi-assignment4.git
   ```
2. Open the project folder in VS Code.
3. Install the **Live Server** extension if not already installed.
4. Right-click `index.html` and select **Open with Live Server**.
5. The site opens at `http://127.0.0.1:5500` (or similar).

No build tools, package managers, or backend server are required. Everything runs in the browser.

### Deploy to GitHub Pages

1. Push the repository to GitHub.
2. Go to **Settings → Pages**.
3. Set the source to the `main` branch, root folder.
4. GitHub generates a live URL within a few minutes.

---

## How to Use the Website

### First-time visitors
1. Start at the top navigation bar and click **About** to read profile information.
2. Scroll down or click **Projects** to see the project showcase.
3. Use the search bar and filters to explore projects by keyword or skill level.
4. Click **Contact** to reach the contact form or social links.

### Using the Developer Quote widget
- The widget loads a quote from the GitHub Zen API on page open.
- Click **New quote** to fetch a fresh quote from the network.
- If the API is unavailable, a cached or fallback quote is shown automatically.

### Using the GitHub Activity widget
- The widget fetches live stats from the GitHub API on page load.
- It shows public repository count, followers, and following for the GitHub profile.
- Click **View Profile** to open the full GitHub profile in a new tab.

### Using the Project Search
- Type any keyword (e.g., `java`, `api`, `react`) to filter matching projects.
- Select a difficulty level or sort order using the dropdowns.
- Click **Clear** to reset all filters at once.

### Using Visitor Preferences
- Enter your name and click **Save name** for a personalized welcome message.
- Session time starts counting from your first page load.
- Visit count increments each time you open the page in this browser.

### Theme Toggle
- Click **Dark / Light** in the header to switch themes.
- Your choice is saved and remembered on your next visit.

---

## File Structure

```
202253960-MuhannadAlMelaifi-assignment4/
├── README.md
├── index.html
├── css/
│   └── styles.css
├── js/
│   └── script.js
├── assets/
│   └── images/
│       ├── profile.jpg
│       ├── project-horse-racing.jpg
│       ├── project-reservation.jpg
│       └── project-labtrack.png
├── docs/
│   ├── ai-usage-report.md
│   └── technical-documentation.md
├── presentation/
│   ├── slides.pdf
│   └── demo-video.mp4
└── .gitignore
```

---

## Browser Compatibility

Tested on modern evergreen browsers:
- Chrome 120+
- Firefox 120+
- Edge 120+
- Safari 17+

Uses standard web APIs: CSS Grid, Flexbox, CSS custom properties, Intersection Observer, Fetch API, localStorage. No polyfills needed for modern browsers.

---

## AI Documentation

- Detailed AI usage report: [docs/ai-usage-report.md](docs/ai-usage-report.md)
- Technical documentation: [docs/technical-documentation.md](docs/technical-documentation.md)

AI tools used: Claude (Anthropic), GitHub Copilot.
