# Daybook

A personal dashboard for habits and goals, gym lifts, boxing and cardio, body weight, and a nightly journal.

## What is in it

- **Today:** greeting, weekly progress tiles, today's habits, and recent activity.
- **Habits & goals:** weekly tracker with streaks, goals with target dates, 12-week consistency map.
- **Gym:** log sessions (exercises, sets, weight, reps), per-lift progress charts, session history.
- **Cardio:** boxing rounds, runs, rides and more, with a weekly minutes target.
- **Coach:** weigh-ins, a projected timeline to your goal weight with milestones, an AI trainer that builds a workout plan and meal plan, and a chat for questions.
- **Journal:** a nightly page that saves as you write, with mood, prompts, search and export.

## How it runs

`index.html` is the whole app: one self-contained page (HTML, CSS and JavaScript). Fonts load from Google Fonts (Young Serif, Nunito, Caveat).

**Where your entries are saved**

- Inside Claude (as an artifact): to your private Claude account, so they follow you between devices.
- Anywhere else (GitHub Pages, local file): to that browser's `localStorage`. Entries stay on that one browser, and clearing site data erases them. Use the export buttons on the Journal tab to keep a copy.

**The AI trainer**

- Inside Claude, it runs on Claude directly. Nothing to set up.
- Outside Claude, open the Coach tab and paste an [Anthropic API key](https://console.anthropic.com/settings/keys) into "Connect your trainer". Calls are billed to that API account, so set a spending limit on the key.

The key is kept in that browser's `localStorage` only. It is never in this repository, never sent anywhere but `api.anthropic.com`, and anyone with access to that browser profile can read it — so only save a key on a device you trust, and use "Remove key" on a shared machine.

## Run locally

Open `index.html` in a browser, or serve the folder:

    python3 -m http.server 8000
