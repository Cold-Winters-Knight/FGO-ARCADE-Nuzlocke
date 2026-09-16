# FGO Arcade Nuzlocke Ruleset and Gacha Banner Presets

A spoiler-safe set of custom summon-weight presets for a **Fate/Grand Order Arcade Nuzlocke-style campaign**.

The goal is not to recreate the original retail banners. These presets turn the Arcade story into a run where your roster develops through limited pulls, story/era-focused banners, a Mystery Box for otherwise awkward-to-place Servants, and a separate Nuzlocke ruleset built around permadeath, NP investment, Command Spells, and Digivolution.

For the actual challenge rules, see **[NUZLOCKE_RULESET_README.md](NUZLOCKE_RULESET_README.md)**.

> **Spoiler note:** The normal banner JSON files contain trading-card IDs and integer weights rather than Servant names. Opening or editing any separately labeled/commented reference copies may reveal banner contents.

## What is included

```text
FGOA_Nuzlocke_Banners/
├─ Story_Banners/
│  ├─ 00_Fuyuki.json
│  ├─ 01_Orleans.json
│  ├─ 02_Septem.json
│  ├─ 03_Okeanos.json
│  ├─ 04_London.json
│  ├─ 05_E_Pluribus_Unum.json
│  ├─ 06_Lost_Jerusalem.json
│  ├─ 07_Babylon.json
│  └─ 08_Lilim_Harlot.json
├─ MYSTERY_BOX.json
├─ README.md
└─ NUZLOCKE_RULES.md
```

## Requirements

These are **configuration presets only**. They do not contain the game, server, or card data.

They are intended for a working local FGO Arcade installation using Cloud23333/Artemis and **Scooby 1.1.2 or newer**, which supports named Draw Rate presets.

The presets use the same version-1 `tc_id -> integer weight` format as the active Artemis summon-weight configuration:

```json
{
  "version": 1,
  "weights": {
    "6": 100,
    "198": 50
  }
}
```

The numbers are **relative weights**. A card with weight `100` is twice as likely as a card with weight `50` within the same active table.

## Installing the banners with Scooby 1.1.2+

Scooby 1.1.2 added native **Draw Rate presets**, so manually replacing `fgo_summon_weights.json` is no longer necessary for normal use.

Copy the supplied banner JSON files into:

```text
Server\artemis\config\summon-presets\
```

For example:

```text
Server\artemis\config\summon-presets\
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

Then:

1. Open the **Scooby launcher**.
2. Open the **Draw Rates** table.
3. Choose the preset for the banner you want to use.
4. Load/apply that preset.
5. Summon normally in-game.
6. When you need a different Singularity banner or the Mystery Box, load the corresponding preset.

No renaming is required when using Scooby's preset system.

### Recommended Nuzlocke workflow

At the start of a Singularity:

1. Load `MYSTERY_BOX.json`.
2. Make the single Mystery Box summon allowed by the rules.
3. Load the current Singularity banner, or any previously unlocked Singularity banner.
4. Spend or save your normal pull allowance as described in `NUZLOCKE_RULES.md`.

Because each player runs their own local server/account, different players can use different presets and progression independently.

## Legacy manual method

If you are using an older Scooby build without Draw Rate presets, the banners still use the same underlying Artemis format.

Back up:

```text
Server\artemis\config\fgo_summon_weights.json
```

Then copy the banner you want into:

```text
Server\artemis\config\
```

and rename the copied file to:

```text
fgo_summon_weights.json
```

Do **not** replace or edit `summon_candidates.json` to use these presets.

Updating to Scooby 1.1.2+ is recommended because named Draw Rate presets remove the need for this manual hot-swap process.

## Story Banner design

Each Story Banner uses the same overall probability budget:

| Result | Probability |
|---|---:|
| Servant | 18% |
| Craft Essence | 82% |

This averages roughly **9 Servants per 50 pulls**.

### Servant rarity budget

| Rarity | Probability |
|---|---:|
| 5★ | 4% |
| 4★ | 5% |
| 3★ | 4% |
| 2★ | 3% |
| 1★ | 2% |

Within a rarity bucket, story-relevant Servants receive **6x the individual weight** of secondary era/returning Servants.

The intent is to let players headhunt characters connected to the current story beat without turning every later banner into one permanently expanding pool.

### Craft Essences

Every Story Banner uses the same curated set of **100 normal, non-Fatal CEs**:

| Rarity | CE count | Probability budget |
|---|---:|---:|
| 5★ | 35 | 12% |
| 4★ | 40 | 25% |
| 3★ | 25 | 45% |

Prize/commemorative clutter and CEs that are not useful for normal gameplay were heavily reduced so that the CE side of the banner still functions as equipment progression rather than filler.

## Story Banner pool sizes

These counts are intentionally spoiler-safe.

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

Pool size is **not** the same thing as rarity rate. The probability budgets above remain fixed even when a later banner contains more high-rarity Servants.

## Mystery Box

`MYSTERY_BOX.json` is a special **Servants-only** pool for otherwise-unassigned characters that do not have a clean home in the story/era banners.

Current spoiler-safe composition:

| Rarity | Servants |
|---|---:|
| 5★ | 14 |
| 4★ | 7 |
| 3★ | 0 |
| 2★ | 0 |
| 1★ | 1 |
| **Total** | **22** |

Every eligible Mystery Box Servant has equal weight in the JSON.

The **duplicate-proof rule is a house rule, not something the JSON can enforce**. If a player rolls a Mystery Servant they have previously received from the Mystery Box, discard that result and reroll.

See `NUZLOCKE_RULES.md` for Mystery Box progression, NP Tokens, and Digivolution.

## What the JSON files do not enforce

The banner files control only what can be drawn and the relative summon weights. They do **not** track or enforce:

- the 50-pull allowance;
- saved pulls;
- one Mystery Box pull per Singularity;
- duplicate protection for Mystery Box pulls;
- starter Servants;
- permadeath;
- NP Tokens;
- Command Spells;
- Digivolution;
- player-specific progression.

Those are challenge rules and must be tracked by the player.

Fixed story/first-clear reward cards are not inserted into these custom summon pools.

## Editing your own presets

Scooby's exported Draw Rate presets use the same structure as these files, so you can duplicate one of the supplied JSONs and edit its `weights` table to make your own banner.

Example:

```json
{
  "version": 1,
  "weights": {
    "6": 100,
    "198": 100,
    "236": 25
  }
}
```

In that example, cards `6` and `198` have equal probability, while card `236` has one quarter of their individual weight.

Only valid summonable trading-card IDs should be used. A missing card ID effectively has zero weight in an explicit preset.

## Important

These are **custom campaign probabilities**, not original FGO Arcade retail rates or reconstructed official banners.

The banner set is intended to create a particular challenge-run experience: limited resources, locally relevant story pools, meaningful duplicates, and enough randomness that two runs can develop very different rosters.
