# Warrior Hub

Desktop web tools for the Warrior Logistics management team (DLS4 / HSA7 / DXFL / JOYL).

| Page | File |
|---|---|
| Home (landing page with tiles + colour picker) | `index.html` |
| Sign in | `login.html` |
| Daily Tasks | `daily-tasks.html` |
| Wave Plan Generator | `wave-plan-generator.html` |
| Posters | `posters.html` |
| Recruitment | `recruitment.html` |

All pages are single HTML files with no build step. They share a left-hand rail for switching pages, so keep them in the same folder.

Live site: `https://<your-github-username>.github.io/<repo-name>/`

## Data
- Right now each page saves to the browser it is opened in ("Local only").
- **No personal data is stored in this repository.** The Recruitment page ships empty; load your starters with **Import data** (bottom-left) from a private backup file, and use **Export data** to take backups.
- Firebase (shared live data) is set up as a separate step.

## Sign-in
- The sign-in page (`login.html`) is switched **off for now** so everything can be previewed. To turn it on, change `REQUIRE_LOGIN=false` to `true` in the guard script near the top of each page.
- When on, it is only a front door: the login is stored in the browser on that device and the files are public on GitHub Pages. Real protected, shared accounts come with Firebase Authentication (a separate step).
