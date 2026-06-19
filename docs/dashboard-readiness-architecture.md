# Dashboard Readiness Architecture

This document defines how the Saskatoon civic-memory capsule can support hourly, daily, weekly, monthly, yearly, and historical dashboard views without collapsing into a scraper dump or unsafe public map.

## Core rule

The dashboard is egress, not storage.

Raw or staged source material enters through ingress. Claims, records, receipts, metrics, and rollups are reviewed before any dashboard output is produced.

## Time windows

Supported dashboard windows:

- `realtime`: current status feeds where source terms allow it, such as transit alerts
- `hourly`: short interval operational summaries
- `daily`: day-level civic activity and source changes
- `weekly`: useful civic brief cadence
- `monthly`: neighbourhood and policy trend cadence
- `quarterly`: planning and budget review cadence
- `yearly`: public memory and longitudinal trend cadence
- `multi_year`: history, demographic, infrastructure, and policy change
- `point_in_time`: archive, census, baseline, and one-time records

## Data layers

1. Source Discovery Layer
   - Finds sources and endpoints.
   - Tracks active, retired, missing, replaced, and blocked sources.
   - Creates endpoint records before ingestion.

2. Ingress Layer
   - Pulls metadata, feeds, API data, or public-safe snapshots according to source policy.
   - Creates receipts for every observation.
   - Does not publish.

3. Claim Layer
   - Extracts source claims.
   - Keeps claims separate from normalized records.
   - Allows conflicts and corrections to be preserved.

4. Record Layer
   - Normalizes claims into civic-memory records.
   - Links records to bins, places, time windows, sources, and receipts.

5. Metric Layer
   - Converts reviewed records into dashboard metrics.
   - Preserves denominator, method, granularity, confidence, and rights metadata.

6. Rollup Layer
   - Aggregates metrics by time window, geography, bin, domain pack, and source type.
   - Produces hourly, daily, weekly, monthly, yearly, and multi-year views.

7. Egress Layer
   - Produces dashboard cards, Seeds drafts, timelines, briefs, civic packets, and research notes.
   - Uses only reviewed records and public-safe metrics.

## Source cadence classes

- `realtime`: GTFS realtime, service status, active alerts
- `hourly`: transit status summaries, weather/status checks, source-health checks
- `daily`: city releases, fire releases, public notices, source diffs
- `weekly`: civic briefs, neighbourhood summaries, service-gap observations
- `monthly`: dashboard rollups, source quality reports, structural condition updates
- `quarterly`: council/budget/planning reviews
- `yearly`: census-style baselines, historical timelines, annual reports
- `irregular`: archives, media references, oral history, heritage records

## Example dashboard views

### City Pulse

Current and recent civic status: transit alerts, service alerts, road restrictions, weather hazards, public notices, and major source updates.

### Neighbourhood Memory

Monthly and yearly record clusters by neighbourhood: history, services, safety, culture, infrastructure, and civic decisions.

### Structural Conditions

Baseline pressure indicators such as food insecurity, poverty, housing, accessibility, transit access, cost of living, and service availability.

### Safety and Resilience

Aggregate-only indicators for emergency response, road safety, fire, public health, weather, and social harm. Avoid exact private addresses and danger scoring.

### Source Quality

Shows source freshness, missing datasets, retired datasets, rights status, stale endpoints, correction counts, and confidence mix.

## Storage to app path

The repo remains the public, auditable civic-memory capsule.

A future dashboard app may generate an app database from these records, likely using:

- JSON and JSONL as canonical interchange
- GeoJSON for public-safe geography
- DuckDB or SQLite for local analysis builds
- PostgreSQL/PostGIS for production spatial dashboards
- Static JSON rollups for low-cost public hosting

The app database should be reproducible from repo records, receipts, and snapshots.

## Public safety constraints

Do not display:

- exact sensitive private locations
- personal identifiers for vulnerable people
- live tactical emergency details
- unsupported accusations
- raw resident reports
- copied copyrighted material
- single-score neighbourhood danger rankings

Prefer:

- aggregates
- trends
- source confidence
- uncertainty notes
- context indicators
- structural causes
- service gaps
- time comparisons
