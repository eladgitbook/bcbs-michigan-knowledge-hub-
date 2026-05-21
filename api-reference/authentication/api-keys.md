---
icon: fingerprint
---

# API Keys & Tokens

## Requesting API Access

API credentials are provisioned by the Platform Engineering team. To request access:

{% stepper %}
{% step %}
### Submit an Access Request
Open a ticket in ServiceNow under **API Access Request**. Include:
- Application or system name
- Business justification
- Required scopes (see [Authentication Guide](authentication.md#available-scopes))
- Technical contact (engineer who will integrate)
{% endstep %}

{% step %}
### Security Review
Platform Engineering and InfoSec will review your request within 3 business days. Complex integrations involving PHI require additional approval from the CISO.
{% endstep %}

{% step %}
### Credential Delivery
Approved credentials are delivered via **1Password Teams** — never by email. You'll receive a share link to retrieve your `client_id` and `client_secret` securely.
{% endstep %}

{% step %}
### Integration & Testing
Use the sandbox environment (`api-sandbox.internal.bcbsm.com`) for testing. Sandbox credentials are separate from production.
{% endstep %}
{% endstepper %}

## Rotating Credentials

Credentials must be rotated:
- **Every 12 months** (enforced by policy)
- **Immediately** if suspected compromise

Rotation is self-service via the API Gateway console at `gateway.internal.bcbsm.com`. Rotating a secret invalidates the old one immediately — update your application before rotating in production.

## Environments

| Environment | Base URL | Purpose |
|---|---|---|
| **Sandbox** | `https://api-sandbox.internal.bcbsm.com/v2` | Development and testing |
| **Staging** | `https://api-staging.internal.bcbsm.com/v2` | Pre-production validation |
| **Production** | `https://api.internal.bcbsm.com/v2` | Live traffic |
