# Health Care America

> Making Sense of Health Insurance One Person at a Time

An interactive learning game where the player is an intern at Health Care America (HCA), an advocacy nonprofit that helps community members understand health insurance. The player works through a backlog of client cases (Emmanuel, Vanessa, Randall, Emma), reviews relevant health-insurance terms for each case, and decides how to advise — balancing a **Community Wellness** meter and a limited **Assistance Fund**.

This is a web rebuild of an Adobe Captivate SCORM project. All game content (scenarios, choices, scoring, vignettes) is verbatim from the original `HI Game Content.xlsx` spec, including original copy quirks.

## Play

Open `index.html` in any modern browser, or visit the deployed GitHub Pages URL.

## How it deploys

Static single-page app. No build step required.

- `index.html` — the entire app (React via CDN, Tailwind via CDN, Babel-standalone for in-browser JSX)
- `assets/` — illustrations and the HCA logo

To deploy via GitHub Pages: **Settings → Pages → Source: Deploy from a branch → Branch: `main` / `/ (root)`**. The game will be live at `https://[your-username].github.io/[repo-name]/` within a minute.

External dependencies (loaded from `unpkg.com` at runtime): React 18, ReactDOM 18, Tailwind CSS, Babel Standalone.

## Where the content lives

All game data is in `index.html` between the comment markers. To edit:

- **Terms shown in the Health Insurance Guide** → `const TERMS = [...]`
- **Category groupings (What You Pay / Who Provides Care / The Law)** → `const CATEGORIES = {...}`
- **Intro slides (Welcome, You're Hired, Your Goal, On the Job Training)** → `const INTRO_SLIDES = [...]`
- **Client scenarios (profile, inquiry, terms, choices, outcomes, vignette)** → `const SCENARIOS = [...]`
- **Starting meter values** → `START_WELLNESS = 50`, `START_FUND = 5000`

Choice scoring follows an Ok / Better / Best rubric based on whether the choice prioritizes learning vs. throwing money at the problem. Money-without-learning choices drop wellness.

## Game flow

1. **Welcome screen** → Start
2. **You're Hired!** (intro)
3. **Your Goal** (meters explained)
4. **On the Job Training** (instructions)
5. **Health Insurance Guide** (9 terms grouped by category)
6. For each client (Emmanuel → Vanessa → Randall → Emma):
   - **Client Profile + Inquiry** → Continue to review some terms
   - **Terms Review** (subset relevant to this case) → Continue to advise
   - **Advise** (case details + 3 choice buttons)
   - **Feedback** (per-choice outcome + meter impact + educational vignette)
7. **Win** (made it through all four), **Lose: Out of Money**, or **Lose: Community Wellness Dropped**

## Credits

Original content and game design: Juli James.
Original implementation: Adobe Captivate (SCORM).
Web rebuild: 2026.
