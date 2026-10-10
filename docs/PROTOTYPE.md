# Captain Waypoint dashboard prototype

The first interactive browser prototype is available at the repository root in `index.html`.

## Preview it

- Open the file on GitHub: https://github.com/Vlieger202/COMMAND-CENTER/blob/main/index.html
- To run it locally, download `index.html` and open it in a modern browser. It does not need a build step or npm installation.

## Publish with GitHub Pages

Because `index.html` is in the repository root, GitHub Pages can serve it as a static site:

1. Open the repository Settings.
2. Open Pages in the Code and automation section.
3. Under Build and deployment, choose Deploy from a branch.
4. Select branch `main` and folder `/ (root)`, then save.
5. Wait for GitHub Pages to finish publishing; the Pages panel will show the site URL.

## Prototype limitations

This is a visual and interactive frontend prototype. Toggles, mission edits, PC/PlayStation status, coffee, weather, aircraft, calendar and system monitor are not connected to live services. The controls only demonstrate the intended UI. Do not rely on these simulated values as real device state.

Next development steps:
1. Connect the prototype to real Home Assistant entities.
2. Add lights and roller-blind controls only after identifying the real entity IDs.
3. Connect a supported calendar integration for Flight Ops.
4. Determine a supported FlightRadar data source before displaying aircraft data.
5. Replace weather and system-monitor placeholders with actual integrations/sensors.

Keep passwords, API keys, tokens, private calendar data and personal Home Assistant configuration out of this public repository.
