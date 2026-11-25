# Austrian & Viennese Government Data, APIs & Funding Sources

Curated from the City-AI / "Mein W(a)ien" research (API scout reports, 2026). These cover open government data, public APIs, and funding/tender sources for Austria and Vienna — useful for anyone building citizen-facing tools, public-data apps, or researching Austrian funding.

## Core "no API-key needed" endpoint families

| Source | Link | What it offers |
|---|---|---|
| Stadt Wien WFS (GeoServer) | https://data.wien.gv.at/daten/geo | Spatial datasets for ~80% of citizen questions: schools, pharmacies, drinking fountains, playgrounds, pools, etc. No key, GeoJSON, CC BY 4.0 |
| Wiener Linien Realtime API | https://www.wienerlinien.at/ogd_realtime/ | Real-time public-transit departures, disruptions, news. No key since Oct 2019 |
| RIS OGD REST API v2.6 | https://data.bka.gv.at/ris/api/v2.6/ | All Austrian federal & Viennese state laws, regulations, case law. No key, ELI/ECLI citations |
| basemap.at WMTS | — | National map tiles (geoland consortium), all 9 states, 99.985% SLA, CC BY 4.0 |
| VAO — Verkehrsauskunft Österreich | https://verkehrsauskunft.at | Nationwide intermodal transit/car/bike routing, 100 free queries/day |
| oesterreich.gv.at | https://www.oesterreich.gv.at | Central federal citizen portal ("Amtshelfer"), life-situation structured index, CC BY 4.0 |

## Useful public APIs & open datasets

| Source | Link | What it offers |
|---|---|---|
| data.gv.at hub repo API | https://qs.data.gv.at/api/hub/repo/datasets | Replacement for the dead legacy CKAN action API — JSON-LD/DCAT search across all Austrian open datasets |
| Statistik Austria OGD REST | https://data.statistik.gv.at | Keyless per-dataset REST + CSV: population, education, demographics |
| AMS Open Data | https://www.ams.at (Open Data section) | Job postings by occupation/industry, apprenticeships, career profiles — monthly CSV, CC BY 4.0 |
| Parlament AT Open Data Filter API | — | Petitions, citizens' initiatives, written inquiries — single POST-JSON endpoint, CC BY 4.0 |
| OpenFirmenbuch.at | https://www.openfirmenbuch.at | Free company-register lookup, no key, built on official Firmenbuch data |
| eHYD Hydro Data | https://ehyd.gv.at | ~700 live river/water-level gauges, CSV export, CC BY 4.0 |
| Polleninformation.at API | https://www.polleninformation.at/api/forecast/public | 4-day hourly pollen forecast JSON (free key) |
| APG Day-Ahead Prices | https://markt.apg.at/en/transparency/cross-border-exchange/day-ahead-prices/ | Live Austrian electricity spot prices (EXAA + SDAC, 15-min resolution) |
| Kulturpool Search API | — | 1M+ Austrian cultural/heritage objects, no-auth search + OAI-PMH bulk |
| OpenSky Network | https://opensky-network.org | Free live ADS-B flight data, bounding-box queries (e.g. "planes over Vienna") |

## Funding, tenders & grants (Austria / Vienna)

| Source | Link | What it offers |
|---|---|---|
| EU TED API v3 | https://api.ted.europa.eu/v3 | All EU above-threshold tenders incl. Austria, free REST+JSON, eForms SDK |
| FFG RSS feed | https://www.ffg.at/rss.xml | Austrian national R&D funding agency — live calls/news feed |
| Wirtschaftsagentur Wien — current calls | https://wirtschaftsagentur.at/aktuelle-foerderungen-der-wirtschaftsagentur-wien/ | ~20 active Vienna startup/SME/digital/AI funding calls |
| aws (Austria Wirtschaftsservice) | https://www.aws.at | Federal funding: Preseed/Seedfinancing, Deep Tech, AI Mission Austria, Gründungsfonds (VC arm), Garantie (credit guarantees) |
| WWTF (Vienna Science & Technology Fund) | https://www.wwtf.at/funding/ | Vienna-specific research funding calls |
| Förderbericht Stadt Wien (CSV) | https://www.wien.gv.at/spezial/studien/ma5/foerderbericht2024.csv | Every Vienna municipal funding allocation, direct download |
| USP Ausschreibungssuche | https://ausschreibungen.usp.gv.at | Free, national, central public-tender search (no ANKÖ paywall) |
| Wien Vergabeportal | https://wien.gv.at/Vergabeportal/List | Official, free Vienna tender listings, CC BY 4.0 |
| OffeneVergaben.at | https://offenevergaben.at | Civic-tech open-source mirror of Austrian public tenders |
| opentender.eu | https://opentender.eu | EU-wide procurement aggregator with an Austria slice (OCDS, quarterly) |
| CORDIS / OpenAIRE | https://cordis.europa.eu · https://api.openaire.eu | EU Horizon Europe/FP7 project & funding graph, SPARQL + REST, Austrian beneficiaries queryable |

**Key caveat worth keeping in mind:** the commercial Vienna tender aggregator ANKÖ (EUR 450/yr, no public API) mirrors notices that are *all* also available for free via TED, USP Ausschreibungssuche, the official `wien.gv.at/Vergabeportal`, and OffeneVergaben.at — prefer those free routes.

*Source: City-AI project's "Mein W(a)ien" API scout reports (funding/tenders, Wien gaps, AT deep, AT coverage waves), 2026.*
