# Source Policy

This project separates source metadata, claims, records, receipts, and conclusions.

## Source types

Supported source types include:

- `official_open_data`
- `official_release`
- `official_archive`
- `public_record`
- `statistical_table`
- `local_media`
- `community_organization`
- `resident_report`
- `oral_history`
- `asset_reference`
- `research_note`

## Source confidence

Every source should be assigned a source confidence value:

- `official_primary`
- `official_secondary`
- `licensed_dataset`
- `media_reported`
- `community_reported`
- `firsthand_with_consent`
- `unverified_claim`
- `research_target`
- `unknown`

Source confidence is not the same as truth. It describes source posture and review needs.

## Claim handling

A claim is a statement made by a source. Claims should be stored separately from normalized records so that conflict, correction, and uncertainty can be preserved.

A single record may link to many claims. A single source may make many claims. Later updates should be linked as revisions, not replacements.

## Citation handling

For materials that should not be copied, store:

- Source title
- Source author or publisher when available
- Source URL or archive reference
- Publication or creation date
- Access date
- Rights status
- Short public-safe summary
- Extracted claims
- Hash or receipt metadata where possible

## Source lifecycle

Each source registry entry should track:

- `source_status`: active, inactive, retired, missing, replaced, research_target
- `update_cadence`: realtime, daily, weekly, monthly, annual, irregular, unknown
- `harvest_mode`: manual, rss, api, open_data_download, archive_reference, metadata_only
- `rights_notes`
- `review_notes`
