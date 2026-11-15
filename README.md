# Warrior Hub

Desktop web tools for the Warrior Logistics management team (DLS4 / HSA7 / DXFL / JOYL).

| Page | File |
|---|---|
| Home (landing page with tiles + colour picker) | `index.html` |
| Sign in | `login.html` |
| Daily Tasks | `daily-tasks.html` |
| Wave Plan Generator | `wave-plan-generator.html` |
| Posters | `posters.html` |
| Calendar (all diary bookings, month / week / day / agenda) | `calendar.html` |
| Recruitment | `recruitment.html` |
| Netradyne (violation coaching cards, weekly audit) | `netradyne.html` |
| PAVE (monthly van condition grades, fleet % Great vs 90% target) | `pave.html` |
| Performance (weekly NoA report generator: overview + coaching cards, saved driver ID database) | `performance.html` |
| Tools (Max Returns, Daily DCR, Weekly DCR, Weekly POD, SPR, Weekly Netradyne calculators) | `tools.html` |

Coming soon (shown greyed out on the home page and rail, not built yet): Kinesis.

All pages are single HTML files with no build step. They share a left-hand rail for switching pages, so keep them in the same folder.

## Data
- **No personal data is stored in this repository.** The Recruitment page ships empty; all driver data lives in the private Firebase database and is only readable by signed-in, approved managers.
- Load a list from a private backup file with **Import data** (bottom-left of Recruitment). Use **Export data** to take backups.

## Sign-in
- Access is by invitation only, using Firebase Authentication (email + password) plus an approved-email list in Firestore. See `FIREBASE-SETUP.md`.

