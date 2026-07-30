# Czechia Administrative Divisions / Česko



## Overview

| Item | Details |
|------|---------|
| Region | 14 |
| Locality | 303 |
| Coordinates | ✅ Included (all levels) |
| Formats | JSON, NDJSON, CSV |
| License | CC-BY-4.0 |
| Last Updated | 2026-07-30 |
| Website | [openadmindata.org/cz](https://openadmindata.org/cz/) |
| API | [openadmindata.org/api/cz](https://openadmindata.org/api/cz/) |

## Browse by Region

| # | Region | Localitys | Link |
|---|----|----|------|
| 1 | Jihočeský (South Bohemian) | 29 | [Browse](divisions/south-bohemian-cz01/) |
| 2 | Zlínský (Zlín) | 10 | [Browse](divisions/zlin-cz02/) |
| 3 | Jihomoravský (South Moravian) | 20 | [Browse](divisions/south-moravian-cz03/) |
| 4 | Vysočina (Vysocina) | 16 | [Browse](divisions/vysocina-cz04/) |
| 5 | Plzeňský (Plzeň) | 30 | [Browse](divisions/plzen-cz05/) |
| 6 | Hlavní město Praha (Prague) | 1 | [Browse](divisions/prague-cz06/) |
| 7 | Pardubický (Pardubice) | 15 | [Browse](divisions/pardubice-cz07/) |
| 8 | Karlovarský (Karlovy Vary) | 8 | [Browse](divisions/karlovy-vary-cz08/) |
| 9 | Moravskoslezský (Moravian-Silesian) | 34 | [Browse](divisions/moravian-silesian-cz09/) |
| 10 | Olomoucký (Olomouc) | 31 | [Browse](divisions/olomouc-cz10/) |
| 11 | Středočeský (Central Bohemian) | 54 | [Browse](divisions/central-bohemian-cz11/) |
| 12 | Královéhradecký (Hradec Králové) | 16 | [Browse](divisions/hradec-kralove-cz12/) |
| 13 | Ústecký (Ústí nad Labem) | 24 | [Browse](divisions/usti-nad-labem-cz13/) |
| 14 | Liberecký (Liberec) | 15 | [Browse](divisions/liberec-cz14/) |

## Data Files

| File | Format | Description |
|------|--------|-------------|
| [all-region.json](data/all-region.json) | JSON | All 14 region records |
| [all-locality.json](data/all-locality.json) | JSON | All 303 locality records |
| [all-flat.json](data/all-flat.json) | JSON | Levels 1-1 flat array |
| [all-flat.ndjson](data/all-flat.ndjson) | NDJSON | Streaming format |
| [all-flat.csv](data/all-flat.csv) | CSV | Spreadsheet format |
| [hierarchy.json](data/hierarchy.json) | JSON | Nested tree |
| [schema.json](data/schema.json) | JSON Schema | Data schema |

## Quick Start

### Python

```python
import json

with open("data/all-region.json", "r", encoding="utf-8") as f:
    data = json.load(f)

for r in data:
    print(f"{r['name']['local']} ({r['name']['en']}) — {r['children_count']['locality']} localitys")
```

### JavaScript

```javascript
import { readFileSync } from "fs";

const data = JSON.parse(readFileSync("data/all-region.json", "utf-8"));
console.log(`Total: ${data.length} regions`);
```

## Schema

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | Unique identifier |
| `level` | integer | 1=region, 2=locality |
| `level_name` | object | Level label (local + English) |
| `name.local` | string | Name in local script |
| `name.en` | string | English name |
| `name.slug` | string | URL-safe slug |
| `parent` | object/null | Parent division reference |
| `ancestors` | array | Full ancestor chain |
| `children_count` | object | Count of children per level |
| `zip_codes` | array | Postal codes (where available) |
| `geo.lat` | string | Latitude (WGS84) |
| `geo.lon` | string | Longitude (WGS84) |

Full schema: [data/schema.json](data/schema.json)

## Hierarchy Browse

```
divisions/{region-slug}/
```

Localitys are listed inline in each region's README.

## AI Integration

- [llms.txt](docs/llms.txt) — Quick reference for AI agents
- [llms-full.txt](docs/llms-full.txt) — Summary with per-region links
- [Per-region data](docs/llms-full/) — Full data by region

## Citation

```
Czechia Administrative Divisions Dataset (CC-BY-4.0)
URL: https://github.com/open-admin-data/czechia-administrative-divisions
```

See [CITATION.cff](CITATION.cff) for machine-readable citation.

## License

- **Data**: [CC-BY-4.0](LICENSE)

## Related

- [Open Admin Data](https://openadmindata.org) — Browse, search and explore administrative divisions for every country
- [open-admin-data](https://github.com/open-admin-data) — GitHub organization with all country repos
- [ListBase](https://www.listbase.org) — Structured reference data for every country
