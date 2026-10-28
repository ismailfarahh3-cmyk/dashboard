# Daybook

A personal dashboard for habits and goals, gym lifts, boxing and cardio, body weight, and a nightly journal.

## What is in it

- **Today:** greeting, weekly progress tiles, today's habits, and recent activity.
- **Habits & goals:** weekly tracker with streaks, goals with target dates, 12-week consistency map.
- **Gym:** log sessions (exercises, sets, weight, reps), per-lift progress charts, session history.
- **Cardio:** boxing rounds, runs, rides and more, with a weekly minutes target.
- **Body:** weigh-ins, a projected timeline to your goal weight with milestones, and a weight chart.
- **Journal:** a nightly page that saves as you write, with mood, prompts, search and export.

## How it runs

`index.html` is the whole app: one self-contained page (HTML, CSS and JavaScript). No build step and no bundler; Firebase loads from a CDN only if you have configured it. Fonts load from Google Fonts (Young Serif, Nunito, Caveat).

It is built mobile-first — a bottom tab bar on phones, top tabs on wider screens — and works offline once the fonts are cached.

## Where your entries are saved

The page picks the best of three, in this order:

1. **Your Google account**, once you sign in — entries live in Firestore under `users/{uid}` and sync live across every device. Needs the one-time setup in [SETUP.md](SETUP.md).
2. **Your Claude account**, when the page is opened as a Claude artifact.
3. **That browser's `localStorage`**, otherwise. Entries stay on the one browser and clearing site data erases them.

Signing in moves anything already in the browser up to your account, without duplicating what is already there. While signed in the browser copy is kept as a live mirror, so the data is in two places rather than one.

There is also **Back up everything** / **Restore a backup** in the footer for moving entries by hand. The restore merges rather than overwrites: identical entries are skipped, and where the same entry differs it keeps whichever copy was edited more recently, so importing the same file twice changes nothing.

## Run locally

Open `index.html` in a browser, or serve the folder:

    python3 -m http.server 8000
