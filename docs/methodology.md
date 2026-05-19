# Methodology

## Data Sources

- **OCHA COD-AB Afghanistan** (CC BY-IGO) — Province and district names (English + Dari/Pashto) with P-codes
- **onaio/lotfa-data** — Province and district centroid coordinates from GeoJSON point layers
- **Afghanistan postal code dataset** — 1,408 postal zones matched to districts by name and proximity
- **OpenStreetMap Nominatim** — Fallback geocoding for 3 districts missing from lotfa-data

## Processing

1. Province and district records from OCHA COD-AB XLSX gazetteer
2. Coordinates merged from lotfa-data GeoJSON points (34 provinces + 399 districts)
3. Remaining 3 district coordinates from Nominatim geocoding
4. Postal codes matched by: exact name (57%), fuzzy name (4%), lat/lon proximity (39%)
5. Multi-format export: JSON, NDJSON, CSV

## Accuracy

- Coordinates: 100% at all levels
- Postal codes: 100% at district level (matched from 1,408 postal zone polygons)
- Build script is idempotent: same input always produces same output