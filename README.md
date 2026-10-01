# Me Time Planner

A planner that knows everyone's hours: tap a time on the day's strips, see what it is for every city, add the event, and let the alarms and goals come to you.

Me Time Planner began as the Plan of [TimePeace](https://github.com/PythonDeuce/TimePeace-app), the all in one desktop clock, and shares its wrapper (`desktop/widget.py`), its store, its settings and its windows. Since 0.2.0 it carries its own code on top: `js/plan-smart.js` (the planning rules), `js/desk.js` and `js/desk-more.js` (the desk), `js/mini.js` (the small windows), `js/holidays.js` (fifteen countries), `desktop/tp_extras.py` and `desktop/tp_qr.py` (the wrapper's hands and the QR code). `scripts/derive_from_timepeace.py` is kept for the record and refuses to run over them.

## The desk

- **Day**: the day under a quick-add line ("lunch with Ana Friday 1pm 90 min #work at Café Nord"), a now line, warnings when events collide, Roll forward, Next up with a countdown, Free today, who is awake, the budgets.
- **Week**: drag blocks to move them, stretch them, draw new ones.
- **Month**: how busy each day is, the free days, what is coming.
- **Goals**: milestones, dependencies, pace, a timeline, projects, Someday, routine bundles, Find me time, Plan my day, Paste an invite.
- **Habits**: days, streaks, chains, a tick a day.
- **Review**: the week in numbers against the week before, time budgets, the archive, undo, the year in review, exports, the week as text or a picture, your free times in any city's time.
- **Cities**: everyone's hours on the strips, who is awake, sunrise and sunset, trips, holidays.

The desk comes in thirty themes, fifteen light and fifteen dark, drawn in one soft style; pick one from the spheres in Settings, Look, or let a pair follow the system's light or dark mode. Drag the desk's edge or corner to size it, or pick a size in Settings.

The line also moves things: "move dentist to Thursday 3pm", "push everything after lunch 30 min". A repeating event can be moved alone (Only this one) or skipped; the card duplicates; a double click on empty space in Day adds an event there; ? shows Keys and the line. A `note:` link on an event (Copy link in HI Notes) opens that note in HI Notes.

Alarms escalate, speak, hold in quiet hours, during focus blocks and under do not disturb, wake the computer, fire on context ("when I am back"), and reach a phone through a webhook. Connect adds calendar subscriptions, a phone page with a QR code, a calendar feed, plans between computers and two small pinned windows. Every feature works on Windows, macOS and Linux; the system's own voice and timers are used where they differ.

## Run from source

    pip install -r desktop/requirements.txt
    python desktop/widget.py

Windows can double click `MeTimePlanner.bat`. Settings live in the `Me Time Planner` folder under your user's application data.

## Releasing

`python scripts/release.py X.Y.Z` tags and pushes; the workflow builds Windows, macOS and Linux; `python scripts/publish.py X.Y.Z` publishes the build on `PythonDeuce/Me-Time-Planner-app`.

## License

MIT, see LICENSE.
