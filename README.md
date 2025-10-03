ReputeX‑Engine
A modular, AI‑driven reputation and language engine for dynamic, immersive storytelling scenarios. Built for AI Dungeon and compatible narrative platforms.

🚀 Features
🌐 Universal Reputation System (URS) Tracks global faction reputation based on player actions using tag‑based Lexicon parsing.

🧍 Personal Reputation Engine Dynamically adjusts interpersonal traits (Charmer, Honorable, Dominant, Submissive, Prankster, etc.) based on player dialogue and behavior.

🔍 Regex‑Driven Lexicons Advanced regular expressions detect player intent and emotional tone from natural language input.

🕛 World Clock Tracks world time in `YYYY‑MM‑DD HH:MM format`. Advances with player actions or dialogue.

🧩 Fully Modular Design Plug‑and‑play with custom scenarios. Configure world time, define factions, and set custom values for your world.

📖 Lore & Location System Context‑sensitive descriptions of locations, varying by speaker origin or perspective.

⚔️ Faction Definitions & Rivalries Each faction has emoji, rivalries, and rep bounds. Supports hidden/emergent factions.

📅 Event Framework

Daily Events: repeatable world flavor (e.g., sunrise, tavern closing).

Monthly Event Pool: random seasonal happenings.

Yearly Events: recurring festivals or one‑off historical beats.

Special Events: one‑time narrative milestones (first visits, discoveries).

Mini Events: repeatable side activities with rewards.

🎁 Reward Application System Mini‑events grant items, boosts, or reputation shifts via applyMiniEventReward.

⚖️ Reputation Categories & Event Mapping Categories (warlike, diplomatic, merciful, etc.) and event tags (HarvestFestival, TwilightMoon) drive faction‑specific reputation changes.

⚙️ Setup & Required Changes
1. Define Your Factions
In your Shared Library, create your world’s factions and set initial reputation values:

```
state.factions = {
  "HyruleRoyalFamily": 0,
  "GoronClan": 0,
  "ZoraDomain": 0,
  // Add more as needed
};
```
2. Set Up the World Clock
The engine expects a state.worldClock object:

```
state.worldClock = { year: 1454, month: 3, day: 27, hour: 7, minute: 0 };
```
3. Configure Lore & Locations
Expand the LORE object with descriptive text for each location and perspective.

4. Define Factions & Rivalries
Use FACTION_DEFS and FACTION_EMOJIS to set faction identities, rivals, and bounds.

5. Add Events
DAILY_EVENTS: recurring world flavor.

MONTHLY_EVENT_POOL: random seasonal events.

YEARLY_EVENTS: recurring or year‑specific anchors.

SPECIAL_EVENTS: one‑time milestones.

MINI_EVENTS: repeatable side activities with rewards.

6. Reputation Categories
Use REP_CATEGORY_CHANGES to define how factions react to archetypal behaviors (warlike, diplomatic, merciful, etc.).

7. Event → Faction Map
Use the map object to tie specific event tags (e.g., HarvestFestival) to faction reputation shifts.

8. Rewards
Extend applyMiniEventReward with new cases for your MINI_EVENTS. Always update state.message for player feedback.

🔄 Required File/Panes Structure
Typical AI Dungeon setup:

Shared Library: ReputeX Core, helper functions, Lexicons, shared state, factions, events.

Input Modifier: Parses player input, applies rep changes, advances time.

Context Modifier: Sets instructions, reputation summaries, optional clock info.

Output Modifier: Displays rep changes, event triggers, time status, NPC reactions.

🧩 Example: Quick Start
js
// In Shared Library
state.factions = { "HyruleRoyalFamily": 0, "GoronClan": 0 };
state.worldClock = { year: 1454, month: 1, day: 1, hour: 8, minute: 0 };
// ...import ReputeX helper functions...

// In Input Modifier
// ...use provided ReputeX input logic...

// In Output Modifier
// ...use provided ReputeX output logic...

// In Context Modifier
// ...set instructions and show summaries...
🙌 Credits
Lothens – Personal Reputation Tracker foundation

LewdLeah – Auto‑Cards call (Mini Language Engine system)

MillennialJesus – Core integration, modular architecture, system expansion

❓ Support
If you need help customizing or expanding ReputeX for your own scenario, contact `MillennialJesus` or `Lothens` on Discord.

💖 If you’ve enjoyed using the ReputeX Engine or found it helpful in your own projects, consider supporting my work on Ko‑fi: [https://ko-fi.com/millennialjesus](https://ko-fi.com/millennialjesus).  
Your support helps me keep building new features, refining the engine, and creating fresh scripts for the community. Thank you for being part of this journey!
