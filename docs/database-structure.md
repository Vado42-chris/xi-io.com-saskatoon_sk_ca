# Database Structure Start Guide

This project starts as a Git-backed civic-memory database. Git provides public history, reviewability, diffs, and receipts. A proper app database can be generated later from these records.

## Start here

Start with source indexes, not harvested content.

Order of operations:

1. Register sources in `source.registry.json`.
2. Create source receipts for when each source was reviewed.
3. Create claim records only when a source makes a specific claim worth preserving.
4. Create normalized records from one or more claims.
5. Link records to places, time, bins, receipts, and rights status.
6. Allow egress only after Ibal review.

## Storage lanes

Use these lanes:

```txt
source.registry.json      source index
data/receipts/            observation and review receipts
records/                  normalized civic-memory records
data/snapshots/           licensed dataset snapshots only
data/derived/             computed outputs
data/indexes/             generated indexes
analysis/                 notes, trends, conflicts, questions
egress/seeds/             public-safe generated outputs
```

## Recommended file formats

Use JSON for manifests, schemas, taxonomies, and registries.

Use JSONL for append-style record collections once volume grows:

```txt
records/events/2026/06/events-2026-06.jsonl
records/timeline/timeline-1906-1945.jsonl
data/receipts/2026/06/receipts-2026-06.jsonl
data/derived/neighbourhood-monthly-summary.jsonl
```

Use Markdown for human review notes, policies, research notes, and egress drafts.

Use GeoJSON only for public-safe boundaries or generalized place geometry.

## Required metadata

Every durable item should preserve:

- `record_id`, `source_id`, `claim_id`, or `receipt_id`
- `city_id`
- Source name
- Source URL or archive reference
- Access or observation timestamp
- Publication or creation timestamp when known
- Rights status
- Public display status
- Review status
- Confidence level
- Sensitivity level
- Time depth and time confidence
- Place scope and location precision
- Primary bin and secondary bins
- Related records
- Notes about uncertainty or conflict

## Do not start with scraping

The first safe milestone is a curated source registry and a small set of manually created test records. Automated harvesting comes after rights, schemas, validation, and Ibal review rules are working.

## First real database slice

The first usable slice should be:

1. Ten source registry entries.
2. Five place records, such as citywide, river, downtown, one bridge, one neighbourhood.
3. Five timeline entries from public-safe sources.
4. Five receipt records showing observation method and rights posture.
5. One Seeds draft generated from linked records.

That proves the system before volume is added.
