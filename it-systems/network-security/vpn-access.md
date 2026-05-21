---
icon: shield-halved
---

# VPN Access

Remote employees and anyone working outside BCBS Michigan offices must connect via VPN to access internal systems.

## VPN Client: GlobalProtect

BCBS Michigan uses **Palo Alto GlobalProtect** for secure remote access.

### Installation

{% tabs %}
{% tab title="Windows" %}
1. Open **Company Portal** and search for "GlobalProtect"
2. Install the application
3. When prompted for a gateway, enter: `vpn.bcbsm.com`
4. Sign in with your BCBS Michigan credentials
5. Approve the MFA prompt in Microsoft Authenticator
{% endtab %}

{% tab title="macOS" %}
1. Open **Self Service** and find "GlobalProtect VPN"
2. Click Install
3. Enter gateway: `vpn.bcbsm.com`
4. Authenticate with your employee credentials + MFA
{% endtab %}

{% tab title="iOS / Android" %}
1. Download **GlobalProtect** from the App Store or Google Play
2. Enter portal address: `vpn.bcbsm.com`
3. Sign in with your BCBS Michigan account
4. Approve MFA when prompted
{% endtab %}
{% endtabs %}

## Connecting & Disconnecting

- **Connect:** Click the GlobalProtect icon in your system tray → **Connect**
- **Disconnect:** Click the icon → **Disconnect** (disconnect when not needed to preserve bandwidth)
- **Auto-connect:** Enabled by default when on non-corporate networks

## Troubleshooting

{% hint style="danger" %}
If you cannot connect to VPN and need immediate access to a critical system, call the IT Helpdesk at **x4357** — do not share credentials or use personal tools as a workaround.
{% endhint %}

| Symptom | Fix |
|---|---|
| "Cannot connect to gateway" | Check internet connection; try `ping vpn.bcbsm.com` |
| MFA prompt not appearing | Open Microsoft Authenticator and check for pending requests |
| Connected but can't reach internal sites | Disconnect and reconnect; check with IT if persistent |
| Slow performance on VPN | Connect to the nearest gateway (Detroit vs. Grand Rapids) |
