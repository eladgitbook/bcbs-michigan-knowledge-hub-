---
icon: clock-rotate-left
---

# API Changelog

{% updates %}

{% update date="2026-05-10" tags="Member Data API" %}
### v2.1 — Batch Eligibility & Coverage Tier
- Added `POST /members/batch` for bulk eligibility lookups (up to 100 members)
- New `coverage_tier` field on member responses: `individual`, `employee+spouse`, `family`
- `asOf` query parameter now supports date ranges for historical eligibility lookups
{% endupdate %}

{% update date="2026-03-15" tags="Claims API" %}
### Claims API — ERA/Remittance Endpoint
- New `GET /claims/{claimId}/remittance` returns 835 ERA data for paid claims
- Added `voided` status to claim lifecycle
- `POST /claims/void` now accepts a `reason` field (required for audit trail)
{% endupdate %}

{% update date="2026-02-01" tags="Provider Directory API" %}
### Provider Directory — Language & Telehealth Filters
- New `language` query parameter filters providers by languages spoken
- New `telehealth` boolean filter returns providers offering virtual visits
- `distanceMiles` now included in all location objects when `zip` parameter is provided
{% endupdate %}

{% update date="2026-01-10" tags="Authentication" %}
### Token Expiry Extended to 1 Hour
Previously tokens expired after 30 minutes. Tokens now have a 3600-second (1 hour) lifetime. The `expires_in` field in token responses reflects this change. Update any applications with hardcoded 1800-second refresh logic.
{% endupdate %}

{% update date="2025-11-20" tags="All APIs" %}
### v2 GA — Breaking Changes from v1
Version 2 of the BCBS Michigan API is now generally available. v1 will be deprecated on **2026-11-20**. Key breaking changes:
- All IDs now use prefixed format (`BCM-`, `CLM-`, `NPI-`) instead of plain integers
- `GET /member` renamed to `GET /members/{memberId}`
- Error responses now use structured `error` object (see [Status Codes](status-codes.md))
- `Authorization` header required on all requests (v1 allowed API key in query param)
{% endupdate %}

{% endupdates %}
