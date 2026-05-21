---
icon: gauge-high
---

# Rate Limits

All BCBS Michigan internal APIs enforce rate limits per `client_id` to ensure platform stability.

## Default Limits

| Endpoint | Limit | Window |
|---|---|---|
| `GET /members/{id}` | 1,000 requests | per minute |
| `POST /members/batch` | 100 requests | per minute |
| `GET /claims` | 500 requests | per minute |
| `GET /claims/{id}` | 1,000 requests | per minute |
| `POST /claims` | 200 requests | per minute |
| `GET /providers` | 500 requests | per minute |
| `GET /providers/{npi}` | 1,000 requests | per minute |

## Rate Limit Headers

Every response includes headers indicating your current usage:

```
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 847
X-RateLimit-Reset: 1716302400
```

`X-RateLimit-Reset` is a Unix timestamp indicating when the window resets.

## Handling 429 Responses

When you exceed the limit, the API returns `429 Too Many Requests` with a `Retry-After` header:

```
HTTP/1.1 429 Too Many Requests
Retry-After: 23
```

Implement exponential backoff with jitter:

```python
import time, random

def request_with_retry(fn, max_retries=5):
    for attempt in range(max_retries):
        response = fn()
        if response.status_code != 429:
            return response
        wait = (2 ** attempt) + random.uniform(0, 1)
        time.sleep(wait)
    raise Exception("Rate limit exceeded after retries")
```

## Requesting Higher Limits

If your use case requires higher throughput, submit a request to Platform Engineering via ServiceNow. Include:
- Estimated requests per minute at peak
- Business justification
- System/application name
