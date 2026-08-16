---
publishedAt: "2026-08-16T13:30:00-04:00"
---

<!--
  PaladinsCat Blog — Terminus Ability-Damage Cheat Signature
  Public-facing content. No source code, internal paths, credentials,
  player names/IDs, or infrastructure details.
-->

# The Terminus Ability-Damage Signature

> A no-CD ultimate exploit leaves a statistically impossible fingerprint in
> per-match damage data. Here is the line that separates it from skilled play.

---

**Published:** August 2026 &nbsp;|&nbsp; **Topic:** Cheat detection · Game analytics

---

## The two metrics

- **Weapon damage/min (WPM)** — hand-weapon damage per minute.
- **Ability damage/min (APM)** — ability damage per minute (total physical
  minus weapon damage).

For a melee frontline like Terminus, the weapon is the main sustained damage
source. Ability damage is bounded by cooldowns — a player can only cast so
many abilities per minute. A no-CD ultimate removes that bound: spam the
ultimate, ignore the weapon. The result:

> **Ability damage far above the human maximum, weapon damage near zero.**

---

## The baseline

Every Terminus ranked match (12,436 valid; only zero-duration bad-data rows
excluded):

| Metric | p50 | p90 | p99 | Max |
|--------|----:|----:|----:|----:|
| WPM | 2,709 | 4,447 | 6,377 | 9,130 |
| APM | 876 | 1,851 | 3,120 | 24,412 |
| DPM | — | — | 7,664 | — |

Weapon damage dominates (≈3× ability at the median). Ability damage has a
hard practical ceiling: p99 is **3,120 APM**; the observed max (24,412) is a
cheater.

**No duration filter is needed.** Siege's fixed capture-and-push structure
means legitimate matches take a minimum time to finish. The shortest recorded
ranked Terminus match is **4.9 minutes**; there are **zero matches under 3
minutes**. Sub-two-minute rows are corrupted zero-duration records, not fast
games.

---

## The detection rule

```text
CHEAT ZONE:  APM > 3,120  AND  WPM < 500
```

- **APM > 3,120** — above the p99 of legitimate play.
- **WPM < 500** — weapon damage near zero.

APM alone is not enough: **94 legitimate matches** exceed 3,120 APM, but every
one deals ≥500 WPM — skilled players still swing the axe. Cheaters deal almost
none.

**Per-player rule** (catches intermittent triggers that average out):

```text
PLAYER RULE:  avg WPM = 0  AND  avg APM > 1,500
```

Both are needed: a cheater with one match at WPM=124 is only caught by the
per-match rule; a multi-match cheater with sub-threshold matches is only
caught by the per-player rule.

**Corroborating signals:** DPM ≈ APM (≈100% ability damage), WPM = 0 exactly,
absurd KDA (e.g. 29/0/0 in five minutes).

---

## Bot-fight distinction

An absurd KDA is not always cheating. When the enemy team disconnects, the
game replaces them with AI that dies constantly — 23/0/0 or 31/0/0 with no
exploit. Match data includes bot-kill breakdowns; a match where a large share
of kills are bot kills (e.g. 48%) is a bot-fight and is excluded. This
mattered: a 15/0/10 top candidate was confirmed legitimate once the bot-kill
ratio showed the enemy team had disconnected.

---

## Results

- **25 matches** hit the cheat zone.
- **28 distinct players** flagged, including 6 previously unflagged.
- **2 private accounts** flagged and resolved via the private-account system.
- Top offender: **29 matches** with the signature.

Two zone-touching candidates were manually reviewed and confirmed legitimate —
both had healthy weapon damage (3,470 and 4,058 WPM), i.e. skilled play, not
the cheat zone.

---

## Why it works

The signature is anchored to a physical constraint — cooldowns — not behavior.
Skilled play changes *how* damage is split between weapon and abilities, but
not the fact that abilities take time to recharge. A no-CD exploit changes
that constraint, and it shows up in the damage split of every match it
triggers. The baseline percentiles set the line; the second condition keeps
skilled players on the right side of it.
