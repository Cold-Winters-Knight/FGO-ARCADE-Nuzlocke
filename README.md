# FGO Arcade Nuzlocke Banner Presets

Custom summon presets and house rules for a **Fate/Grand Order Arcade Nuzlocke-style campaign**.

For the challenge rules, see **[NUZLOCKE_RULES.md](NUZLOCKE_RULES.md)**.

## Installation — Scooby 1.1.2+

Copy **all ten raw `.json` preset files** from this folder directly into:

```text
Server\artemis\config\summon_presets\
```

If summon_presets does not exist, go ahead and create it.

After copying, that folder should contain:

```text
Server\artemis\config\summon_presets\
├─ 00_Fuyuki.json
├─ 01_Orleans.json
├─ 02_Septem.json
├─ 03_Okeanos.json
├─ 04_London.json
├─ 05_E_Pluribus_Unum.json
├─ 06_Lost_Jerusalem.json
├─ 07_Babylon.json
├─ 08_Lilim_Harlot.json
└─ MYSTERY_BOX.json
```

Then open Scooby's **Draw Rates** page and load whichever preset you want to use.

No renaming and no manual replacement of `fgo_summon_weights.json` is required when using Scooby 1.1.2+.

## Important: these are strict JSON files

The preset files intentionally contain **only valid JSON**.

Do not add inline comments such as:

```text
// Artoria Pendragon
```

Scooby's preset loader rejects `//` comments.

The format is:

```json
{
  "version": 1,
  "weights": {
    "6": 34286,
    "198": 1000
  }
}
```

The quoted number on the left is the **trading-card ID**.  
The integer on the right is the card's **relative summon weight**.
The current total weight for each story banner is 1,000,000.
The mystery box is set to 1 weight for everything in it.

## Recommended campaign workflow

At the start of each Singularity:

1. Load `MYSTERY_BOX.json`.
2. Use the one Mystery Box summon granted by the rules.
3. Load the current Singularity banner, or any previously unlocked Singularity banner.
4. Spend or save your normal pull allowance according to `NUZLOCKE_RULES.md`.

## Banner rates

Each Story Banner uses:

| Result | Probability |
|---|---:|
| Servant | 18% |
| Craft Essence | 82% |

Servant rarity budget:

| Rarity | Probability |
|---|---:|
| 5★ | 4% |
| 4★ | 5% |
| 3★ | 4% |
| 2★ | 3% |
| 1★ | 2% |

Within a rarity bucket, story-relevant Servants receive **6× the individual weight** of secondary era/returning Servants.

Every Story Banner uses the same curated set of **100 normal, non-Fatal Craft Essences**:

| Rarity | CE count | Probability budget |
|---|---:|---:|
| 5★ | 35 | 12% |
| 4★ | 40 | 25% |
| 3★ | 25 | 45% |

## Story Banner pool sizes

| Banner | 5★ | 4★ | 3★ | 2★ | 1★ | Total Servants |
|---|---:|---:|---:|---:|---:|---:|
| Fuyuki | 2 | 8 | 4 | 4 | 2 | 20 |
| Orleans | 5 | 7 | 3 | 2 | 1 | 18 |
| Septem | 8 | 4 | 2 | 2 | 2 | 18 |
| Okeanos | 7 | 5 | 3 | 3 | 2 | 20 |
| London | 11 | 3 | 1 | 1 | 2 | 18 |
| E Pluribus Unum | 13 | 4 | 2 | 1 | 2 | 22 |
| Lost Jerusalem | 16 | 2 | 2 | 2 | 1 | 23 |
| Babylon | 17 | 2 | 2 | 1 | 1 | 23 |
| Lilim Harlot | 15 | 3 | 2 | 1 | 1 | 22 |

Pool size does not change the fixed rarity-rate budgets above.

## Mystery Box

`MYSTERY_BOX.json` is Servants-only.

| Rarity | Servants |
|---|---:|
| 5★ | 14 |
| 4★ | 7 |
| 3★ | 0 |
| 2★ | 0 |
| 1★ | 1 |
| **Total** | **22** |

Every eligible Mystery Box Servant has equal weight.

Duplicate protection, pull limits, permadeath, NP Tokens, Command Spells, and Digivolution are house rules and are not enforced by the JSON files.

## Important

These are **custom campaign probabilities**, not reconstructed retail FGO Arcade banners.
