---
icon: paper-plane
---

# Submit a Claim

## POST /claims

Submit a professional (837P) or institutional (837I) claim.

**Required scope:** `claims:submit`

### Request Body

```json
{
  "claimType": "professional",
  "submitterId": "NPI-1234567890",
  "memberId": "BCM-123456789",
  "serviceLines": [
    {
      "procedureCode": "99213",
      "diagnosisCodes": ["Z00.00"],
      "serviceDate": "2026-05-15",
      "billedAmount": 185.00,
      "units": 1,
      "renderingProvider": {
        "npi": "NPI-0987654321",
        "firstName": "Dr. Sarah",
        "lastName": "Chen"
      }
    }
  ],
  "billingProvider": {
    "npi": "NPI-1234567890",
    "taxId": "38-1234567",
    "name": "Metro Health Associates",
    "address": {
      "street1": "500 Medical Pkwy",
      "city": "Detroit",
      "state": "MI",
      "zip": "48201"
    }
  }
}
```

### Response

```json
{
  "claimId": "CLM-2026-00498271",
  "status": "received",
  "submittedAt": "2026-05-21T14:32:00Z",
  "estimatedProcessingDate": "2026-06-04",
  "trackingUrl": "/v2/claims/CLM-2026-00498271"
}
```

## GET /claims/{claimId}

Check the status of a submitted claim.

**Example:**
```bash
curl https://api.internal.bcbsm.com/v2/claims/CLM-2026-00498271 \
  -H "Authorization: Bearer $TOKEN" \
  -H "X-Client-ID: $CLIENT_ID"
```

## GET /claims

Search claims with filters.

| Parameter | Type | Description |
|---|---|---|
| `memberId` | string | Filter by member |
| `status` | string | `submitted`, `processing`, `adjudicated`, `paid`, `denied` |
| `fromDate` | date | Service date range start |
| `toDate` | date | Service date range end |
| `page` | integer | Pagination (default: 1) |
| `pageSize` | integer | Results per page (max: 100) |
