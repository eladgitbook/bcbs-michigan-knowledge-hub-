---
icon: stethoscope
---

# Provider Directory API — Overview

The Provider Directory API provides access to BCBS Michigan's network of contracted providers, including physicians, hospitals, urgent care centers, and behavioral health facilities.

## Key Capabilities

- **Provider search** — by name, NPI, specialty, location, or network
- **Network participation** — verify if a provider is in-network for a specific plan
- **Location details** — office addresses, phone numbers, accepting new patients status
- **Specialties & languages** — filter by specialty and languages spoken
- **Facility information** — hospital affiliations, accreditations

## Base Path

```
/v2/providers
```

## Networks

| Network Code | Description |
|---|---|
| `BCN` | Blue Care Network (HMO) |
| `BCBS-PPO` | Blue Cross Blue Shield PPO |
| `BCBS-HDHP` | High-Deductible Health Plan network |
| `BCBS-GOVT` | Medicare Advantage network |

## Required Scope

All provider directory operations require `providers:read`.
