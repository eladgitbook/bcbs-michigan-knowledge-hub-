---
icon: circle-info
---

# Status Codes

Standard HTTP status codes returned by BCBS Michigan internal APIs.

## Success

| Code | Meaning |
|---|---|
| `200 OK` | Request succeeded. Response body contains the result. |
| `201 Created` | Resource created successfully (e.g., claim submitted). |
| `204 No Content` | Request succeeded with no response body (e.g., PATCH contact update). |

## Client Errors

| Code | Meaning | Common Causes |
|---|---|---|
| `400 Bad Request` | Invalid request body or parameters. | Missing required field, wrong data type, invalid date format |
| `401 Unauthorized` | Missing or invalid token. | Expired token, wrong credentials, missing `Authorization` header |
| `403 Forbidden` | Authenticated but not authorized for this operation. | Missing required scope, accessing another client's data |
| `404 Not Found` | Resource does not exist. | Wrong member ID, claim ID that doesn't exist in your client context |
| `409 Conflict` | Operation conflicts with current state. | Resubmitting a claim that was already voided |
| `422 Unprocessable Entity` | Request is well-formed but semantically invalid. | NPI not registered, member not eligible on service date |
| `429 Too Many Requests` | Rate limit exceeded. | See [Rate Limits](rate-limits.md) |

## Server Errors

| Code | Meaning | Action |
|---|---|---|
| `500 Internal Server Error` | Unexpected server error. | Retry with exponential backoff; report to Platform Engineering if persistent |
| `502 Bad Gateway` | Upstream system unavailable. | Usually transient; retry after 30 seconds |
| `503 Service Unavailable` | API is temporarily down for maintenance. | Check status page at `status.internal.bcbsm.com` |

## Error Response Format

All error responses follow this shape:

```json
{
  "error": {
    "code": "MEMBER_NOT_FOUND",
    "message": "No member found with ID BCM-999999999",
    "requestId": "req_7f3a2b1c",
    "timestamp": "2026-05-21T14:32:00Z"
  }
}
```

Use `requestId` when filing a support ticket — it traces the request through all systems.
