---
icon: magnifying-glass
---

# Search Providers

## GET /providers

Search the provider directory with filters.

### Query Parameters

| Parameter | Type | Description |
|---|---|---|
| `name` | string | Provider last name or facility name (min 3 chars) |
| `npi` | string | National Provider Identifier |
| `specialty` | string | Specialty code (e.g., `207Q00000X` for Family Medicine) |
| `network` | string | Network code: `BCN`, `BCBS-PPO`, `BCBS-HDHP`, `BCBS-GOVT` |
| `zip` | string | Center of search radius |
| `radius` | integer | Search radius in miles (default: 10, max: 50) |
| `acceptingNewPatients` | boolean | Filter to providers accepting new patients |
| `language` | string | ISO 639-1 language code (e.g., `es`, `ar`) |
| `page` | integer | Pagination (default: 1) |
| `pageSize` | integer | Results per page (max: 50) |

### Example — Primary Care Near Detroit

```bash
curl "https://api.internal.bcbsm.com/v2/providers" \
  -H "Authorization: Bearer $TOKEN" \
  -H "X-Client-ID: $CLIENT_ID" \
  -G \
  --data-urlencode "specialty=207Q00000X" \
  --data-urlencode "network=BCBS-PPO" \
  --data-urlencode "zip=48201" \
  --data-urlencode "radius=10" \
  --data-urlencode "acceptingNewPatients=true"
```

### Response

```json
{
  "total": 48,
  "page": 1,
  "pageSize": 10,
  "providers": [
    {
      "npi": "NPI-0987654321",
      "firstName": "Sarah",
      "lastName": "Chen",
      "credentials": "MD",
      "specialty": "Family Medicine",
      "acceptingNewPatients": true,
      "networks": ["BCBS-PPO", "BCN"],
      "locations": [
        {
          "name": "Metro Health Associates",
          "address": "500 Medical Pkwy, Detroit, MI 48201",
          "phone": "313-555-0200",
          "distanceMiles": 2.3
        }
      ],
      "languages": ["en", "zh"]
    }
  ]
}
```

## GET /providers/{npi}

Retrieve full details for a specific provider by NPI.

Returns the full provider object including all locations, hospital affiliations, board certifications, and network participation history.
