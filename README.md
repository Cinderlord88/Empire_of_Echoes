  <img src="Empire of Echoes.png">

# Empire_of_Echoes
Scifi script using procedural generation as a reliability interface between AI narration and code


# Empire of Echoes

**A sci-fi exploration, survival, and salvage adventure where the story is told by AI—but the consequences are enforced by code.**

**Current release:** `v0.10.0-alpha.18` (ECO-01)  
**Status:** Playable alpha · Active development · **Not yet V1.0**  
**Platform:** [AI Dungeon](https://aidungeon.com/) · Four-tab Adventure Scripts (JavaScript)

---

## The premise

Humanity is running out of options. Far from a dying Earth, the corporate-controlled station **Azaheim** serves as a gateway to the ruins of a civilization nobody understands: the **Eirseid**.

You are a **Pathfinder**—one of the people desperate, brave, or foolish enough to board an ancient alien ship and venture toward forgotten worlds. Explore abandoned installations, confront hostile organisms, survive inexplicable hazards, and recover technology worth a fortune to **Cosmos Industries**.

Then try to bring it home.

**The expedition loop:**

`Prepare at Azaheim → Travel → Explore → Discover & collect salvage → Return → Sell → Upgrade → Go again`

The central tension is simple: **How much farther are you willing to go when every extra discovery could make you rich—or kill you?**

## What makes it different?

Empire of Echoes uses a **mechanical → procedural → narrative** design:

1. **JavaScript decides the rules:** location, travel, skill rolls, health, combat outcomes, inventory, credits, and other persistent facts.
2. **Procedural systems create the situation:** rooms, encounters, creatures, artifacts, threats, and consequences.
3. **AI Dungeon tells the story:** atmosphere, dialogue, discovery, and cinematic narration within the outcomes established by the scripts.

You don't need to roleplay through a command console. Write actions naturally:

> I duck behind the machinery and hide from the creature.  
> I fire my sidearm from cover.  
> I collect the Eirseid data crystals and carry them back to the ship.  
> I sell our salvage to Cosmos and buy a tool kit.

Explicit `#` commands remain available when precision is helpful. The design emphasizes **player agency**: the storyteller should not make major voluntary choices for your character.

## Features in the current alpha

| System | Current capability |
|---|---|
| **Expeditions & travel** | Azaheim departure, multi-day journeys, arrival, Site exploration, and return |
| **Procedural Sites** | Persistent room/connection structure, discoveries, hazards, and exploration results |
| **Character mechanics** | Attributes, skills, specialties, d20 checks, situational difficulty and injury penalties |
| **Health & medical care** | Persistent Wounds, injuries, treatment supplies, medical checks, and recovery support |
| **Combat** | Natural-language attacks, weapons, opposed rolls, persistent creature Wounds, death, fleeing, hiding, and concealed-attack bonuses |
| **Alien life** | Procedurally generated creatures, species registry, and encounter-activated species Story Cards |
| **Salvage** | Room-specific resources and artifacts, collection, backpack limits, ship storage, and persistent ownership |
| **Economy** | Artifact appraisal, crew-share payouts, credits, marketplace purchases, and a compact gear catalog |
| **Useful equipment** | Situational Advantage for applicable tools, including climbing kits, tool kits, and medical scanners |
| **Reliability** | Persistent save state, compatibility-oriented migration, and Retry/duplicate-transaction safeguards |

> **Alpha limitation:** Some combat features—including the autonomous Creature Director—are validated with debug-spawned creatures but **are not yet fully integrated into ordinary procedural Site encounters**. A number of catalog items are purchasable but do not yet have complete consumption or protection mechanics.

## Salvage, survival, and credits

Eirseid Sites are not just sightseeing destinations. Recovering valuable technology is the reason Pathfinders keep taking the risk.

- **Data crystals:** 50 credits each.
- **Alloy cubes:** 75 credits each.
- **Archaeological artifacts:** appraised on return; their value is hidden until assessed.
- **Scavenged finds:** tracked as actual objects, not merely rewards mentioned by the narrator.

Finding an item does **not** automatically put it in your inventory. You must collect it, carry it, and bring it home. Salvage may be stored aboard the ship, and successful sales credit your share of the proceeds. Items cannot legitimately be collected or sold twice.

At Azaheim, earnings can fund medical supplies and practical equipment for the next expedition. Gear is intended to matter mechanically: carrying the right tool can improve a relevant skill check, but does not grant a universal bonus to unrelated actions.

## Installation

1. Download the latest **Four-Tab Update** release package.
2. In your AI Dungeon scenario's script editor, replace the contents of **Library**, **Input**, **Context**, and **Output** with the four matching `.txt` files.
3. Keep the scenario's existing **AI Instructions**, **Plot Essentials**, opening character-creation variables, and Story Cards. The scripts complement these; they do not replace the setting.
4. Start or resume an adventure. Use `#COMMANDS` for the command reference or `#SHOP` at Azaheim to inspect the economy.

**Important:** Install **all four files from the same version**. Don't mix script tabs from different alpha releases. Existing saves are intended to remain compatible, but make a backup before updating an ongoing adventure.

### Useful commands

| Command | Purpose |
|---|---|
| `#COMMANDS` | Display available game commands |
| `#GEAR` | View equipped weapons and gear |
| `#INVENTORY` | View carried items and equipment |
| `#SALVAGE` | Inspect tracked salvage |
| `#COLLECT ALL` | Collect accessible salvage, within capacity |
| `#STOW ALL` | Deposit carried salvage while aboard the Site ship |
| `#SHOP` | Browse the Azaheim equipment catalog |
| `#BUY Tool Kit` | Purchase an item, if available and affordable |
| `#SELL ALL` | Sell eligible recovered salvage at Azaheim |
| `#CREDITS` | Check your money |
| `#MEDKIT` | Check medical supplies |

Natural-language alternatives are supported for common actions; commands are fallbacks, not the required play style.

## Project structure

The four Adventure Script tabs cooperate to maintain one consistent game state:

```text
Library.txt  — shared systems, tables, rules, and persistent-state helpers
Input.txt    — player-intent detection and authoritative action resolution
Context.txt  — mechanical and procedural guidance passed to the storyteller
Output.txt   — narration checks, presentation, and validated output handling
```

The distributed package uses versioned filenames such as `EmpireOfEchoes_v0.10.0-alpha.18_Library.txt`.

The development package also contains the automated test suite. To run it in an environment with Node.js and Bash:

```bash
bash Tests/run_all_tests.sh
```

**Latest development result:** 650/650 automated checks passed for alpha.18. Automated success does not mean every mechanic has been fully validated in live AI Dungeon play.

## Road to V1.0

The biggest remaining milestones are:

- Connect regular procedural Site encounters to persistent creature health, natural-language combat, and bounded autonomous behavior.
- Support carefully validated creative or environmental outcomes, such as defeating a creature by collapsing machinery onto it.
- Complete a live **Azaheim → expedition → Site → salvage → return → sale → upgrade** acceptance test, including save/resume and Retry cases.
- Review unfinished equipment behaviors and either implement or clearly restrict them for V1.0.

Longer-term possibilities include detailed armor and ammunition mechanics, oxygen consumption, equipment wear, station expenses and debt, and richer NPC economies.

## Inspiration & acknowledgments

**Empire of Echoes** is an unofficial fan-made AI Dungeon adaptation inspired by **_Across a Thousand Dead Worlds_**, designed by **Alex T.** and published by **Blackoath Entertainment**.

The project borrows and adapts gameplay concepts while developing its own scenario terminology, JavaScript systems, and presentation. It is **not affiliated with or endorsed by** Blackoath Entertainment or AI Dungeon. Original game text and artwork are not included in this README.

The underlying idea: **an AI-generated story with the memory, limits, and consequences of a real game.**
