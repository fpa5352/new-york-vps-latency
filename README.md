# New York VPS: Is the Server Actually in New York, What Does 1 GB Cost, and Which Plan Fits Your Workload? (Latency, Refund Terms, Hidden Limits)

A 1 GB VPS sold as "New York" runs from $2.48 to $13.99 a month depending on who you buy it from. Several of those servers sit in Secaucus, New Jersey, on the far side of the Hudson, and two providers publish street addresses that make the geography checkable rather than a matter of trust. What follows is what each price tier actually includes, the latency you can plan against from a New York metro node, and the order-form clauses that decide whether a cheap plan survives contact with your workload.

> **Quick version**
> - Static site, WireGuard endpoint, cron-driven scraper, uptime probe: 512 MB to 1 GB. The cheapest tier is the correct buy.
> - WordPress with MySQL, a handful of Docker containers, a trading bot: 2–4 GB, and check how resizing works before you commit.
> - A contract or auditor that names New York State: get the datacenter address and state in writing before paying.
>
> 👉 [See Evoxt's current New York VPS plans](https://bit.ly/EvoXt)

## What Evoxt charges for a New York VPS

Evoxt sells its New York / US East location from the same plan list as its other regions, so tier names carry across locations. The figures below come from third-party plan trackers: VPSBenchmarks' August 2026 review for the VM-1 through VM-8 tiers, and a deals listing for the 512 MB entry plan. Evoxt's checkout is the authority on current pricing, and VPSBenchmarks notes its list isn't exhaustive, so there may be tiers between these.

| Plan | vCPU · RAM | Storage | Price (USD) | Order |
| --- | --- | --- | --- | --- |
| VM-0.5 | 1 · 512 MB | 5 GB | $2.99/mo list, about $2.56/mo billed yearly | [Order VM-0.5](https://bit.ly/EvoXt) |
| VM-1 | 1 · 2 GB | 20 GB | $5.99/mo | [Order VM-1](https://bit.ly/EvoXt) |
| VM-2 | 2 · 4 GB | 30 GB | $11.99/mo | [Order VM-2](https://bit.ly/EvoXt) |
| VM-4 | 4 · 8 GB | 60 GB | $23.99/mo | [Order VM-4](https://bit.ly/EvoXt) |
| VM-8 | 8 · 16 GB | 80 GB | $47.99/mo | [Order VM-8](https://bit.ly/EvoXt) |

A few things sit outside those numbers and change the value calculation.

**Bandwidth is throttled, not billed.** Evoxt gives each VM a monthly allowance and slows the port past it instead of charging overage; VPSBenchmarks lists a 2 TB/month free allowance on a 2-core, 4 GB instance and records the provider as not charging for bandwidth at all. For a proxy or a media relay, that's a very different month-three bill from providers that meter at $0.29/GB.

**A weekly offsite backup is included on every VM**, including the 512 MB tier, and you restore it yourself from the control panel. Most providers at $2.99 treat backups as a paid add-on or skip them.

**What's missing matters too.** Evoxt's published feature list shows no DDoS filtering and no reverse DNS, and billing is monthly rather than hourly. If your workload attracts attack traffic, or you need PTR records for outbound mail, budget for a fronting proxy or pick a provider that has both.

No refund term appears in the plan data reviewed here, so ask support before paying if a money-back window is part of your decision.

👉 [Compare Evoxt's tiers and current pricing](https://bit.ly/EvoXt)

## Your New York VPS is probably in New Jersey

EDIS Global publishes the full address of its New York location: Equinix NY2, 275 Hartz Way, Secaucus, NJ 07094, coordinates 40.77859, -74.06935. Its own page calls this the "New York metro" rather than New York City. ExtraVM does the same thing: its NYC VPS runs at Evocative EWR1, 1 Enterprise Ave N, Secaucus, NJ 07094, described as "just across the Hudson River from Manhattan."

Cloudzy and Kamatera both market a New York region without a street address. Cloudzy's region is us-nyc-1, placed in "the New York metropolitan area"; Kamatera advertises New York data centers with no address published on its New York page. One hosting seller argues that most providers advertising New York VPS space are really in New Jersey, which is a sales pitch rather than an audit, but the two published addresses are consistent with it.

For latency this distinction means nothing. Secaucus is a few kilometres from Midtown, and the fiber routes are the same ones the Manhattan carrier hotels use. For compliance it means everything. If a contract, data-residency clause, or auditor requires the physical server to be in New York State, a New Jersey address fails that requirement even though the ping is identical. Ask for the datacenter address and state in writing before you pay, and keep the reply.

## What latency does a New York metro node actually deliver?

ProwHost publishes a table of indicative round-trip times from New York over public internet routes:

| Destination | Typical RTT |
| --- | --- |
| Toronto | ~12 ms |
| Chicago | ~20 ms |
| Miami | ~30 ms |
| Los Angeles | ~65 ms |
| London | ~70 ms |
| Frankfurt | ~80 ms |

ExtraVM quotes 5–30 ms across the East Coast and 70–90 ms to London and Amsterdam, so treat London as a 70–90 ms band rather than a single figure. These are averages across carrier routes and time of day, not guarantees, and they say nothing about the last mile between your users and their ISP.

For anything latency-sensitive, published tables are a starting point at best. EDIS Global and ExtraVM both run public looking-glass tools, and EDIS explicitly suggests testing latency to your trading platform before ordering. If you're routing orders to a broker endpoint or running an RTB worker against an exchange, that test tells you more than any table, this one included.

## Why four providers charge $3.48 to $13.99 for the same 1 GB

| Provider | 1 GB plan | Platform notes | Constraint worth knowing |
| --- | --- | --- | --- |
| Cloudzy | $3.48/mo (page currently shows 50% off from $6.95) | AMD EPYC, NVMe, DDR5, 40 Gbps uplink | 14-day money-back; region listed as us-nyc-1 with no street address |
| ExtraVM | $4.50/mo | Ryzen 9 / EPYC, NVMe, DDoS filtering, in-house support staff | 5-day refund, fiat payments only; Secaucus, NJ |
| EDIS Global | €4.99/mo excl. VAT | Intel vCPU, 2×10 Gbps uplink, Tier III facility | Resize needs a full shutdown plus manual partition work |
| ProwHost | $13.99/mo (page shows $19.99 struck through) | NVMe, 500 Mbit/s to 1 Gbit/s port | Ports 25, 465, 137–139 blocked; no refunds on virtual servers |

Most of that spread is hardware generation and port speed. Cloudzy and ExtraVM run current AMD parts with NVMe throughout; EDIS pairs Intel vCPUs with a 2×10 Gbps uplink in a Tier III facility; ProwHost sells 500 Mbit/s to 1 Gbit/s ports at close to four times Cloudzy's promotional rate.

The rest is what comes bundled and who answers tickets. ExtraVM includes DDoS scrubbing and states its support engineers are in-house rather than outsourced. Evoxt folds a weekly offsite backup into a $2.99 plan. Neither Cloudzy's nor ProwHost's figure should be treated as a long-term rate: both pages show discounted prices against struck-through list prices with no stated end date, and Cloudzy's "50% off all plans" banner carries no expiry either.

One currency note for cross-border buyers. EDIS prices in euros and excludes VAT, so a European customer paying from an EU billing address will see tax added at checkout, and anyone else carries FX conversion on top.

👉 [Check Evoxt's current New York plans and inclusions](https://bit.ly/EvoXt)

## Five things to confirm before you pay

**1. The refund window.** Cloudzy advertises 14 days. ExtraVM allows 5 days and only for fiat payments, so a crypto purchase has no exit. ProwHost states that virtual servers have no refund option at all. Kamatera sidesteps the question with a 30-day free trial instead. Read this before you migrate anything, because "I'll test it for a month and cancel" only works at some of these providers.

**2. Blocked outbound ports.** ProwHost blocks 25, 465, 137, 138 and 139, which rules out running your own SMTP and breaks NetBIOS-dependent Windows tooling. Any provider can have similar filters without advertising them prominently. If mail is part of the plan, ask about port 25 in writing.

**3. Overage pricing.** ProwHost bills $0.29/GB past the monthly allowance. Evoxt throttles the port instead. A video proxy, seedbox, or log shipper behaves very differently under those two regimes once traffic crosses the cap.

**4. What a resize costs in downtime.** Cloudzy says RAM, vCPU and storage resize live through KVM hotplug, most upgrades finishing under 60 seconds. EDIS requires a full shutdown and restart, and after a storage upgrade you expand the partition and filesystem yourself. Buying small and growing later is only cheap when the growth path doesn't need a maintenance window.

**5. Uplink speed is not your bandwidth.** A "40 Gbps" or "2×10 Gbps" figure describes the node's port, not a guarantee to your VM. EDIS says as much on its own speedtest panel: its 9,242 Mbps download result was recorded from the New York host platform to a nearby speedtest server, and the page states plainly that this is not per-VPS guaranteed throughput. Size expectations from the fair-use terms, not the port number.

👉 [See how Evoxt's plans handle backups and bandwidth](https://bit.ly/EvoXt)

## Which plan for which job

- **Static site, redirect, VPN endpoint, monitoring probe:** 512 MB. Evoxt's VM-0.5 at $2.99 or Cloudzy's 512 MB at $2.48. Both are enough; neither needs a control panel.
- **Small API or a WordPress install with a real database:** 2 GB. Evoxt VM-1 at $5.99 or ExtraVM's 2 GB at $8.00. A 5 GB disk will not hold a WordPress stack once plugins and uploads arrive.
- **Docker host with several containers, or a Postgres instance that gets used:** 4 GB. Evoxt VM-2 at $11.99 or ExtraVM's 4 GB at $14.00.
- **Trading bot or order router:** 2 GB is the floor, and CPU is rarely the constraint. Use the provider's looking glass against your broker endpoint first, then decide whether a New Jersey address satisfies whoever reviews your setup.
- **Mail server:** confirm port 25 before you buy anything, at any price.

Two things are worth doing before you pay anyone: get the datacenter's state in writing if a contract mentions New York, and screenshot the renewal price next to the introductory one. Everything else here can be fixed after deployment with a reboot or a resize.

👉 [Start with Evoxt's 512 MB plan or compare its larger tiers](https://bit.ly/EvoXt)
