# Me Time Planner

A planner that knows everyone's hours: tap a time on the day's strips, see what it is for every city, add the event, and let the alarms and goals come to you.

Me Time Planner is built from the same code as [TimePeace](https://github.com/PythonDeuce/TimePeace-app), the all in one desktop clock, and shares its wrapper (`desktop/widget.py`), its store, its settings and its windows. `scripts/derive_from_timepeace.py` rebuilds this folder from a TimePeace checkout; the product's own pieces are its name, icon, settings folder, repositories and the hub page the main window opens (`index.html?widget=1&tool=planhub`).

## Run from source

    pip install -r desktop/requirements.txt
    python desktop/widget.py

Windows can double click `MeTimePlanner.bat`. Settings live in the `Me Time Planner` folder under your user's application data.

## Releasing

`python scripts/release.py X.Y.Z` tags and pushes; the workflow builds Windows, macOS and Linux; `python scripts/publish.py X.Y.Z` publishes the build on `PythonDeuce/Me-Time-Planner-app`.

## License

MIT, see LICENSE.
