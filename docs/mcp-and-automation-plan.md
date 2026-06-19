# MCP and Automation Plan

This project should support MCP-style tools and scheduled automation, but automation must be staged behind safety and review controls.

## Principle

Automation may collect metadata, check endpoints, create receipts, and build draft metrics. Automation must not publish public-facing egress without review.

## Tool groups

### Source Discovery Tools

- `discover_sources`
- `check_source_endpoint`
- `diff_source_catalogue`
- `classify_source_type`
- `create_source_receipt`

Purpose: find and verify sources before ingestion.

### Ingress Tools

- `ingest_metadata`
- `ingest_open_dataset_snapshot`
- `ingest_gtfs_realtime_status`
- `ingest_rss_metadata`
- `create_claim_from_source`
- `create_record_from_claim_cluster`

Purpose: create source, claim, receipt, and draft record objects. Default mode should be metadata-only.

### Analysis Tools

- `link_duplicate_records`
- `detect_conflicts`
- `build_time_window_rollup`
- `build_neighbourhood_rollup`
- `build_source_quality_report`
- `build_structural_conditions_profile`
- `detect_missing_data`

Purpose: turn reviewed records into metrics, trends, gaps, and evidence trails.

### Egress Tools

- `generate_seed_draft`
- `generate_dashboard_card`
- `generate_neighbourhood_brief`
- `generate_civic_packet`
- `generate_timeline_entry`

Purpose: produce reviewable outputs from linked clusters, not unsupported single inputs.

### Safety and Security Tools

- `scan_private_identifiers`
- `generalize_sensitive_location`
- `check_rights_status`
- `check_public_display_status`
- `check_live_emergency_risk`
- `check_neighbourhood_stigma_risk`
- `create_ibal_review_report`

Purpose: block unsafe storage or public display.

## Automation cadence

### Hourly

- Check source endpoint health.
- Pull allowed realtime metadata, such as transit status where terms allow it.
- Build source-health receipts.
- Flag endpoint changes or failures.

### Daily

- Check City releases, service alerts, public notices, fire releases, source catalogue updates, and selected public record feeds.
- Create metadata-only receipts and draft claims.
- Build daily city pulse draft.

### Weekly

- Build neighbourhood and citywide briefs.
- Run duplicate linking and conflict detection.
- Generate source-quality notes.
- Draft Seeds candidates.

### Monthly

- Build neighbourhood rollups.
- Build structural condition summaries.
- Review source registry for stale, retired, missing, and replaced sources.
- Generate dashboard cards.

### Quarterly

- Review council, budget, planning, infrastructure, and policy clusters.
- Generate civic packets and research questions.

### Yearly

- Rebuild yearly dashboard views.
- Archive source registry state.
- Refresh long-term baseline datasets where updates exist.
- Produce annual civic-memory summary.

## API surface for a future app

Proposed read-only endpoints:

```txt
GET /api/v1/sources
GET /api/v1/sources/{source_id}
GET /api/v1/endpoints
GET /api/v1/records
GET /api/v1/records/{record_id}
GET /api/v1/claims/{claim_id}
GET /api/v1/receipts/{receipt_id}
GET /api/v1/metrics?window=daily&geography=citywide
GET /api/v1/rollups?window=monthly&bin=14
GET /api/v1/dashboard/cards
GET /api/v1/seeds
GET /api/v1/source-quality
```

Proposed protected internal endpoints:

```txt
POST /internal/ingress/source-check
POST /internal/ingress/metadata
POST /internal/analysis/rollup
POST /internal/egress/seed-draft
POST /internal/ibal/review
```

## Write safety

All write actions should default to:

```txt
metadata_only
review_required
no_public_egress
no_private_person_data
no_sensitive_exact_location
no_raw_copyright_content
```

## MCP server boundary

The MCP server should not own truth. It should perform actions against the repo and app database through validated schemas, produce receipts, and return reviewable diffs.

The repo remains the durable public memory. The dashboard app remains derived egress.
