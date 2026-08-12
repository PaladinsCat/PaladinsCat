<p align="center">
  <a href="https://paladinscat.com/">
    <img src="assets/paladinscat.png" alt="PaladinsCat logo" width="120">
  </a>
</p>

# PaladinsCat

**Paladins: Comp Analytics Tool** — advanced statistics, or just meow.

PaladinsCat is a community analytics platform that brings Paladins player profiles, match histories, champion statistics, and account signals together in one place. It helps players inspect competitive activity through transparent, data-driven evidence while publishing technical investigations into game-data quality.

[**Visit PaladinsCat →**](https://paladinscat.com/)

## How it began

PaladinsCat began with an investigation into a long-standing API failure caused by skin IDs exceeding the signed 16-bit limit of `32,767`. Affected matches returned incomplete data, but an undocumented endpoint provided an alternative route to recover the player identities needed to reconstruct them. That discovery became the foundation of PaladinsCat's match-recovery system and the wider analytics platform.

[**Read the investigation →**](docs/blog/public-release/skin-id-overflow.md)

This repository contains PaladinsCat's public releases, technical investigations, and community-facing project material. The production source code and internal operations remain in separate private repositories.

© 2026 PaladinsCat. All rights reserved.
