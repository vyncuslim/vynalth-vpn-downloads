# Community exit node and sponsorship program (DRAFT)

**Status:** Not launched, no new countries online. Prepared 2026-11-07 for review. This repository contains beta-download and rollout documentation, **not** the WireGuard node or client implementation.

## Purpose and boundaries

Vynalth AI VPN is an independent technology project (not represented as an incorporated company). We are exploring **explicitly authorized**, no-subscription-fee international WireGuard exit nodes for a **small, controlled beta**. This is an inquiry, not a request for blind public traffic relaying. No contributor is obliged to provide an exit node, and no host may be advertised until full acceptance.

**Do not** use random public proxies, compromised hosts, identity/credit-card cycling for cloud trial accounts, or provider plans that prohibit public VPN egress. An on-paper region or tunnel transit PoP is not a real egress country.

## Reviewed infrastructure sponsorship leads (not approved)

| Lead | Official program | What is actually offered | Fit and blockers |
|---|---|---|---|
| UFO.Hosting | https://ufo.hosting/en/project-support-program | Up to 3 months free KVM VPS (2 vCPU, 2 GB RAM, 40 GB SSD), with an honest public write-up | Time-limited; requires verified audience >=1000 monthly visitors/subscribers or >=100 GitHub stars; **must obtain written consent** to operate a third-party VPN exit, allowed region, quota, public IPv4 cost, age/contract terms |
| Enzonic | https://www.enzonic.com/grants | Project-specific sponsored server for visible sponsor credit, project must be publicly accessible | **May be app/game container, not a full VPS**; confirm TUN, IP forwarding, UDP, stable exit IP, commercial/public VPN policy, and free quota. Under-18 eligibility explicitly requires guardian permission |
| ZMTO | https://zmto.com/opensource | Open-source VPS sponsorship | Requires a qualified public repo, recognized license, active maintenance. VPN source/license not yet established. Confirm public VPN AUP before applying |
| BitFolk | https://tools.bitfolk.com/wiki/Sponsored_hosting | Select charitable/nonprofit projects, 1.5 GiB/10 GiB/2 TB transfer baseline | Nonprofit community services only, potentially ineligible for a general VPN product; ask only if scope legitimately meets nonprofit requirements |

### Explicitly rejected / not viable

- **FreeVPS.org** (https://www.freevps.org/) explicitly **prohibits public VPNs** under its current published Operating Policy, even though it advertises worldwide regions. Never use it for public Vynalth AI VPN exit nodes.
- Oracle Cloud Always Free VM is limited to the account's **home region**: https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm . Does **not** make Japanese/European VMs free in the existing SG tenancy.
- Google e2-micro free VM is limited to certain US locations and **1 GB/month VM egress**: https://docs.cloud.google.com/free/docs/free-cloud-features . Public IPv4, other networking and overage charges must be evaluated separately.
- Vercel Functions and Cloudflare Workers cannot simply substitute for a generic WireGuard UDP exit node.

## Host-acceptance questionnaire: send BEFORE collecting node credentials

1. **Explicit consent:** Can we operate a **managed VPN/WireGuard egress** serving third-party beta users from your network? Will the upstream/datacenter/ISP AUP allow it? Please confirm in writing.
2. **Region:** Actual host country/city and stable geographic egress IP; no misleading GeoIP flag.
3. **Network:** Linux root/admin or needed capabilities, kernel TUN, UDP both ways, IP forwarding and firewall/NAT capability; is an actual public IPv4 available or is there only NAT with forwarded ports? IPv6 support?
4. **Limits:** Available sustained monthly egress, fair use and speed; does a VPN require a special plan? Any invoice, deposit, auto-renew, payment card, surprise IPv4/bandwidth cost?
5. **Security:** Who retains physical/VM control, who handles abuse complaints, patches, key revocation, incident response, and how quickly can traffic be disabled? Do not ask volunteers to expose residential family networks to strangers.
6. **Reliability:** Expected availability, monitoring consent, cancellation/termination notice, geographic location, technical support and contact pathway.
7. **Eligibility:** Any age, jurisdiction, formal company registration, open-source license, content promotion or guardian-approval requirements.
8. **Data privacy:** What network metadata is logged by the provider or ISP, and what geographic privacy obligations apply?

Do not request SSH passwords, WireGuard private keys or root API tokens through public GitHub Issues, PRs or email. Use individual credential delivery via an approved secure channel after written eligibility and capacity approval. Each node must have **unique WireGuard private keys** and per-user/device peer isolation.

## Proposed onboarding workflow (staging first)

1. Sponsor expresses interest via private project contact channel; collect only provider name, country, available resources, AUP confirmation and voluntary contact. Keep sensitive fields private.
2. Technical lead manually verifies provider identity, permission to host public third-party VPN exit, public IPv4/IPv6, quotas and an authorized sponsor representative. If permission is denied or unclear: STOP.
3. Implement on a separately provisioned staging host (one test peer, one node); restrict server firewall and allowed users; no public rollout, no wildcard forwarding from unknown clients.
4. Validate real external **IPv4 egress from intended country**, DNS resolver location and no DNS or IPv6 leakage; reject advertising IPv6 if not properly routed. Validate Kill Switch failure behavior on actual Android/Windows devices.
5. Enforce access authentication, per-device revocation, rate limiting, abuse reporting, egress quota and safe shutdown. Recheck sponsor bandwidth and legal terms. Avoid content inspection or indefinite connection log storage.
6. Create a sanitized operational evidence record (date, city, approved quota, test result, uptime); never include key material in public repo.
7. Only after signoff, provision DNS hostnames, enable the node in a **real server-controlled registry**, run one staged client release, and monitor. Failure => region off, user informed, SG-01 not impacted.

## Resource request

For one **non-production pilot** initially, ask for an existing donated Linux VM: >= 1 vCPU, >=1 GB RAM, >=10 GB disk, kernel TUN, UDP, stable public egress address and a **hard traffic cap**. Desired host country: JP, DE, US, FR, GB or any real region not yet operated. Confirm sponsor covers **all** charges and requires no paid upgrade. Public rollout requires explicit separate authorization.

## Action status (2026-11-07)

- [x] Identify candidate official programs and rejections
- [x] Write qualification questionnaire and pilot plan
- [ ] Confirm with each provider that public/third-party WireGuard VPN exits are permitted
- [ ] Verify legal/age/account requirements with responsible adult if required
- [ ] Receive actual sponsored server and secure provisioning details (never publish)
- [ ] Deploy staging WireGuard node in approved country
- [ ] Run device and egress acceptance testing
- [ ] Enable first new region under explicit rollout authorization

> This document is a request-for-support and safety screen. It does not constitute any received sponsorship or public VPN production readiness.
