# SolarEV Cities

A visual communication tool for exploring Australia’s postcode-level solar, EV, and battery transition.

SolarEV Cities layers postcode-level datasets onto one interactive map — EV registrations, rooftop PV installations, PV capacity, battery installations, battery capacity, SolarEV readiness, missing-link typologies, and Australia’s top 50 cities. By making these datasets visible together, it helps researchers, planners, policymakers, and the public understand where the ingredients for SolarEV Cities are already emerging, where gaps remain, and why V2H/V2G integration matters.

Live map: https://tilly4064.github.io/solarEVcity/

Best viewed on desktop. Mobile is functional but cramped because the map includes a sidebar, popups, legends, and story panels.

---

## What it does

SolarEV Cities brings several postcode-level datasets onto one map so users can see where rooftop solar, electric vehicles, and batteries overlap spatially.

The map is designed around the **SolarEV Cities** concept: urban energy and mobility systems where rooftop PV, EV batteries, household batteries, and future vehicle-to-home and vehicle-to-grid technologies are integrated rather than treated as separate systems.

### Map layers

Toggle on/off from the sidebar. One postcode choropleth layer is shown at a time, while the city overlay can be combined with any layer.

| Layer | What it shows |
|---|---|
| **EV registrations** | Battery-electric vehicle registrations by postcode. |
| **PV installations** | Total rooftop solar PV installation counts by postcode. |
| **PV capacity** | Installed PV capacity by postcode, shown with a light-blue to dark-blue scale. |
| **Battery installations** | Battery installation counts by postcode. |
| **Battery capacity** | Installed battery capacity by postcode, shown with a light-blue to dark-blue scale. |
| **SolarEV readiness score** | Exploratory percentile-based score combining EV, PV, and battery uptake. |
| **Missing-link typology** | Categorical layer identifying areas such as solar-led, EV-led, SolarEV emerging, Solar + battery ready, and SolarEV candidate postcodes. |
| **Top 50 cities** | Light-purple proportional circles showing Australia’s largest cities and towns by population. This overlay can be switched on together with any postcode layer. |

### Tools and interface

- **Homepage / landing screen** — introduces the SolarEV Cities concept before opening the map.
- **About the concept** — explains why solar, EVs, batteries, and V2H/V2G need to be understood as one integrated system.
- **Layer sidebar** — switch between postcode-level indicators.
- **Draggable postcode popup** — click any postcode to inspect local values.
- **City popup** — click a city marker to inspect population and rank information.
- **Numeric legends** — layer-specific legends with approximate value ranges.
- **Collapsible interface** — map-first layout with floating panels.

---

## Data sources

Most datasets are pre-processed and bundled into the webmap for static deployment.

| Layer / variable | Source |
|---|---|
| Postcode boundaries | ABS Australian Statistical Geography Standard, Postal Areas 2021 |
| EV registrations | EV registration dataset, January 2025 |
| PV installations | Small-scale solar installation postcode data |
| PV capacity | Small-scale solar capacity postcode data |
| Battery installations | Small-scale battery installation postcode data |
| Battery capacity | Small-scale battery capacity postcode data |
| PV density and rooftop potential fields | Postcode-level solar dataset used for PV density, estimated houses, rooftop PV potential, and annual rooftop PV energy potential |
| Top 50 cities | .id / ABS Significant Urban Area population ranking |
| Map tiles | CARTO Positron / OpenStreetMap contributors |

---

## Stack

- **MapLibre GL JS** for map rendering
- **Vanilla JavaScript** — no framework, no build step, no npm dependencies
- **Static HTML deployment**
- Embedded or bundled GeoJSON for postcode and city data
- Client-side layer switching and popups

The app is designed to run as a static webmap on GitHub Pages, Netlify, Cloudflare Pages, or any basic static host.

---

## Interpretation

SolarEV Cities does **not** show that postcodes are already fully integrated SolarEV systems.

Instead, the map highlights where the required ingredients are present or missing:

- rooftop PV;
- EV uptake;
- household battery uptake;
- battery capacity;
- urban concentration;
- potential for future V2H/V2G integration.

A true SolarEV City also requires:

- V2H/V2G-compatible EVs;
- bidirectional home chargers;
- smart charging and energy management systems;
- suitable tariffs and market rules;
- distribution grid readiness;
- policy coordination across energy, transport, housing, and planning;
- equitable access for renters, apartment residents, and lower-income households.

---

## Limitations

- The map uses postcode-level aggregation, so it does not show household-level behaviour.
- EV, PV, and battery counts are stock indicators, not measured energy flows.
- PV capacity and battery capacity do not indicate when energy is generated, stored, discharged, or consumed.
- The readiness score is an exploratory communication indicator, not a formal model.
- The missing-link typology simplifies complex energy and transport systems into broad categories.
- The map does not measure actual self-sufficiency, self-consumption, V2H operation, or V2G export.
- City points are reference overlays and should not be interpreted as official SolarEV City boundaries.
- Some postcode areas contain large commercial or power-station PV capacity, which can affect capacity-based interpretation.
- Data availability and reporting periods differ across datasets.

This webmap is a research communication and visualisation tool, not a definitive energy-system model.

---

## Architecture notes

- Postcode polygons are loaded as GeoJSON.
- Choropleth layers are controlled through MapLibre style expressions.
- One main postcode choropleth is visible at a time to avoid layers hiding each other.
- The Top 50 cities layer is an independent overlay and can be combined with any postcode layer.
- Popups are custom draggable panels for better usability on dense postcode information.
- The readiness score uses percentile-normalised indicators to reduce distortion from skewed raw values.
- The typology layer classifies postcodes by relative EV, PV, and battery uptake patterns.

---

## Licence

Code released under the MIT licence unless otherwise specified. Data remains owned by its respective publishers. Check each source dataset for its own licence and reuse conditions.

## Acknowledgements

Built with publicly available postcode, solar, battery, EV registration, and city population data. Map rendering by MapLibre GL JS. Basemap tiles use CARTO / OpenStreetMap contributors.
