# Daybook

A personal dashboard for habits and goals, gym lifts, boxing and cardio, body weight, a Google Calendar view, and a nightly journal.

## What is in it

- **Today:** greeting, weekly progress tiles, today's habits, recent activity, and what is coming up on your calendar.
- **Calendar:** month view of your Google Calendar, with training days marked.
- **Habits & goals:** weekly tracker with streaks, goals with target dates, 12-week consistency map.
- **Gym:** log sessions (exercises, sets, weight, reps), per-lift progress charts, session history.
- **Cardio:** boxing rounds, runs, rides and more, with a weekly minutes target.
- **Coach:** weigh-ins, a projected timeline to your goal weight with milestones, an AI trainer that builds a workout plan and meal plan, and a chat for questions.
- **Journal:** a nightly page that saves as you write, with mood, prompts, search and export.

## How it runs

`index.html` is the whole app: one self-contained page (HTML, CSS and JavaScript).

- Inside Claude (as an artifact), data is saved to the viewer's private account, and the Calendar and Coach features work through Claude's connector and sampling capabilities.
- Anywhere else (for example GitHub Pages), it saves to the browser's localStorage. The Calendar and Coach sections show a note instead, because they need Claude.
- Fonts load from Google Fonts (Young Serif, Nunito, Caveat).

## Run locally

Open `index.html` in a browser, or serve the folder:

    python3 -m http.server 8000
