---
icon: code
layout:
  width: wide
---

# API Reference

Internal REST APIs for BCBS Michigan systems. These APIs are for authorized internal use and partner integrations only.

{% hint style="warning" %}
**Internal use only.** All API access requires authentication with a valid service account token. Contact the Platform Engineering team to request credentials.
{% endhint %}

## Available APIs

<table data-view="cards">
  <thead>
    <tr>
      <th></th>
      <th></th>
      <th data-hidden data-card-target data-type="content-ref"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>👤 Member Data API</strong></td>
      <td>Member eligibility, demographics, and coverage information. Supports individual and batch lookups.</td>
      <td><a href="member-data-api/members-overview.md">Member Data API</a></td>
    </tr>
    <tr>
      <td><strong>🧾 Claims API</strong></td>
      <td>Submit, query, and update claims. Supports 837P/I electronic submissions and real-time status checks.</td>
      <td><a href="claims-api/claims-overview.md">Claims API</a></td>
    </tr>
    <tr>
      <td><strong>🏥 Provider Directory API</strong></td>
      <td>Search and retrieve provider information including location, specialties, and network participation.</td>
      <td><a href="provider-directory-api/providers-overview.md">Provider Directory API</a></td>
    </tr>
  </tbody>
</table>

## Base URL

```
https://api.internal.bcbsm.com/v2
```

All requests must include:
- `Authorization: Bearer <token>`
- `Content-Type: application/json`
- `X-Client-ID: <your-client-id>`
