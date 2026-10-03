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
| DVLA Tracker | `dvla.html` |

All pages are single HTML files with no build step. They share a left-hand rail for switching pages, so keep them in the same folder.

## Data
- **No personal data is stored in this repository.** The Recruitment and DVLA pages ship empty; all driver data lives in the private Firebase database and is only readable by signed-in, approved managers.
- Load a list from a private backup file with **Import data** (bottom-left of Recruitment / DVLA). Use **Export data** to take backups.

## Sign-in
- Access is by invitation only, using Firebase Authentication (email + password) plus an approved-email list in Firestore. See `FIREBASE-SETUP.md`.
