# Safety and Security Model

This repository is public, so safety and security are part of the data model, not an afterthought.

## Threat model

Primary risks:

- Publishing private personal information
- Amplifying unverified claims
- Copying restricted or copyrighted content
- Exposing sensitive locations
- Creating neighbourhood stigma
- Publishing live tactical emergency information
- Treating baseline poverty or food insecurity as a danger score
- Allowing automation to write unreviewed public egress
- Losing source provenance
- Losing correction history
- Over-trusting mixed-granularity proxy data

## Default safety posture

Default to metadata-only, review-required, and public-safe aggregation.

Records and metrics need explicit public display status before egress.

## Security controls

### Repository controls

- Use pull requests for major schema or policy changes after bootstrap.
- Require schema validation before accepting generated data.
- Keep generated public egress separate from primary records.
- Use clear commit messages that name the affected layer.

### Automation controls

- Automation defaults to dry run or metadata-only.
- Automation creates receipts for every observation.
- Automation must not publish public-facing egress without review.
- Automation must not store secrets in repo files.
- Automation must not store private addresses or private-person identifiers.

### Source controls

- Each source must have rights status.
- Each endpoint must have discovery status.
- Each source should track active, retired, missing, replaced, or blocked state.
- Source diffs should preserve previous state, not silently overwrite it.

### Dashboard controls

- Dashboards use reviewed metrics, not raw records.
- Sensitive records appear as aggregate-only or metadata-only.
- Avoid exact sensitive locations.
- Avoid single-score danger rankings.
- Show source confidence and granularity warnings.

## Ibal gates

Ibal blocks egress when:

- rights status is unknown or restricted
- public display status is blocked or review-required
- location precision is unsafe for the output
- source confidence is too low for the claim
- claim involves vulnerable people without adequate protection
- event is live and tactical details could create risk
- output creates unsupported stigma or danger framing

## Incident response

If unsafe data is committed:

1. Stop further automation touching that lane.
2. Create a remediation issue or note.
3. Remove or generalize the unsafe public data.
4. Preserve a non-sensitive correction receipt.
5. Review source, schema, and automation controls that allowed the issue.

Do not preserve private details in the remediation note.
