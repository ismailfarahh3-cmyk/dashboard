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

`index.html` is the whole app: one self-contained page (HTML, CSS and JavaScript). No build step, no dependencies, no backend. Fonts load from Google Fonts (Young Serif, Nunito, Caveat).

It is built mobile-first — a bottom tab bar on phones, top tabs on wider screens — and works offline once the fonts are cached.

## Where your entries are saved

- Opened as a Claude artifact: to your private Claude account, so they follow you between devices.
- Anywhere else (GitHub Pages, a local file): to that browser's `localStorage`. Entries stay on that one browser, and clearing site data erases them.

To move data between the two, use **Back up everything** in the footer on one device and **Restore a backup** on the other. The restore merges rather than overwrites: identical entries are skipped, and where the same entry differs it keeps whichever copy was edited more recently, so importing the same file twice changes nothing.

## Run locally

Open `index.html` in a browser, or serve the folder:

    python3 -m http.server 8000
