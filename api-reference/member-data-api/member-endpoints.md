---
icon: plug
---

# Member Endpoints

## GET /members/{memberId}

Retrieve a single member's eligibility and demographics.

**Path parameters:**

| Parameter | Type | Description |
|---|---|---|
| `memberId` | string | BCBS Michigan member ID (format: `BCM-XXXXXXXXX`) |

**Query parameters:**

| Parameter | Type | Default | Description |
|---|---|---|---|
| `include` | string | `eligibility` | Comma-separated fields: `eligibility`, `demographics`, `coverage`, `dependents` |
| `asOf` | date | today | Coverage effective date to check (`YYYY-MM-DD`) |
| `realtime` | boolean | `false` | Force real-time lookup (requires premium scope) |

**Example request:**
```bash
curl https://api.internal.bcbsm.com/v2/members/BCM-123456789 \
  -H "Authorization: Bearer $TOKEN" \
  -H "X-Client-ID: $CLIENT_ID" \
  -G --data-urlencode "include=eligibility,coverage,demographics"
```

**Example response:**
```json
{
  "memberId": "BCM-123456789",
  "subscriberId": "BCM-100000001",
  "eligibility": {
    "status": "active",
    "effectiveDate": "2026-01-01",
    "terminationDate": null
  },
  "demographics": {
    "firstName": "Jane",
    "lastName": "Doe",
    "dateOfBirth": "1985-03-15",
    "gender": "F"
  },
  "coverage": {
    "planCode": "PPO-GOLD-500",
    "groupNumber": "GRP-99001",
    "deductible": { "individual": 500, "metYTD": 235.00 },
    "outOfPocketMax": { "individual": 4000, "metYTD": 235.00 }
  }
}
```

---

## POST /members/batch

Check eligibility for up to 100 members in a single request.

**Request body:**
```json
{
  "memberIds": ["BCM-123456789", "BCM-987654321"],
  "include": ["eligibility"],
  "asOf": "2026-05-21"
}
```

**Response:** Array of member objects, with a `notFound` array for IDs that returned no results.

---

## PATCH /members/{memberId}/contact

Update a member's contact information.

**Requires scope:** `members:write`

**Request body:**
```json
{
  "phone": "313-555-0100",
  "email": "jane.doe@email.com",
  "address": {
    "street1": "123 Main St",
    "city": "Detroit",
    "state": "MI",
    "zip": "48201"
  }
}
```
