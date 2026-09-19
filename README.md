# FGO Arcade Nuzlocke Banner Presets

Custom summon presets and house rules for a **Fate/Grand Order Arcade Nuzlocke-style campaign**.

For the challenge rules, see **[NUZLOCKE_RULES.md](NUZLOCKE_RULES.md)**.  
For the complete human-readable roster and exact drop-rate reference for every banner, see **[BANNER_DROP_RATES.md](BANNER_DROP_RATES.md)**.  
For exact Servant pools and per-Servant rates, see **[SERVANT_BANNER_ROSTERS.md](SERVANT_BANNER_ROSTERS.md)**.  
For the shared Craft Essence pool and exact CE rates, see **[CE_BANNER_ROSTER.md](CE_BANNER_ROSTER.md)**.  
For the English/Japanese CE name cross-reference, see **[CE_ENGLISH_NAME_MAP.md](CE_ENGLISH_NAME_MAP.md)**.  
For the full local Servant catalog and acquisition coverage audit, see **[SERVANT_ROSTER_COVERAGE.md](SERVANT_ROSTER_COVERAGE.md)**.

## Installation — Scooby 1.1.2+

Copy **all ten raw `.json` preset files** from this folder directly into:

```text
Server\artemis\config\summon_presets\
```

If `summon_presets` does not exist, create it manually.

Then open Scooby's **Draw Rates** page and load whichever preset you want to use. No renaming and no manual replacement of `fgo_summon_weights.json` is required when using Scooby 1.1.2+.

## Important: these are strict JSON files

The preset files intentionally contain **only valid JSON**. Do not add `//` comments to them; Scooby's preset loader rejects commented JSON.

The quoted number on the left is the **trading-card ID**. The integer on the right is the card's **relative summon weight**. Every Story Banner totals exactly **1,000,000** weight.

## Campaign summon workflow

1. At the start of each Singularity, load `MYSTERY_BOX.json` and use the one Mystery Box summon granted by the rules.
2. Load the current Singularity banner or any previously unlocked Singularity banner.
3. Complete a Story Node (all three required clears) to earn **1 Normal Pull** and spend it immediately.
4. You may then use the one Material Mission allowed between Story Nodes; completing it earns **1 Normal Pull**, which must also be spent immediately.
5. Normal Pulls **cannot be banked**. Previously unlocked banners remain legal choices for every earned pull.

## Story Banner rates

Each Story Banner keeps the same total result split:

| Result | Probability |
|---|---:|
| Servant | 18% |
| Craft Essence | 82% |

The Servant rarity budget is now intentionally skewed toward lower rarity Servants:

| Rarity | Probability per normal pull | Share of Servant hits |
|---|---:|---:|
| 5★ | 1.5% | 8.33% |
| 4★ | 3.0% | 16.67% |
| 3★ | 5.5% | 30.56% |
| 2★ | 5.0% | 27.78% |
| 1★ | 3.0% | 16.67% |
| **Any Servant** | **18.0%** | **100%** |

**75% of Servant results are now 1–3★.**

### Recurring low-rarity roster

Every normal, regular-category **1★, 2★, and 3★ Servant** is available on every Story Banner. Their rates are still chapter-sensitive:

- story/era-featured low-rarity Servants use the existing **6× featured weighting**;
- recurring background commons use the **1× baseline weighting**.

This allows NP levels on common Servants to grow naturally across the campaign without turning each chapter into an identical flat pool.

### Timeline Drift — Miyamoto Musashi

**Miyamoto Musashi (`tc_id 1465`) appears on every Story Banner at exactly 0.05% per pull.**

She does not receive the 6× chapter-featured multiplier. Her 0.05% comes out of the fixed 1.5% 5★ budget; it does not increase the overall Servant rate.

Alternate Musashi forms remain outside the normal banners for Digivolution.

## Craft Essences

Every Story Banner uses the same curated **100-card CE pool** and the same combined **82%** CE budget. The CE rarity distribution is now deliberately skewed toward common equipment:

| CE rarity | Probability per normal pull | Share of CE hits |
|---|---:|---:|
| 5★ | 8.0% | 9.76% |
| 4★ | 20.0% | 24.39% |
| 3★ | 54.0% | 65.85% |
| **Any CE** | **82.0%** | **100%** |

With 35 five-star, 40 four-star, and 25 three-star CEs in the shared pool, this gives approximately **0.2286% per 5★ CE**, exactly **0.5000% per 4★ CE**, and exactly **2.1600% per 3★ CE**.

The shared CE roster is documented in **[CE_BANNER_ROSTER.md](CE_BANNER_ROSTER.md)**. The human-readable CE documentation uses English-localized card names; preset IDs and weights are unchanged.

## Story Banner pool sizes

| Banner | 5★ | 4★ | 3★ | 2★ | 1★ | Total Servants |
|---|---:|---:|---:|---:|---:|---:|
| Fuyuki | 3 | 8 | 8 | 7 | 2 | 28 |
| Orleans | 6 | 7 | 8 | 7 | 2 | 30 |
| Septem | 9 | 4 | 8 | 7 | 2 | 30 |
| Okeanos | 8 | 5 | 8 | 7 | 2 | 30 |
| London | 12 | 3 | 8 | 7 | 2 | 32 |
| E Pluribus Unum | 13 | 4 | 8 | 7 | 2 | 34 |
| Lost Jerusalem | 16 | 2 | 8 | 7 | 2 | 35 |
| Babylon | 18 | 2 | 8 | 7 | 2 | 37 |
| Lilim Harlot | 16 | 3 | 8 | 7 | 2 | 36 |


Pool size does not change the fixed rarity-rate budgets above.

## Mystery Box

`MYSTERY_BOX.json` remains Servants-only and unchanged in this revision. Every eligible Mystery Box Servant has equal weight; duplicate protection is a house rule rather than something enforced by the JSON.

## Important

These are **custom campaign probabilities**, not reconstructed retail FGO Arcade banners.
