# Afghanistan Administrative Divisions / افغانستان

Open dataset of Afghanistan's administrative hierarchy — 34 provinces and 401 districts. This repository provides structured, bilingual (Dari/Pashto + English) reference data with geographic coordinates and postal codes at every level. Designed for developers, researchers, government agencies, and AI agents.

Licensed under CC-BY-4.0. Browse the hierarchy through GitHub's folder navigation, download aggregate files in JSON/CSV/NDJSON, or integrate directly via raw URLs.

## Overview

| Item | Details |
|------|---------|
| Province | 34 |
| District | 401 |
| Coordinates | ✅ Included (all levels) |
| Postal Codes | ✅ Included (district level) |
| Formats | JSON, NDJSON, CSV |
| License | CC-BY-4.0 |
| Last Updated | 2026-05-19 |

## Browse by Province

| # | Province | Districts | Link |
|---|----|----|------|
| 1 | بدخشان (Badakhshan) | 28 | [Browse](divisions/badakhshan-af17/) |
| 2 | سمنگان (Samangan) | 8 | [Browse](divisions/samangan-af20/) |
| 3 | لوگر (Logar) | 7 | [Browse](divisions/logar-af05/) |
| 4 | پکتیکا (Paktika) | 19 | [Browse](divisions/paktika-af12/) |
| 5 | سرپل (Sar-e-Pul) | 7 | [Browse](divisions/sar-e-pul-af22/) |
| 6 | پکتیا (Paktya) | 11 | [Browse](divisions/paktya-af13/) |
| 7 | نورستان (Nuristan) | 8 | [Browse](divisions/nuristan-af16/) |
| 8 | بلخ (Balkh) | 15 | [Browse](divisions/balkh-af21/) |
| 9 | پنجشیر (Panjsher) | 7 | [Browse](divisions/panjsher-af08/) |
| 10 | جوزجان (Jawzjan) | 11 | [Browse](divisions/jawzjan-af28/) |
| 11 | کندهار (Kandahar) | 16 | [Browse](divisions/kandahar-af27/) |
| 12 | دایکندی (Daykundi) | 9 | [Browse](divisions/daykundi-af24/) |
| 13 | ارزگان (Uruzgan) | 7 | [Browse](divisions/uruzgan-af25/) |
| 14 | غور (Ghor) | 10 | [Browse](divisions/ghor-af23/) |
| 15 | فراه (Farah) | 11 | [Browse](divisions/farah-af33/) |
| 16 | پروان (Parwan) | 10 | [Browse](divisions/parwan-af03/) |
| 17 | فاریاب (Faryab) | 14 | [Browse](divisions/faryab-af29/) |
| 18 | کندز (Kunduz) | 7 | [Browse](divisions/kunduz-af19/) |
| 19 | خوست (Khost) | 13 | [Browse](divisions/khost-af14/) |
| 20 | هرات (Hirat) | 16 | [Browse](divisions/hirat-af32/) |
| 21 | کنر ها (Kunar) | 15 | [Browse](divisions/kunar-af15/) |
| 22 | کابل (Kabul) | 15 | [Browse](divisions/kabul-af01/) |
| 23 | هلمند (Hilmand) | 13 | [Browse](divisions/hilmand-af30/) |
| 24 | غزنی (Ghazni) | 19 | [Browse](divisions/ghazni-af11/) |
| 25 | میدان وردک (Maidan Wardak) | 9 | [Browse](divisions/maidan-wardak-af04/) |
| 26 | کاپیسا (Kapisa) | 7 | [Browse](divisions/kapisa-af02/) |
| 27 | ننگرهار (Nangarhar) | 22 | [Browse](divisions/nangarhar-af06/) |
| 28 | زابل (Zabul) | 11 | [Browse](divisions/zabul-af26/) |
| 29 | تخار (Takhar) | 17 | [Browse](divisions/takhar-af18/) |
| 30 | نیمروز (Nimroz) | 5 | [Browse](divisions/nimroz-af34/) |
| 31 | لغمان (Laghman) | 5 | [Browse](divisions/laghman-af07/) |
| 32 | بغلان (Baghlan) | 15 | [Browse](divisions/baghlan-af09/) |
| 33 | بادغیس (Badghis) | 7 | [Browse](divisions/badghis-af31/) |
| 34 | بامیان (Bamyan) | 7 | [Browse](divisions/bamyan-af10/) |

## Data Files

| File | Format | Description |
|------|--------|-------------|
| [all-province.json](data/all-province.json) | JSON | All 34 province records |
| [all-district.json](data/all-district.json) | JSON | All 401 district records |
| [all-flat.json](data/all-flat.json) | JSON | Levels 1-1 flat array |
| [all-flat.ndjson](data/all-flat.ndjson) | NDJSON | Streaming format |
| [all-flat.csv](data/all-flat.csv) | CSV | Spreadsheet format |
| [hierarchy.json](data/hierarchy.json) | JSON | Nested tree |
| [schema.json](data/schema.json) | JSON Schema | Data schema |

## Quick Start

### Python

```python
import json

with open("data/all-province.json", "r", encoding="utf-8") as f:
    data = json.load(f)

for r in data:
    print(f"{r['name']['local']} ({r['name']['en']}) — {r['children_count']['district']} districts")
```

### JavaScript

```javascript
import { readFileSync } from "fs";

const data = JSON.parse(readFileSync("data/all-province.json", "utf-8"));
console.log(`Total: ${data.length} provinces`);
```

## Schema

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | Unique identifier |
| `level` | integer | 1=province, 2=district |
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
divisions/{province-slug}/
```

Districts are listed inline in each province's README.

## AI Integration

- [llms.txt](docs/llms.txt) — Quick reference for AI agents
- [llms-full.txt](docs/llms-full.txt) — Summary with per-province links
- [Per-province data](docs/llms-full/) — Full data by province

## Citation

```
Afghanistan Administrative Divisions Dataset (CC-BY-4.0)
URL: https://github.com/open-admin-data/afghanistan-administrative-divisions
```

See [CITATION.cff](CITATION.cff) for machine-readable citation.

## License

- **Data**: [CC-BY-4.0](LICENSE)

## Related

- [ListBase](https://www.listbase.org) — Structured reference data for every country
- [open-admin-data](https://github.com/open-admin-data) — Open administrative data for ASEAN countries
- [thailand-administrative-divisions](https://github.com/open-admin-data/thailand-administrative-divisions) — Thailand dataset
