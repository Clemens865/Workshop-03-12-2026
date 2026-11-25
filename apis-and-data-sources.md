# Weather, Climate & Environmental APIs

Curated from the Weather-App project's API & Data Catalog (verified, with licensing notes). Full catalog has 100+ entries across forecast, radar/nowcast, warnings, air quality, pollen and marine — this is the "quick picks" tier.

## Core forecast

| API | Link | Notes |
|---|---|---|
| Apple WeatherKit | https://developer.apple.com/weatherkit/ | Native Swift, 500k calls/month free, global forecast + alerts, requires Apple attribution |
| Open-Meteo Forecast API | https://open-meteo.com/en/docs | One API, selectable models (ICON, GFS, IFS, AROME, etc.), CC BY 4.0, AGPLv3 self-hostable, free tier non-commercial only |
| Bright Sky | https://brightsky.dev/ | Ready-made JSON wrapper over DWD (German weather service) MOSMIX/observations/radar/warnings, open source, self-hostable |
| ECMWF Open Data (IFS / AIFS) | https://www.ecmwf.int/en/forecasts/datasets/open-data | Free, CC BY 4.0 global forecast backbone incl. ensembles |
| MET Norway Locationforecast 2.0 | https://api.met.no/weatherapi/locationforecast/2.0/documentation | Free, commercial-OK global fallback (needs caching proxy + User-Agent header) |

## Radar, nowcast & warnings

| API | Link | Notes |
|---|---|---|
| DWD Radar Composites (RV/WN/RADOLAN) | https://opendata.dwd.de/weather/radar/composite/ | 1km/5-min radar + 2h nowcast for Germany, CC BY 4.0 |
| Rainbow.ai Nowcast & Tiles API | https://developer.rainbow.ai/ | Global 1km/1min nowcast up to 4h, from $25/mo |
| MeteoAlarm Feeds (EUMETNET) | https://feeds.meteoalarm.org/ | Europe-wide official weather warnings per country, JSON/Atom |
| DWD Pollenflug-Gefahrenindex | https://opendata.dwd.de/climate_environment/health/alerts/s31fg.json | Official German pollen index, 8 species, CC BY 4.0 |

## Air quality & marine

| API | Link | Notes |
|---|---|---|
| Open-Meteo Air Quality API | https://open-meteo.com/en/docs/air-quality-api | CAMS-based European/US AQI, pollutants, dust, pollen in one call |
| BSH Water Level Forecast API | https://gdi.bsh.de/ldproxy/rest/services/WaterLevelForecast | Official 7-day water level/storm surge, 136 North Sea/Baltic gauges, no key |

## AI weather models (research-grade)

| Model | Link |
|---|---|
| Google DeepMind GraphCast / GenCast | — (see Google WeatherNext) |
| Google WeatherNext (AI ensemble forecasts) | https://developers.google.com/weathernext |
| ECMWF AIFS model weights (Hugging Face) | — |

*Source: `Software-Projects/Weather-App/docs/api-catalog.md` ("Quick picks (MVP)" section) and `docs/RESEARCH.md`.*
