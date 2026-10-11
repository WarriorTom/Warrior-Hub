# Firebase setup for Warrior Hub: step by step (with sign-in)

Do GITHUB-SETUP.md first so the site is live. Then do this. It takes about 20 minutes.

## What Firebase will do for you
- **Shared live data**: Daily Tasks, Recruitment and Posters save to one place, so every manager sees the same thing on any device.
- **Real sign-in**: only people you approve can open the pages or read the data.
- It is free on Google's "Spark" plan for a team this size. No card needed.

## How accounts work (the short version)
This is an **invite-only** system. Nobody can sign themselves up.
1. **You (Tom) create each person's account** in the Firebase console: their email and a temporary password.
2. **You add their email to an approved list** (one tiny entry per person; Part 5). This is what actually protects the data.
3. The person opens the site and lands on the **Sign in** page. They type their email and password and go to the Hub.
4. They can use **Forgot password** on the sign-in page. Firebase emails them a reset link, so you never need to know their password.
5. To remove someone, delete them from the approved list (and delete the account). They are locked out straight away.
There is no "Create account" button on the site. The sign-in page only signs in.

Why the approved list matters: the Firebase key sits in the public page code (that is normal and safe), but without the list anyone could create an account against the project directly. The list stops that.

## Part 1: Create the project
1. Go to **console.firebase.google.com** and sign in with a Google account (use a work or shared one you will keep).
2. Click **Create a project**, name it `warrior-hub`, click Continue.
3. Turn **Google Analytics off** (not needed), click **Create project**, then **Continue**.

## Part 2: Register the web app and get your config
1. On the project home click the **web icon** (`</>`).
2. App nickname: `warrior-hub-web`. Leave "Firebase Hosting" **unticked**. Click **Register app**.
3. You will see a block of code with `firebaseConfig = { apiKey: ..., authDomain: ..., projectId: ..., storageBucket: ..., messagingSenderId: ..., appId: ... }`.
4. **Copy that whole block and send it to me.** These values are not secrets. I will put them into every page.
5. Click **Continue to console**.

## Part 3: Turn on sign-in
1. Left menu: **Build** then **Authentication**, click **Get started**.
2. Tab **Sign-in method**: choose **Email/Password**, switch **Enable** on (leave "Email link" off), **Save**.
3. Tab **Settings** then **Authorised domains**: click **Add domain** and add `YOUR-USERNAME.github.io`.
   (`localhost` is already there.)

## Part 4: Create the database
1. Left menu: **Build** then **Firestore Database**, click **Create database**.
2. Location: choose **eur3 (europe-west)** or **europe-west2 (London)**. This cannot be changed later.
3. Choose **Start in production mode**, click **Create**.

## Part 5: Lock it down (the important bit)
1. In Firestore open the **Rules** tab, delete what is there and paste this exactly, then **Publish**:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    function approved() {
      return request.auth != null
        && exists(/databases/$(database)/documents/allowed/$(request.auth.token.email));
    }
    match /allowed/{email} {
      allow read: if request.auth != null && request.auth.token.email == email;
      allow write: if false;
    }
    match /{document=**} {
      allow read, write: if approved();
    }
  }
}
```

2. Open the **Data** tab, click **Start collection**, Collection ID: `allowed`.
3. Document ID: your email in **all lowercase** (for example `tom@yourcompany.com`). Add one field: `ok` (boolean) = `true`. Save. Optional: add a second field `name` (string) with their display name, for example `Tom Jackson`; it is shown on the home page and used for "done by" labels.
4. Repeat **Add document** for each manager who should have access (lowercase email as the Document ID).

## Part 6: Create the accounts
1. **Authentication** then **Users** tab, click **Add user**.
2. Enter the person's email and a temporary password (at least 6 characters). Click **Add user**.
3. Do this for yourself and each manager. Tell them their temporary password privately, and tell them to use **Forgot password** to set their own.

## Part 7: Send me the config, then I finish the pages
Send me the `firebaseConfig` block from Part 2. I will then:
- put it into Daily Tasks, Recruitment, Posters and the Hub;
- switch **Sign-in** on in all pages (it is off right now) and connect `login.html` to Firebase, with Forgot password and Sign out;
- connect **Recruitment** to Firebase (it currently saves only in the browser; Daily Tasks and Posters are already built for Firebase);
- send you a new zip to upload to GitHub (Part 5 of GITHUB-SETUP.md).

## Part 8: First run after that
1. Open `https://YOUR-USERNAME.github.io/warrior-hub/` and sign in with your account.
2. Open Recruitment and click **Import data**, then choose `recruitment-data-2026-10-03.json`. It now saves to Firebase for everyone who is signed in.
3. Ask a manager to sign in on their own device and check they see the same data.

## Good to know
- **Keep the JSON file private.** After the first import you can use **Export data** for backups.
- **Poster images** are saved inside the database. Large images may need to be smaller; I will test this when wiring it.
- If someone says "missing or insufficient permissions", their email is missing (or not lowercase) in the `allowed` list.
- Firestore's free limits (50k reads and 20k writes a day) are plenty for this team.
