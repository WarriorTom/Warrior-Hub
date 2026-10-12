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
| DVLA Tracker | `dvla.html` |
| Netradyne (violation coaching cards, weekly audit) | `netradyne.html` |
| MOT Tracker (MOT due dates, MOT bookings to the Calendar, VINs, spreadsheet import from a blank REG / VIN template) | `mot-tracker.html` |

Coming soon (shown greyed out on the home page and rail, not built yet): Kinesis.

All pages are single HTML files with no build step. They share a left-hand rail for switching pages, so keep them in the same folder.

## Data
- **No personal data is stored in this repository.** The Recruitment and DVLA pages ship empty; all driver data lives in the private Firebase database and is only readable by signed-in, approved managers.
- Load a list from a private backup file with **Import data** (bottom-left of Recruitment / DVLA). Use **Export data** to take backups.

## Sign-in
- Access is by invitation only, using Firebase Authentication (email + password) plus an approved-email list in Firestore. See `FIREBASE-SETUP.md`.

## MOT Tracker data
- Vehicles are stored in the Firestore collection `mot_vehicles`; MOT bookings are written into the Calendar's `bookings` collection. The 13 current vans load automatically the first time the page is opened while `mot_vehicles` is empty.
