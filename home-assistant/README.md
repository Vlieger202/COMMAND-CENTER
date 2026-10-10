# Home Assistant — Captain Waypoint Command Center

This folder stores starter configuration and dashboard examples for the COMMAND-CENTER project.

## Files

- `examples/waypoint-dashboard-cards.yaml` — example Lovelace cards for PC, PlayStation, coffee, weather, radar, aircraft placeholder, mission, and system monitoring.
- `examples/waypoint-helpers.yaml` — example mission helper and coffee notification script.
- `themes/waypoint202.yaml` — starter dark aviation-inspired theme.

## Before using these examples

1. Back up your Home Assistant configuration.
2. Confirm the entity IDs in Developer Tools → States.
3. Install any required custom cards through HACS and register their frontend resources.
4. Add cards individually to a test dashboard first.
5. Validate configuration before restarting Home Assistant.
6. Keep credentials, tokens, private calendar data, and backups out of GitHub.

The FlightRadar panel is intentionally a placeholder until a supported integration and its actual entities are confirmed. Lights and roller-blind controls should be added only after the corresponding real entities are identified.
