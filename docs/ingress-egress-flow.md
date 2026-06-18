# Ingress and Egress Flow

This project separates collection, interpretation, review, and publication.

## Ingress

Ingress is the intake layer. It accepts source references, open-data indexes, archive references, official releases, media metadata, community organization updates, resident reports, and research notes.

Ingress should create source records, claim records, receipt records, and draft normalized records. It should not immediately publish.

## Normalization

Normalize incoming items into the core `record` model.

A record may be:

- event
- place
- organization
- archive reference
- photo reference
- map reference
- dataset snapshot
- news claim cluster
- civic decision
- timeline entry
- neighbourhood profile
- business entry
- venue entry
- cultural memory
- oral history
- dashboard metric
- story seed
- research note

## Review

Ibal reviews every record before public egress.

Review checks source, claim, time, place, rights, privacy, bin, confidence, sensitivity, and uncertainty.

## Storage

Store public-safe structured records in this repository. Store metadata and references for restricted or copyrighted materials. Do not store raw restricted content.

## Egress

Egress outputs may include:

- Seeds article draft
- Neighbourhood brief
- Timeline entry
- Dashboard card
- Aggregate dashboard data
- Civic packet
- Research note

Egress should be generated from linked clusters, not single unsupported inputs.

## Minimum Seeds cluster

A Seeds output should have:

- Place record
- Timeline entries where relevant
- Source records
- Archive references where relevant
- Media claims as metadata
- Asset references, not unauthorized copies
- Neighbourhood or ward links
- Conflict or uncertainty notes
- Rights status
- Public-safe summary
