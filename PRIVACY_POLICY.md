# Privacy Policy

This public repository must preserve civic memory without exposing private people to avoidable harm.

## Do not store

Do not store private personal information, including:

- Private phone numbers
- Private email addresses
- Exact private residential addresses for sensitive records
- Licence plates
- Private workplace identifiers
- Private social handles
- Child identifying details
- Victim, witness, patient, or vulnerable-person identifiers beyond what is safely public and necessary

## Sensitive public records

Some facts may be public but still unsafe to amplify. Use `review_required`, `public_metadata_only`, `public_aggregate_only`, or `blocked` when a record could increase harm.

## Geography safety

Use geography precision values:

- `exact_public_facility`
- `intersection`
- `block`
- `neighbourhood`
- `ward`
- `citywide`
- `withheld`
- `unknown`

For public dashboard output, sensitive records should usually use neighbourhood, ward, citywide, or aggregate display.

## Resident reports

Resident reports require special handling. Do not publish names, private addresses, accusations, photos, or identifying details without review and permission.

## Review flags

Use these review flags when needed:

- `child_or_youth_related`
- `victim_or_witness_related`
- `medical_or_overdose_related`
- `domestic_or_family_related`
- `sexual_safety_related`
- `culturally_sensitive`
- `private_address_sensitive`
- `rumour_or_unverified`
- `live_emergency_sensitive`
