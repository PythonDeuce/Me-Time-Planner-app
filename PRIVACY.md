# Me Time Planner privacy

Me Time Planner runs entirely on your computer.

## What stays local

- Settings, About, Export writes one backup file where you choose (your settings, notes, moments, quiz stats and the tray options); Import reads one you pick. Move to a synced folder copies your data into a folder you pick, which your sync service then handles under its own terms; Me Time Planner itself still sends nothing.
- An alarm or a reminder shows a card in the clock and a notification through your system's own notification service, on this computer only. "Add to calendar" writes an `.ics` file under `calendar/` in the settings folder and opens it with whatever handles calendar files on your computer; the file goes nowhere else. "Import calendar" reads an `.ics` file you pick and keeps only the events' titles and times; the file itself is not copied.
- Window positions and the tray options live in `state.json` in the same folder.
- "Detect my city" asks your system for a location once, matches it against a city list bundled with the app, and keeps only the city name and time zone. The coordinates are not stored or sent anywhere.
- The log file `timepeace.log` records startup, window events, and errors, and stays on your disk. It never includes note text or settings values.
- Updates leave this folder alone. A copy of `store.json` is taken right before an update installs (`backups/`), beside the copies taken at every start.

Folder locations:

- Windows: `%APPDATA%\Me Time Planner`
- macOS: `~/Library/Application Support/Me Time Planner`
- Linux: `~/.config/Me Time Planner`

## The MCP connector

When an assistant is configured to use Me Time Planner as an MCP server, it starts `Me Time Planner --mcp` itself and that process talks to the running clock over the loopback address only, authorized by a token the clock writes to `control.json` in its settings folder for the length of a run. The assistant sees what the tools return (your cities, the time there, note titles and text when it asks for them) and nothing else. Nothing is sent anywhere by Me Time Planner; what the assistant does with an answer is governed by that assistant.

## The two network requests

**The update check.** Once a day, and when you press "Check for updates" in Settings, About Me Time Planner, the app asks GitHub for the latest release of Me Time Planner:

`https://api.github.com/repos/PythonDeuce/Me Time Planner-app/releases/latest`

The request carries the app version in its User-Agent header and nothing else. GitHub sees your IP address, as any web request does. The answer tells the app whether a newer version exists.

When a newer version exists and Updates is set to Automatic in Settings, About Me Time Planner (the default), the app downloads that release's file for your system from GitHub, checks it against the checksum published with the release, keeps it in the `updates` folder beside your settings, and installs it the next time Me Time Planner starts (or when you choose Restart now), on Windows, Mac and Linux alike. The old build is kept beside the app as `.old` until the next start, in case the swap has to be undone. Set Updates to Manual and the app only tells you; you open the download page yourself.


**A link you press.** "Google" on a moment in Plan opens Google Calendar in your browser with that moment's title, time and city list in the address, so the entry is ready to save there. It happens only when you press it, and the app itself sends nothing.

There is no telemetry, no analytics, no crash reporting, and no account.

## Removing everything

Quit Me Time Planner and delete the folder above. That removes every setting, note, and log.
