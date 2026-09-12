---
publishedAt: "2026-08-16T13:30:00-04:00"
---

<!--
  PaladinsCat Blog — Terminus Ability-Damage Cheat Signature
  Public-facing content. No source code, internal paths, credentials,
  player names/IDs, or infrastructure details.
-->

# The Terminus Ability-Damage Cheat Signature

> What defines the signal, and how it is detected.

---

**Published:** August 2026 &nbsp;|&nbsp; **Topic:** Cheat detection

---

## What defines it

Two per-match damage metrics:

- **WDPM** — weapon damage per minute.
- **SDPM** — ability damage per minute.

A no-CD ultimate exploit lets a player spam abilities while weapon damage
stays near zero. Legitimate play cannot do that — cooldowns cap ability
damage. The signal is **high SDPM with near-zero WDPM**.

Legitimate ranked Terminus play (12,436 matches):

| Metric | p50 | p90 | p99 | Max |
|--------|----:|----:|----:|----:|
| WDPM | 2,709 | 4,447 | 6,377 | 9,130 |
| SDPM | 876 | 1,851 | 3,120 | 24,412 |

## How it is detected

```text
CHEAT ZONE:    SDPM > 3,120 AND WDPM < 500
PLAYER RULE:   avg WDPM = 0 AND avg SDPM > 1,500
```

The zone catches single matches; the player rule catches intermittent
triggers that average out. SDPM alone is not enough — 94 legitimate matches
exceed 3,120 SDPM, but all of them deal ≥500 WDPM.

## Results

- 25 matches in the cheat zone.
- 28 players flagged, including 6 previously unflagged and 2 private
  accounts.
- Top offender: 29 matches.
