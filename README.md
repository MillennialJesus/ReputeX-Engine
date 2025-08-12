ReputeX-Engine
A modular, AI-driven reputation and language engine for dynamic, immersive storytelling scenarios. Built for AI Dungeon and compatible narrative platforms.

🚀 Features

🌐 Universal Reputation System (URS):
Tracks global faction reputation based on player actions using tag-based Lexicon parsing.

🧍 Personal Reputation Engine:
Dynamically adjusts interpersonal traits (`Charmer`, `Honorable`, `Dominant`, `Submissive`, `Prankster`, etc.) based on player dialogue and behavior.

🔍 Regex-Driven Lexicons:
Advanced regular expressions detect player intent and emotional tone from natural language input.

🕛 World Clock:
Tracks world time in `YYYY-MM-DD HH:MM` format. Advances with player actions or dialogue.

🧩 Fully Modular Design:
Easy to integrate—plug and play with custom scenarios.
`You’ll still need to configure world time, define your factions, and set any custom values for your scenario!`

⚙️ Setup & Required Changes
To use ReputeX in your scenario, you MUST:

Define Your Factions

In your Shared Library pane, create your world’s factions and set initial reputation values for each:
``` js
state.factions = {
  "NCR": 0,
  "Legion": 0,
  "Boomers": 0,
  // Add more as needed
};
```
Set Up the World Clock

The engine expects a state.worldClock object:
``` js
state.worldClock = { year: 1454, month: 3, day: 27, hour: 7, minute: 0 };
```
You can set your own start date/time.

Customize Reputation Categories (Optional)

The Personal Reputation Engine supports traits like `Charmer`, `Honorable`, `Dominant`, etc.

If you want custom traits or unique behaviors, edit/add to the `PERSONAL_REP_PATTERNS` in the Shared Library.

Adjust Lexicon/Regex Patterns (Optional)

To match your scenario’s tone or add custom phrases, expand `PERSONAL_REP_PATTERNS` and/or the Lexicon.

Configure Faction Logic (Optional)

For special rules (e.g., mutually exclusive factions, unique win/loss conditions), update `canStartQuest`, `isHostile`, etc.

Import ALL ReputeX Helper Functions

IMPORTANT:
Place all core engine functions (`initWorldReputation`, `initPersonalReputation`, `getClockString`, `time-skip/advance helpers`, etc.) in your Shared Library pane.

If your scripting engine `does NOT` share functions between panes, copy necessary helpers into Input/Output Modifiers.

Integrate Output/Context/UI Formatting

You can use the included Output Modifier for reputation/status bars, time updates, and hybrid job notifications.

Adjust output formatting for your scenario’s style.

[OPTIONAL] Modular Extensions

Add `world events`, `milestone triggers`, `hybrid jobs`, or custom `NPC reactions` using your scenario’s needs.

For advanced features (AutoCards, etc.), follow extension documentation.
```
// === AutoCards (Input) ===
  text = AutoCards("input", text);  //<==🚨IF NOT USING AUTO-CARDS, REMOVE🚨!!
```
```
 // --- AutoCards for Context ---
  let stop = '';
  [text, stop] = AutoCards("context", text, stop);  //<== 🚨IF NOT USING AUTO-CARDS, REMOVE!!🚨
```
🔄 Required File/Panes Structure
Typical AI Dungeon scenario setup:

`Shared Library:
ReputeX Core, all helper functions, Lexicons, and shared state.`

`Input Modifier:
Parses player input, applies personal/faction rep changes, handles time advancement.`

`Context Modifier:
Sets up instructions, reputation summaries, and optional clock info.`

`Output Modifier:
Displays rep changes, hybrid unlocks, time status, and NPC reactions.`

🧩 Example: Quick Start
``` js
// In Shared Library
state.factions = { "NCR": 0, "Legion": 0 };
state.worldClock = { year: 1454, month: 1, day: 1, hour: 8, minute: 0 };
// ...import all ReputeX helper functions here...

// In Input Modifier
// ...use provided ReputeX input logic...

// In Output Modifier
// ...use provided ReputeX output logic...

// In Context Modifier
// ...set instructions and show summaries...
```
🙌 Credits

Lothens – Personal Reputation Tracker foundation

LewdLeah – Mini Language Engine (MLE) system (coming soon!)

MillennialJesus – Core integration, modular architecture, system expansion

❓ Support
If you need help customizing or expanding ReputeX for your own scenario, contact `MillennialJesus` or `Lothens` on Discord.



