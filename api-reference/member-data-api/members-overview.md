---
icon: id-card
---

# Member Data API — Overview

The Member Data API provides access to member eligibility, demographics, and coverage information across BCBS Michigan and Blue Care Network plans.

## Key Capabilities

- **Eligibility lookup** — real-time coverage verification by member ID or subscriber ID
- **Demographics** — name, address, date of birth, contact information
- **Coverage details** — plan type, effective dates, deductible and out-of-pocket status
- **Batch lookups** — up to 100 members per request for bulk eligibility checks
- **Dependents** — retrieve subscriber + all dependents in a single call

## Base Path

```
/v2/members
```

## Data Freshness

Member data is updated nightly from core systems. Real-time eligibility queries reflect the prior day's enrollment updates. For immediate enrollment confirmation, use the `?realtime=true` query parameter (higher latency, premium scope required).

## Required Scopes

| Operation | Scope |
|---|---|
| Read member data | `members:read` |
| Update contact info | `members:write` |
| Batch eligibility | `members:read` + `members:batch` |

## Rate Limits

- Standard: 1,000 requests/minute
- Batch endpoint: 100 requests/minute

See [Rate Limits](../reference/rate-limits.md) for full details.
