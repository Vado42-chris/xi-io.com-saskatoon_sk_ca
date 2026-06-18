# Data Policy

This repository is a public civic-memory capsule. Its data policy is designed around public benefit, provenance, inspectability, privacy, and rights-aware preservation.

## Preservation principles

1. Preserve metadata before content.
2. Preserve provenance before interpretation.
3. Preserve claims separately from conclusions.
4. Preserve revisions rather than overwriting history.
5. Generalize sensitive geography before public display.
6. Store only what can be lawfully and ethically stored in a public repository.

## Allowed data classes

The repository may store:

- Public open-data records and derived snapshots where licence terms allow reuse.
- Source registry entries.
- Archive references and finding-aid references.
- Metadata for news, books, photos, maps, videos, and social posts.
- Extracted civic claims, with source references and receipts.
- Historical timeline entries with source links.
- Place, neighbourhood, ward, and organization records.
- Derived analysis such as weekly summaries, dashboard cards, and trend records.
- Public-safe summaries created from reviewed record clusters.

## Restricted data classes

The repository must not store:

- Private personal contact information.
- Exact private residential addresses for sensitive events.
- Licence plates, personal phone numbers, private emails, or private social handles.
- Live tactical emergency information.
- Unverified accusations about private people.
- Full copyrighted articles, books, photographs, videos, or archive scans unless licence and rights status explicitly allow public redistribution.
- Raw social media dumps.
- Personal medical, family, child, victim, or witness details beyond what is necessary and already safely public.

## Append-aware model

Records should be treated as append-aware. A later correction or update creates a new receipt or revision. It should not silently replace the original observation.

## Public display model

Every record needs a `public_display_status` value:

- `public_safe`
- `public_aggregate_only`
- `public_metadata_only`
- `review_required`
- `blocked`

A record may be preserved for audit while being blocked from public-facing dashboards or articles.
