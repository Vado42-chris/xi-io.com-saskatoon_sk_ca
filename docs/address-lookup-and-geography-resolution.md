# Address Lookup and Geography Resolution

This project may eventually use address lookup to resolve public geography, but private addresses should not become durable public records.

## Core rule

The address is ingress-only. The public geography is durable.

## Safe pattern

1. A user enters an address or location.
2. The system resolves it to public geography.
3. The system stores only public geography identifiers.
4. The raw address is discarded unless a separate user-owned private vault explicitly requires it.

## Durable geography examples

- country
- province
- city
- ward
- neighbourhood
- federal riding
- provincial constituency
- census unit
- transit route
- public facility
- service catchment

## Do not store

- private residential address strings
- private latitude and longitude
- personal household notes
- private resident identity
- household-level baseline inference

## Baseline warning

Baseline data describes geography and structural context. It is not proof about an individual person, household, block, or private address.

## Status values

Use these status values in baseline, source, metric, and receipt records where appropriate:

```txt
address_lookup_transient
public_geography_only
personal_address_not_stored
baseline_layer_not_event_layer
mixed_granularity_warning
proxy_data
source_granularity_confirmed
source_granularity_unclear
```
