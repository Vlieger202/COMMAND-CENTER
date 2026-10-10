# Captain Waypoint Command Center

**Project:** Project COMMAND CENTER  
**Status:** Design and learning phase  
**Primary goal:** Build a personal, aviation-inspired Home Assistant dashboard for a dedicated tablet in the living room.

## Vision

Captain Waypoint Command Center is a dark, cockpit-inspired dashboard with a practical focus on status, planning, smart-home controls, and personal projects. The tablet is planned to have a microphone and speaker for future voice interaction.

The project will be built gradually. Learn the software and validate the design before purchasing dedicated hardware.

## Dashboard sections

- **Captain Waypoint Status** — the main header should communicate the current status of Captain Waypoint, rather than a generic slogan.
- **Startup PC** — show whether the PC is online and, where available, system information.
- **Startup PlayStation** — show PlayStation availability/status where supported.
- **Ding Dong Coffee** — a quick coffee-related button or automation.
- **Weather** — current conditions and forecast.
- **Radar** — precipitation/weather radar for Belgium.
- **Aircraft Status** — show aircraft selected by the user in FlightRadar24, where a supported integration or data source makes this possible. Do not hard-code example aircraft as live data.
- **Flight Ops** — show the user's actual calendar events and upcoming appointments.
- **Lights & Shades** — controls for lights, brightness where supported, and roller blinds/curtains where supported.
- **System Monitor** — Home Assistant/server/network status and available metrics.
- **Current Mission / Projects** — personal goals and active projects.
- **Quick Status** — concise status indicators for connected systems.

## Design direction

- Dark, premium aviation/cockpit look.
- Black/navy surfaces with restrained gold, blue, and green status accents.
- Clear information hierarchy suitable for a fixed tablet.
- Readable at a glance; avoid overcrowding the interface.
- Responsive layout that can be tested on a computer before tablet hardware is purchased.
- Use real Home Assistant entities and integrations for live values; use clearly labelled placeholders during development.

## Planned technology

- Home Assistant and Lovelace dashboards.
- HACS custom cards where useful (for example Mushroom, Button Card, and Card Mod).
- YAML for dashboard and automation configuration.
- ESPHome later if physical buttons or sensors are needed.
- Voice control later, after the dashboard and core integrations work reliably.

## Development phases

1. **Learn and prepare:** Git/GitHub basics, YAML, Home Assistant concepts, entities, helpers, and dashboards.
2. **Prototype the UI:** create the dashboard layout using placeholder entities and test it on a desktop browser.
3. **Connect integrations:** add weather, calendar, PC/PlayStation status, radar, and FlightRadar-related data as supported.
4. **Smart-home controls:** add lights and roller blinds using the actual entities available in the home.
5. **Tablet experience:** optimize the layout for kiosk/full-screen use and test touch targets.
6. **Voice and hardware:** only after the software prototype works, evaluate tablet, microphone, speaker, mounting, and optional ESPHome hardware.

## Important implementation notes

- Entity IDs in examples are placeholders until the actual Home Assistant entities are known.
- FlightRadar aircraft selection depends on the available integration/API and its capabilities; verify before promising live selected-aircraft data.
- Do not commit passwords, access tokens, API keys, personal calendar exports, Home Assistant backups, or other private data to GitHub.
- Keep secrets in local configuration or a supported secret store, and exclude them from version control.
- Start with a private repository if the project later needs to contain real configuration or household details.

## Current next steps

- [ ] Confirm the local project folder is connected to this GitHub repository.
- [ ] Add the latest dashboard mockup to the repository under `docs/images/` when committing files locally.
- [ ] Create a first Lovelace prototype with placeholder entities.
- [ ] Inventory the actual Home Assistant entities before wiring up controls.
- [ ] Keep hardware purchases on hold while learning the software.
