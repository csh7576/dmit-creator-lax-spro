# DMIT Creator: What the LAX.sPro High-Defense Plan Actually Includes, What It Costs, and How to Check Stock Before You Buy

Most people who search for "DMIT Creator" have the same three questions. What is this plan, what does it cost right now, and can I actually order one. Short version: it's the `PVM.LAX.sPro.CREATOR` VPS in DMIT's Los Angeles Secure Pro line, it lists at $71.99 per quarter, and the third question is the one that genuinely needs a longer answer.

Here's the whole picture, including the part where the plan line was publicly scheduled for retirement.

## What "Creator" actually refers to

DMIT names products in a code format you can decode: `PVM.LAX.sPro.CREATOR`.

- **PVM** — a KVM virtual machine
- **LAX** — Los Angeles data center
- **sPro** — Secure Pro, DMIT's DDoS-hardened tier (sometimes written "Premium Secure" or "Anti-DDoS sPro")
- **CREATOR** — the plan tier itself

So "DMIT Creator" is not a separate product family or a creator-economy branding gimmick. It's one specific plan inside DMIT's sPro line, and it's the entry point of that line.

DMIT itself has been operating since 2017 and sells in Los Angeles, Hong Kong, and Tokyo, with its reputation built on premium China-optimized routes. Third-party reviews consistently describe the hardware as AMD EPYC processors, NVMe storage, and RAIDs, with no meaningful overselling — that combination is why the pricing sits where it does. Reviews also note DMIT is fine with Alipay and PayPal and offers a Chinese interface, even though support tickets get English replies.

What separates sPro from DMIT's regular Premium (Pro) line is where the protection sits:

- **Inbound** traffic is processed through Cloudflare Magic Transit
- **Outbound/return** traffic runs on DMIT's Premium routes, meaning CN2 GIA back toward China
- **DDoS mitigation** is described as always-on with 5Tbps+ of capacity

If you want a plain-English summary: Pro gives you a fast, clean, China-friendly route. sPro gives you roughly the same return route but adds a Cloudflare scrubbing layer on the way in, so a large attack hits Cloudflare's network instead of your VM.

## What $71.99/quarter buys

| Item | Spec |
| --- | --- |
| Plan code | PVM.LAX.sPro.CREATOR |
| CPU | 2 vCPU |
| RAM | 2GB |
| Storage | 20GB SSD |
| Monthly traffic | 1.5TB |
| Bandwidth | 100Mbps, upgradeable to 200Mbps |
| IPs | 1 IPv4 + 1 /64 IPv6 |
| DDoS protection | 5Tbps+, always-on, via Cloudflare Magic Transit |
| Return routing | CN2 GIA toward China |
| Billing | $71.99/quarter (list) |
| Test range | 45.88.194.0/24 |

That spec sheet is small for the money if you only look at CPU and RAM. It makes more sense once you look at what the routing and the scrubbing layer cost — this is not a plan you buy for compute.

