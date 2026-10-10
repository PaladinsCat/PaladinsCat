---
title: "Reading Paladins Statistics: Win Rates, Samples, and Missing Data"
author: "PaladinsCat Team"
date: "October 10, 2026"
publishedAt: "2026-10-10T00:20:00-04:00"
excerpt: "A practical guide to interpreting Paladins win rates, performance samples, matchup tables and missing data, with worked hypothetical examples."
---

# Reading Paladins Statistics: Win Rates, Samples, and Missing Data

A high win rate becomes useful when you know which matches produced it, how
many observations it contains, and what the table measures. Those details help
you decide whether a result is relevant to your champion, mode and next match.

This guide explains how to make that comparison on PaladinsCat. Every numerical
example below is hypothetical; none is a reported live champion or player result.

## Start with what one observation means

Different pages count different things. Keep the unit beside the number:

| View | What an observation represents | What to check |
|:---|:---|:---|
| Players in the last 24 hours | A distinct public player identity observed in tracked matches | The rolling window and queue coverage |
| Performance distribution | An eligible player-match value for the selected metric | The queue, champion or role, and metric sample count |
| Champion/talent matchup | A team result while the selected champion/talent faced an opposing champion/talent | The opponent, talent, queue, date selection and encounter count |
| Player trend | Retained observations contributing to the displayed history | The selected window and available historical coverage |

A player can contribute many performance observations while contributing only
one identity to a unique-player count. A single team match can also contribute
several champion-versus-opponent observations. These units answer different
questions; adding them together would lose their meaning.

The activity total uses a rolling previous 24 hours. Its queue counts overlap
when the same player appears in several queues. Our
[active-player methodology](https://paladinscat.com/blog/how-paladinscat-counts-active-players)
explains the counting and coverage rules in detail.

## Read the sample beside the win rate

Consider this hypothetical table:

| Selection | Wins | Recorded games | Win rate | After one additional loss |
|:---|---:|---:|---:|---:|
| A | 3 | 3 | 100% | 75% |
| B | 55 | 100 | 55% | About 54.5% |

Selection A won every recorded game in its small sample. Its percentage changes
sharply when one more result arrives. Selection B's percentage changes less
under the same addition. Sorting the original percentages puts A first, but
does not establish that A will perform better in your next game.

Keep both the percentage and its count in a comparison or screenshot. Narrow
filters can leave very few observations, especially for a specific talent and
opponent. There is no universal game count that makes a result certain. Repeated
players and similar match conditions can also remain in a larger sample.

## Match the population before comparing

Compare the same mode, date selection and metric. Ranked performance and casual
performance describe separate populations; casual performance comparisons use
the selected mode rather than treating every casual queue as interchangeable.

Use champion and role filters where the view offers them. Damage and healing
rates describe different responsibilities, and team composition can change the
opportunities a player has. A broad average is useful context, but it is not a
complete assessment of a particular player's decisions.

Record the window offered by the page. The activity card's rolling 24 hours
does not define every other statistic's window. A selectable historical range
also does not prove that every match within it was recorded. Daily and cumulative
player trends describe available indexed observations, so avoid calling them
complete lifetime history.

## Separate missing evidence from a recorded zero

An empty matchup cell means that the selected comparison has no available
result. Reading it as a 0% win rate would imply observed losses that the cell
does not establish.

Metric sample counts can differ too. In a hypothetical set of matches,
PaladinsCat might retain 100 damage-per-minute samples but only 80 weapon-damage
samples because 20 records lack an authoritative damage breakdown. Those 20
missing inputs do not demonstrate zero weapon damage. A recorded zero and an
unavailable value have different meanings.

Champion totals can also contain observations without a selected talent or
loadout. A difference between the champion total and the visible talent rows
does not by itself prove that a talent row is missing.

PaladinsCat preserves verified parts of Limited matches for inspection while
excluding those incomplete matches from ratings and champion/performance
aggregates. See
[Understanding Limited Matches](https://paladinscat.com/blog/when-match-recovery-stops)
for a concrete example of that boundary.

## Keep per-minute values and averages distinct

For a hypothetical damage comparison:

| Match | Damage | Duration | Damage per minute |
|:---|---:|---:|---:|
| A | 100,000 | 10 minutes | 10,000 |
| B | 100,000 | 20 minutes | 5,000 |

Both matches have the same damage total. Their per-minute rates differ because
the time available differs.

The average of these two match rates is 7,500. Dividing their combined 200,000
damage by their combined 30 minutes gives about 6,667. The first summary gives
each match equal weight; the second weights by duration. PaladinsCat's
per-match-average summaries preserve the former distinction. Do not reconstruct
an average from combined totals or average several displayed subgroup averages
unless you know the required weighting.

## Treat matchups and builds as observations

A champion/talent matchup reports team outcomes while facing the opponent. It
does not isolate a duel between those two champions. Other teammates, maps,
player experience and match circumstances can contribute to the observed result.

Likewise, a talent or loadout with a high recorded win rate may have been selected
by a different group of players or in different situations. The table alone
cannot show that choosing it caused the higher rate.

Use the results to shortlist questions: Does this selection have enough relevant
observations to inspect? Which situations might explain its performance? Does
it fit your role and team? Then examine the available match evidence alongside
the aggregate rather than treating a ranking as a guaranteed outcome.

## A checklist before sharing a conclusion

- State the page, mode and selected date window.
- Keep the sample count beside the rate or average.
- Identify whether the unit is players, matches or player-match values.
- Match champion, role and talent filters where available.
- Distinguish recorded zeroes from unavailable values.
- Describe the result as an observation of the selected data, with its coverage
  limits, rather than a universal prediction.

If a total or comparison appears inconsistent, use the
[PaladinsCat contact page](https://paladinscat.com/contact). Include the page URL,
selected filters, displayed window and the discrepancy you can reproduce. That
context helps distinguish a counting difference from a data or display problem.
