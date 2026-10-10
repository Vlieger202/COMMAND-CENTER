# Live aviation and Antwerp weather integration plan

This plan extends the Captain Waypoint dashboard without pretending demo values are live data.

## 1. Flightradar24 live aircraft tracking

The dashboard can show a selected aircraft, flight number/callsign, aircraft type, altitude, speed, heading and position if the chosen data source provides those fields.

**Recommended path**
- First decide whether to use the official Flightradar24 API or an existing supported Home Assistant integration.
- The official Flightradar24 API is a separate product from the normal website/mobile subscription and requires its own API subscription and credits.
- Keep any API token on a trusted backend or Home Assistant secret store. Never put it in `index.html`, browser JavaScript, GitHub Pages files, or a public repository.
- Fetch data on the server side and expose only the fields needed by the dashboard.
- Add a map and selected-flight details only after confirming access and the allowed usage terms.

Official references:
- API FAQ: https://fr24api.flightradar24.com/docs/faq
- API authentication: https://fr24api.flightradar24.com/docs/authentication
- API endpoint documentation: https://fr24api.flightradar24.com/docs/endpoints

## 2. Live weather above Antwerp

**Preferred first step: Home Assistant weather integration.**
- Set the weather location to Antwerp, Belgium.
- Use the resulting weather entity for temperature, conditions, wind, humidity and supported forecasts.
- For radar/precipitation, use a separate supported radar map or weather provider; a standard weather entity does not necessarily provide a radar image.
- If the dashboard remains a static GitHub Pages site, it cannot securely store private API keys. Use Home Assistant or a small trusted backend to access protected APIs.

Home Assistant weather documentation: https://www.home-assistant.io/integrations/weather

Alternative: OpenWeather provides current conditions and forecasts by coordinates, but API keys must be kept out of public frontend code:
- Current weather: https://openweathermap.org/api/current
- API overview: https://openweathermap.org/api

## 3. Architecture

For secure live integrations, the intended data flow is:

`Provider / Home Assistant → trusted server-side integration → dashboard`

Do not call a private API directly from public browser JavaScript if that exposes a token. Do not commit credentials, tokens, private calendar data, or Home Assistant configuration containing secrets.

## 4. Build order

1. Decide where the dashboard will run: GitHub Pages alone, or Home Assistant/local network as the live dashboard.
2. Configure weather for Antwerp and verify the real Home Assistant entity.
3. Choose the Flightradar24 data route and check cost/usage terms before enabling live tracking.
4. Add server-side secret handling and test the data flow.
5. Replace the placeholder panels only when real data is available.

**Current status:** planning only. The existing dashboard panels remain demo/placeholder panels until real integrations are configured and verified.