👉 [check the current DMIT Creator listing and stock](https://www.dmit.io/aff.php?aff=12046)

## The traffic counter is the detail most buyers miss

This is worth reading twice before ordering.

According to a DMIT usage guide updated in late 2025, the **Creator plan meters traffic in both directions and suspends the VM if you exceed the cap**. That's different from several of DMIT's Tier 1 plans, which were changed to count only `MAX(IN, OUT)` — the larger of upload or download, not the sum.

In practice, a 1.5TB monthly allowance under bidirectional metering behaves more like 750GB in each direction if your traffic is symmetrical. For a site serving pages, download usually dominates, so it's not catastrophic. For anything that both pulls and pushes heavily — backups, mirroring, file relays — it will disappear faster than the number on the order page suggests, and the consequence is suspension rather than throttling.

Bandwidth is the second cost lever. The base port is 100Mbps; DMIT lists an upgrade to 200Mbps for around $9 per month.

## Availability: the part that isn't settled

Here's where this plan gets awkward, and it would be dishonest to pretend otherwise.

DMIT announced that the **LAX.sPro product line would shut down on December 31, 2025**, with existing sPro customers served until that date. The stated reason was that the Cloudflare contract ended early and the product line's performance hadn't matched expectations.

At the same time, the Creator plan has been showing up restocked at a higher price than its earlier $56.99 per quarter, and it's still being written up as an active orderable plan in current hosting coverage.

Both things are on the record, and they don't fully reconcile. The practical upshot: **treat Creator availability as uncertain, and confirm on the order page before you plan a migration around it.** Don't prepay a long cycle on the assumption the line is around for years, and don't assume the page you're looking at reflects live inventory an hour from now.

👉 [verify current availability before you decide](https://www.dmit.io/aff.php?aff=12046)

DMIT's stock situation is a recurring theme across their premium lines in general. The China-optimized Pro tiers in Los Angeles, Hong Kong, and Tokyo go in and out of stock regularly, and restock alerts are a small genre of blog post on their own.

## How Creator compares to DMIT's other Los Angeles lines

DMIT's Los Angeles lineup splits by network quality, and the price gap between tiers is almost entirely a routing gap.

| Line | Entry configuration | Entry price | Routing | Best for |
| --- | --- | --- | --- | --- |
| Tier 1 (T1) | 1 vCore / 1GB / 20GB SSD / 1TB, 4Gbps burst | from about $36.9/year | International routing, no China optimization | Budget projects, global audiences |
| Eyeball (EB) | 1 vCore / 2GB / 20GB SSD / 1.5TB, 2Gbps | from about $9.99/month | CMIN2 optimized | China-facing traffic where budget matters |
| Premium (Pro) | 1 vCore / 2GB / 20GB SSD / 1TB, 1Gbps | from about $9.99/month | CN2 GIA both directions | Sites and apps needing stable China latency |
| Secure Pro (sPro / Creator) | 2 vCore / 2GB / 20GB SSD / 1.5TB, 100Mbps | $71.99/quarter | Cloudflare Magic Transit in, CN2 GIA out, 5Tbps+ DDoS mitigation | Anything that gets attacked |

Prices in that table are entry-level list prices and they move — DMIT adjusts them, and stock states change what's actually orderable at any given moment. Hong Kong and Tokyo equivalents exist across the same series and cost more, because the bandwidth itself costs more there.

The comparison that matters: the Pro line's smallest plan and the Creator plan start at similar monthly money, but Pro gives you roughly four times the bandwidth and a bigger monthly traffic allowance, while Creator trades both of those away for the scrubbing layer. That's the actual decision. If you don't need DDoS protection, Pro is the better buy — it's not close.

## What you can scale

Creator isn't meant to be replaced when you outgrow it; it's meant to be upgraded in place. DMIT lists upgrade ranges across CPU, memory, storage, traffic, and port speed rather than forcing a plan migration.

Configuration ceilings on this plan line run up to roughly 8 vCPU, 16GB RAM, 400GB SSD, and 20TB of monthly traffic on a 200Mbps port, based on how the sPro lineup has been documented. Storage and bandwidth upgrades are billed separately, so the headline $71.99 is the floor, not the ceiling.

One note on IPs: high-DDoS sPro instances historically couldn't have their IP swapped freely. The Cloudflare setup requires whitelisting at the subnet level, which is something DMIT pays for, so IP changes were restricted by design. If your workflow depends on rotating IPs, verify the current policy before buying.

## Who should buy Creator, and who shouldn't

**It fits, if:**

- You run something that gets attacked, or has been attacked before — game servers, e-commerce checkouts, payment and webhook endpoints, anything adversarial traffic finds interesting
- You need real China-optimized return routing on top of that protection, not instead of it
- You're comfortable on an unmanaged VPS. DMIT's support covers the hypervisor, power, panel, and network. It does not cover your web stack, database tuning, or application errors
- You'd rather pay $260 a year and stop thinking about it than save $150 and handle a nullrouted IP yourself

**It doesn't fit, if:**

- You just need cheap Linux compute. The Creator spec is 2 vCPU and 2GB. Cheaper DMIT tiers give you more for less
- You're running a proxy or personal tunnel. You'd be paying for a scrubbing architecture you never touch. Reviewers have been saying this about sPro since 2021, and it's still true
- You want to trial it casually. The refund window is narrow and promo-priced orders are usually excluded from refunds entirely
- You need managed support

## Price history worth knowing

If you remember sPro being cheap, you're not imagining it. Early promotional periods had the same plan landing around $106 to $113 per year after a 15% recurring code, and around $14.90 per month at list. The current list works out to roughly $260 per year with the annual discount applied.

That's a meaningful jump for the same tier. Some of it is the restock pricing, some of it is that the earlier numbers were promotional. Either way, don't budget from 2021 numbers.

## Billing, discounts, and refunds

DMIT mostly doesn't run coupon-driven marketing. The discount structure is baked into the billing cycle instead:

- **Monthly** — list price
- **Semi-annual** — about 2.77% off, landing near $140 per half-year
- **Annual** — about 9.71% off, landing near $259.99 per year

Third-party trackers still list recurring codes for the sPro line. `Go-Build-A-Site` is the one that has circulated longest, and it's been listed as an annual 15% recurring discount on the LA sPro line as recently as late 2025 — but codes get rotated, and you should test it at checkout rather than assume it applies.

Refunds follow DMIT's standard policy: within a few days of purchase, under 10GB of traffic used, and no abuse flags. Refunds to account balance typically skip the fee; refunds back to your original payment method generally carry one. Sale and promo-priced orders are commonly excluded. Read the current terms rather than trusting the summary, since this is the kind of policy that gets adjusted.

Payment methods include PayPal, Alipay, and credit cards. Good luck getting a faster answer out of support in Chinese than English — the interface is translated, the ticket replies usually aren't.

## How to order

1. Open the DMIT order page through the link below and find the sPro / Secure Pro section in the Los Angeles location
2. Confirm the CREATOR plan is actually in stock — this is the step people skip and regret
3. Pick your billing cycle. Annual is the cheapest per month; if availability genuinely worries you, quarterly keeps your exposure short
4. Apply any code you have at checkout and confirm the discount actually applies to the total
5. Pay, then log into the panel to set your root password, install an OS, and check the traffic metering view so you know exactly how your 1.5TB is being counted

👉 [start an order on the DMIT Creator plan](https://www.dmit.io/aff.php?aff=12046)

## Quick answers

**Is Creator the same as LAX.Pro?**
No. Same family of routing on the way out, but Creator adds Cloudflare Magic Transit on the way in plus always-on mitigation. That's the whole price difference.

**What happens if I go over 1.5TB?**
The VM is suspended rather than throttled. Budget for bidirectional counting, not one-way.

**Can I upgrade CPU, RAM, or storage later?**
Yes, configuration scales in place. Bandwidth and traffic upgrades are billed on top.

**Will the line still exist next year?**
DMIT announced an end-of-2025 shutdown for LAX.sPro and has also restocked the plan since. Nobody outside DMIT can tell you which direction it lands. Check before you commit, and weight your billing cycle accordingly.

**Is it worth $260/year?**
Only if you need the DDoS layer. If you need China-optimized routing and nothing is attacking you, DMIT's Pro line does that job for less money.

## The bottom line

The Creator plan is a specialist tool priced like one. You're paying for a Cloudflare-grade scrubbing layer on the inbound path and CN2 GIA on the return, wrapped around a deliberately modest 2 vCPU / 2GB VM. If your workload is a site or service that keeps getting hit, that trade makes sense, and the bidirectional traffic metering is a real constraint you should size against before ordering.

If it isn't, DMIT has cheaper lines that solve the routing problem without charging you for protection you'll never trigger.

Either way, check stock and confirm the current price on the order page before you buy. This plan has changed price, changed availability, and been publicly slated for retirement all within a fairly short window, and no article written today can promise what the page says tomorrow.

Details on this page reflect published pricing and product information gathered from DMIT coverage and documentation; specs, prices, stock, and discount codes can change at any time.
