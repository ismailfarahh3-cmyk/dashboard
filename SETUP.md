# Setting up Google sign-in

The dashboard works without this — it just saves to whatever browser you
opened it in. Do the steps below once and your entries follow your Google
account to every device instead.

It all runs on Firebase's free Spark plan. No card required.

## 1. Create the project

1. Go to https://console.firebase.google.com and click **Create a project**.
2. Name it anything (`daybook` is fine).
3. Turn **Google Analytics off** — nothing here uses it.

## 2. Turn on Google sign-in

1. In the left sidebar: **Build → Authentication → Get started**.
2. Open the **Sign-in method** tab, pick **Google**, toggle **Enable**.
3. Pick a support email (your own), then **Save**.

## 3. Create the database

1. Left sidebar: **Build → Firestore Database → Create database**.
2. Choose a location near you (`northamerica-northeast1` is Montreal).
3. Start in **production mode** — the rules in step 4 replace the default.

## 4. Lock it down

Open the **Rules** tab, replace everything with this, and click **Publish**:

    rules_version = '2';
    service cloud.firestore {
      match /databases/{database}/documents {
        match /users/{uid}/{document=**} {
          allow read, write: if request.auth != null && request.auth.uid == uid;
        }
      }
    }

This is the part that actually protects your data: it says a signed-in
account can read and write only its own documents, and nobody can touch
anyone else's. Do not skip it.

## 5. Allow the site to sign you in

1. **Authentication → Settings → Authorized domains → Add domain**.
2. Add `ismailfarahh3-cmyk.github.io`.

`localhost` is already on the list, so opening the file locally works too.

## 6. Paste your config

1. Click the gear icon → **Project settings**.
2. Under **Your apps**, click the web icon (`</>`), give it a nickname,
   and **Register app**. Skip the hosting offer.
3. Copy the `firebaseConfig` values it shows you.
4. Open `index.html`, find `const FB_CONFIG={` near the top of the
   `<script>`, and replace the six `PASTE_…` values with yours.
5. Commit and push.

Those values are public by design — they identify your project, they
don't grant access to it. The rules in step 4 are what keep your data
yours. Firebase shows them in client code on purpose.

## 7. Check it

Open the site, scroll to the bottom, click **Sign in with Google**.
The pill in the header should change to "Synced to your Google account",
and anything already in that browser gets moved up to your account the
first time. Sign in on your phone and the same entries appear.

## If something goes wrong

- **`auth/unauthorized-domain`** — step 5 is missing or has a typo.
- **Popup closes instantly / nothing happens** — a popup blocker. The page
  retries with a full-page redirect, so allow popups or just wait.
- **"Missing or insufficient permissions"** — the step 4 rules weren't
  published, or the path doesn't match `users/{uid}`.
- **Header still says "not synced"** — the config in step 6 is still the
  `PASTE_…` placeholders, or the file didn't get pushed.
