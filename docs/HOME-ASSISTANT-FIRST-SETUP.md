# First setup: Captain Waypoint in Home Assistant

We will build this in small steps. Do not paste example entity IDs into a live setup without checking them first.

## Goal for phase 1

1. Display weather for Antwerp, Belgium.
2. Display aircraft detected around Antwerp and Brussels Airport.
3. Keep API keys and credentials out of GitHub.

## Step 1 — confirm your Home Assistant setup

Before we change configuration, confirm that you can open your Home Assistant dashboard and reach:
- Settings → Devices & services
- Settings → Dashboards
- Developer Tools → States

Do not share passwords, access tokens, or screenshots containing private details.

## Step 2 — add aircraft tracking

A community integration is available:
https://github.com/AlexandrErohin/home-assistant-flightradar24

Its documentation describes installation through HACS, configuration through Settings → Devices & services, a monitoring latitude/longitude, radius and altitude filters, and an aircraft map/card. Review its current README and terms before installing; it is a community integration, not an official Home Assistant integration.

High-level steps:
1. Open HACS and search for Flightradar24. If it is not available in the search results, follow the integration's official README for adding its repository.
2. Install the integration and restart Home Assistant if requested.
3. Open Settings → Devices & services → Add integration → search for Flightradar24.
4. Set the monitoring coordinates and radius for the airspace you want to cover. Check the configuration options and request frequency carefully.
5. Wait for the initial data load. It can take a few minutes.
6. Open Developer Tools → States and find the real sensor entity, commonly named similar to `sensor.flightradar24_current_in_area`.
7. Add the aircraft card using `examples/aircraft-tracking-antwerp.yaml`, but replace the example entity ID if yours differs.

Coverage note: Antwerp and Brussels Airport are separated by a significant distance. A single large radius centered between them may include a lot of extra airspace. We should choose the radius and center carefully, and consider separate monitors only if the integration and provider terms support that approach.

Data note: this community integration may retrieve data from Flightradar24's service and may be affected by rate limits, service changes, or provider terms. It is not a guarantee of official API access. If you need a supported commercial data feed, evaluate the official FR24 API separately.

## Step 3 — add Antwerp weather

Home Assistant's weather entity is supplied by a weather provider integration. See:
https://www.home-assistant.io/integrations/weather

1. Go to Settings → Devices & services → Add integration.
2. Choose a weather provider available in your installation.
3. Configure the location as Antwerp, Belgium.
4. Open Developer Tools → States and note the actual weather entity ID.
5. Adapt `examples/weather-antwerp.yaml` to use that entity ID and add the card to your dashboard.

A weather entity may provide current conditions and forecast fields such as temperature, humidity, wind and precipitation probability, depending on the provider. A live precipitation radar often needs a separate radar map/provider.

## Step 4 — protect the project

- Never commit API keys, passwords, session cookies, access tokens or private Home Assistant backups.
- Do not place secrets in the public `index.html` or other GitHub Pages JavaScript.
- Prefer Home Assistant integrations and secret storage for credentials.
- Keep this repository's public files limited to examples without personal information.

## Next checkpoint

Before proceeding to more features, confirm:
- Home Assistant is running and accessible.
- Whether HACS is installed.
- Whether the Flightradar24 integration appears in HACS or has been installed.
- The actual entity ID created for aircraft in the area.
- The actual weather entity ID for Antwerp.

Once those are confirmed, we can adapt the dashboard YAML to your real entities rather than guessing.
