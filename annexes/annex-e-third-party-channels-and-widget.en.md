# 25. Annex E. Third-Party Channels and Website Widget Schedule

- Document Path: [docs/platform-legal/annexes/annex-e-third-party-channels-and-widget.en.md](./annex-e-third-party-channels-and-widget.en.md)
- Counterpart Language Document Path: [docs/platform-legal/annexes/annex-e-third-party-channels-and-widget.id.md](./annex-e-third-party-channels-and-widget.id.md)
- Parent Agreement Document Path: [docs/platform-legal/terms-and-conditions.en.md](../terms-and-conditions.en.md#25-annex-e-third-party-channels-and-website-widget-schedule)
- Table of Contents Document Path: [docs/platform-legal/TOC.en.md](../TOC.en.md#25-annex-e-third-party-channels-and-website-widget-schedule)

### 25.1. WhatsApp Business Connection Requirements and Operational Terms

25.1.1. Pursuant to [Article 10 of the Agreement (docs/platform-legal/terms-and-conditions.en.md)](../terms-and-conditions.en.md#10-article-10-third-party-channels-and-website-widget-integration), to connect an AI Agent to WhatsApp Business, the Customer must maintain an active Subscription Plan that includes WhatsApp support and supply valid credentials issued to the Customer (access token, phone number identifier, business account identifier, and webhook verification token).

25.1.2. The Customer is solely responsible for configuring its webhook endpoint URL and verification token in its WhatsApp Business configuration, maintaining its account standing, and paying any messaging or conversation charges billed by the channel operator.

### 25.2. Telegram Bot Connection Requirements and Operational Terms

25.2.1. To connect an AI Agent to Telegram, the Customer must maintain an active Subscription Plan that includes Telegram support and supply a valid Telegram bot token issued to the Customer.

25.2.2. Upon saving a valid Telegram bot token on a deployed AI Agent, the Platform automatically registers the webhook connection with the Telegram service and removes the webhook when the Telegram connection is disabled or the AI Agent is stopped.

### 25.3. Embeddable Web Widget Origin Allowlist and Security Requirements

25.3.1. When embedding the Web Widget on external websites, the Customer must configure the allowed website origins in the Main Dashboard, subject to the following technical rules:
(a) Maximum Origins: Up to ten (10) distinct origins per AI Agent.
(b) Mandatory HTTPS Protocol: Every allowed origin must use the encrypted HTTPS protocol scheme. Plain HTTP origins are rejected.
(c) Valid Public Domain Hostname: Every allowed origin must specify a valid public domain name containing at least one dot and a valid top-level domain, and must not be a local loopback hostname, a raw IPv4 address, or an IPv6 address.
(d) No Wildcards or Paths: Wildcard characters, user-info prefixes, URL paths, query strings, and fragments are rejected.
(e) Browser Frame Enforcement: The Platform serves the embedded Web Widget with a browser frame security header restricted strictly to the Customer's validated allowed origins.
