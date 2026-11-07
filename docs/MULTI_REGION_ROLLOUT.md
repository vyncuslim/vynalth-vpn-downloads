# Vynalth AI VPN — Multi-Region rollout (planning only)

> Status: DRAFT, 2026-11-07. This repository distributes beta artifacts; it is **not** the VPN server control plane or the source of the Windows/Android/Linux clients. Neither this document nor `multi-region-nodes.example.json` enables any VPN location.

## Confirmed baseline / non-regression

- Existing SG-01: Oracle Cloud Singapore, legacy WireGuard IPv4 endpoint `168.107.64.137:51820` (operator-reported), public hostname `vpn.vynalthai.com`, DNS `10.0.0.173`.
- Do **not** alter SG-01 `wg0`, existing peers, DNS, kill switch or IPv4 routes to add regions.
- SG-01 IPv4 previously connected; IPv6 public end-to-end, Android real-device and complete Windows/Linux acceptance remain unresolved. No claim of global production readiness.
- `docs/multi-region-nodes.example.json` deliberately marks **every** region `selectable:false` and provides **no** active provisioning data.

## Target coverage (not yet deployed)

Wave 1: SG-01 existing; JP-01 Japan, DE-01 Germany, US-01 United States (new, planned).
Wave 2: MY-01 Malaysia, KR-01 South Korea, HK-01 Hong Kong, GB-01 United Kingdom, FR-01 France, NL-01 Netherlands, CA-01 Canada, AU-01 Australia (planned).

Each new country needs its **own real in-country exit server** and region-specific public IP. A UI flag, proxy DNS change, or cloud edge function does not create that exit.

## Implementation contract (in VPN application/control-plane repo, not this downloads repo)

1. Add server-managed `GET /api/vpn/regions` (read-only, public-safe metadata) and authenticated `POST /api/vpn/configs` (device- and user-authorized config issuance). Require signed/verified metadata or secure authenticated HTTPS delivery, `Cache-Control: no-store` for credentials, deny unknown/disabled regions.
2. For each region create a separate WireGuard gateway (UDP 51820 or another documented UDP port), unique server private/public key pair, isolated peer database/keys, firewall/NSG and least-privilege management. Never copy SG-01 private keys or active peer configuration to another region.
3. Use hostnames such as `jp-01.vpn.vynalthai.com` only **after** the host exists and deployment tests pass. Keep legacy `vpn.vynalthai.com` on SG-01. Do not publish placeholder A/AAAA DNS records.
4. Clients: list regions with explicit availability (online/offline/coming soon); show only genuinely accepted regions as connectable. Auto-connect considers user preference, regional health and latency, not country label alone. Do not switch exit country silently.
5. Privacy/security: device permission check; deny cross-user config issuance; per-node key rotation/revocation; disconnect and kill-switch preserve no-leak behavior; do not log raw browsing traffic or private keys. Protect the provisioning API against replay, abuse, SSRF and rate-limit exhaustion.
6. Reliability: metrics for WireGuard handshake, real external IPv4 and IPv6, DNS, packet loss, RTT, service uptime, egress quota and cost; alert on regressions. Disable unhealthy nodes server-side and show honest status. No silent fail-open outside VPN.
7. Rollback: feature flag per region, immutable release manifest and rollback; never automatically edit production network rules. SG-01 must remain unaffected when a new-region deployment fails.

## Release gate per new region

- [ ] Sponsorship/free-tier allowance or written cost approval, **including bandwidth overages**; target RM0/month until funding exists.
- [ ] A real VM with controllable public IP, supported UDP ingress/egress, country verified from independent checks.
- [ ] WireGuard device-specific key provisioning and handshake tested (no shared user private keys).
- [ ] Genuine external IPv4 exit and DNS requests match the intended region; validate IPv6 too if advertised. Block/disable broken dual-stack.
- [ ] Windows 11, Android actual phone and Linux client tests; Wi-Fi ↔ cellular transition, restart, reconnect and kill-switch checks.
- [ ] DNS and IPv6 leak tests, MTU, route isolation, key revoke, throttling/abuse handling.
- [ ] Latency / packet loss and sustained load tests, independent region geolocation, uptime monitor.
- [ ] Status changed to selectable **only after** successful acceptance, with evidence/timestamp and release owner confirmation; staging preview before production.

## Free-tier reality check (2026-11-07)

- Oracle's Always Free VM compute is restricted to the tenancy **home region**. Existing Singapore Always Free does not give additional always-free Japan/Germany nodes.
  https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm
- Google Cloud free tier gives one e2-micro VM-hour allowance in selected US regions, but **only 1 GB/month outgoing VM traffic**. This can be a low-volume US functional test, not a credible free public VPN exit.
  https://docs.cloud.google.com/free/docs/free-cloud-features
- Vercel hosting for the website/API is not a replacement for a UDP WireGuard exit VM.
- No new region should be deployed on a paid plan or incur billable usage without cost approval. Do not treat promotions or short-term trial credits as permanent free capacity.

## Dependency / next implementation location

The public `vyncuslim/vynalth-vpn-downloads` repo is only the signed/beta download publishing surface. The Vercel `vynalth-ai-vpn` project serves a VPN information/download site, not proof of a globally deployed WireGuard back end. **The actual client/management source repository and region provisioning service must be located before coding client and backend integrations.** This PR intentionally modifies no running gateway, app release or production endpoint.
