# GitHub setup: step by step

## What you have
- `warrior-hub.zip`: the 6 pages + README + .gitignore (unzip it first). **No driver data inside.**
- `recruitment-data-2026-10-03.json`: your starters. **Keep this file private. Never upload it to GitHub.**
- This guide.

## One thing to know first
GitHub Pages on a free account needs a **public** repository, so anyone with the link can open the pages.
That is why the Recruitment page in the zip starts empty and your starters live in the JSON file instead.
(A private repo with Pages needs a paid GitHub plan.)
The **Demo** button on every page fills it with made-up sample data, so you can show people the tools without any real data.

## Part 1: Create the repository
1. Go to **github.com** and sign in (or create a free account).
2. Click **+** (top right) then **New repository**.
3. Repository name: `warrior-hub` (letters, numbers and dashes only; it becomes part of the web address).
4. Choose **Public**.
5. Leave **Add a README file** unticked (ours is included).
6. Click **Create repository**.

## Part 2: Upload the files
1. Unzip `warrior-hub.zip` on your computer.
2. On the empty repo page click **uploading an existing file** (or **Add file** then **Upload files**).
3. Open the unzipped folder and select **all the files inside it** (not the folder itself) and drag them in:
   `index.html`, `login.html`, `daily-tasks.html`, `recruitment.html`, `wave-plan-generator.html`, `posters.html`, `calendar.html`, `dvla.html`, `netradyne.html`, `mot-tracker.html`, `pave.html`, `README.md`
   (`.gitignore` is a hidden file and is optional; it is fine to skip it.)
4. Do **not** add `recruitment-data-2026-10-03.json`.
5. Scroll down, leave the message as it is, click **Commit changes**.

## Part 3: Switch on the website
1. In the repo click **Settings** (top row of tabs).
2. Left menu: **Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
4. Branch: **main**, folder: **/ (root)**, then **Save**.
5. Wait 1 to 2 minutes and refresh that page. A banner appears: *Your site is live at*
   `https://YOUR-USERNAME.github.io/warrior-hub/`
6. Open it. You land on the Warrior Hub with tiles for each tool and the colour picker.
   (Sign-in is switched off for now, so you go straight in.)

## Part 4: Load your starters
1. Open `https://YOUR-USERNAME.github.io/warrior-hub/recruitment.html`.
2. In the left panel click **Import data** and pick `recruitment-data-2026-10-03.json`.
3. Confirm. Your starters appear.
Until Firebase is on, the data lives in that browser only. Use **Export data** regularly as a backup, and use the same browser each time.

## Part 5: Updating a page later
1. In the repo click **Add file** then **Upload files**.
2. Drop in the new version of the page with the **same file name** (it replaces the old one).
3. Click **Commit changes**. The live site refreshes in about a minute.

## Quick check once it is live
- Home page loads and the 4 tiles open the right pages.
- Click **Demo** on the home page: every page fills with sample data. Click **Exit demo** to go back.
- Recruitment page shows empty until you import your file.

## Optional: command line instead of drag and drop
```
git clone https://github.com/YOUR-USERNAME/warrior-hub.git
cd warrior-hub
# copy the files in, then:
git add .
git commit -m "Update pages"
git push
```

## Next
Firebase (shared live data across devices) comes next, only when you ask. Before any personal data goes into Firebase it needs sign-in protection, because the public link would otherwise let anyone read it.
