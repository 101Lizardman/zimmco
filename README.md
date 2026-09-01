# ZimmCo Vending Unit — A Warden's Guide

A free, interactive 3D prop for **ZimmCo Refreshment Beverages**, a module for the [Mothership RPG](https://www.tuesdayknightgames.com) by Shane Vincent. Point your players at a live vending machine, let them push the buttons themselves, and let the tool handle the rolls, the state, and the consequences.

**Use it live:** https://101lizardman.github.io/zimmco/
**Get the module:** [ZimmCo Refreshment Beverages on itch.io](https://shanevincent.itch.io/zimmco-refreshment-beverages)

Works on any device with a browser — pass a laptop around the table, throw it up on a shared screen, or hand players a phone to poke at while you read the room.

---

## What this actually is

*ZimmCo Refreshment Beverages* is a short, drop-in module: a vending machine you can put in front of your players almost anywhere, dispensing cheap drinks with minor effects for 25C a can — with a pile of hidden alternate uses buried underneath, from a tucked-away toolkit to a machine you can hack, gut, or climb inside of.

This tool *is* that machine. It's not a summary or a reference sheet — it's the actual prop, built to be handed to your players. They click the coin slot, they pick a flavour, they can find (or already know, if you've told them) the tricks in the RUMORS table below and try them for real. Durability, stores, dice rolls, state changes, sound and lighting cues — the tool tracks and plays all of it out, so you're free to just run the scene.

Grab the full module — beverage tables, merch, and the complete rules this tool is built from — at the [itch.io page](https://shanevincent.itch.io/zimmco-refreshment-beverages).

---

## Rumors

**Between each downtime, the first time your players come across a ZimmCo vending machine, roll a d10 for a rumor.** It's a rumor — something they've heard, not something they necessarily believe or act on — but it's the hook that tells them a given machine can do more than dispense drinks. Feel free to hand out more than one over a campaign; nothing stops the same trick coming up twice, or a group hearing several rumors before they ever find a machine.

| d10 | Rumor | What it's hinting at |
|---|---|---|
| 0 | **TOOLS** — In exchange for a pack of cigarettes, an old shipwright told you how to find the little lever tucked away behind the panel of the coin slot… | The hidden latch beside the coin slot |
| 1 | **BUILT RIGHT** — While drinking heavily you are regaled of a time when someone once patched up their radiation shielding with panels from a ZimmCo vending machine… | Flavour only — no feature in this tool |
| 2 | **TERMINAL** — After catching that kid trying to spoof your ID chip, you learn that she got access to it from the vending machine — why is it even on the network? | The Terminal tile (password below) |
| 3 | **PROXIMITY SENSOR** — Junkers used to setup these bad boys as warning alarms for if any of the less community-minded individuals happened upon the same wreck… | The Proximity Sensor hotspot |
| 4 | **TRANSCEIVER** — A clone mentioned they had escaped their creators by smashing apart a ZimmCo vending machine and finding some sort of communicator inside… | The Transceiver tile (password below) |
| 5 | **SHELTER** — You'd heard this one a million times before — some Spacer in a tight spot wiggled their way inside the machine, sealed themselves in and drifted in space for weeks, but it simply can't be true… right? | The Shelter tile (password below) |
| 6 | **JUMP START** — Shorting the capacitor bank allows for a single, dangerous high voltage surge of power, but what's left behind is just a brick. | The Jump Start tile (password below) |
| 7 | **LIFESAVER** — When ZimmCo was in operation it wasn't yet forbidden to commercially use research chemicals — it's what gives Klassic flavour its unique taste. | Flavour + a module rule this tool doesn't automate (see itch.io) |
| 8 | **FIZZLER** — "Well I got ten 'er twelve cans, see? Taped 'em alllll up — like this! Then when there's no atmers'phere, pop a hole in one and FZZZZZ! Foam galore" | Flavour + a module rule this tool doesn't automate |
| 9 | **GOLDEN TICKET** — A closely guarded secret, often shared unwillingly, about a hidden Kombinat facility untouched by time… | Campaign hook — not a machine feature |

Rumors 1, 7, 8, and 9 are pure narrative colour (or point at rules this tool doesn't need to automate) — the full text and rules for all of them are in the module itself.

---

## Features, passwords, and their rumors

Some of the machine's alternate uses are things your players find by clicking around the model. Others are locked behind a password — **something you hand out yourself**, in character, whenever it fits the scene (a rumor above, a note on a body, an NPC who owes them a favour, whatever). Type it into the password field on the relevant tab and hit Enter.

| Feature | How it's triggered | Password | Rumor |
|---|---|---|---|
| **Vending** | Click the coin slot | — | — |
| **Tools** | Click the small latch beside the coin slot until it jams (15 clicks) | — | 0 – TOOLS |
| **Hack the Mainframe** | Click the exposed panel (5 clicks, or just 1 while in Lock Down) for an INTELLECT check | — | — |
| **Terminal** | Once **Hacked**, open the Hacked tab and enter the password | `matrix` | 2 – TERMINAL |
| **Crack It Open** | Strike either side panel (10 clicks, or just 1 in Lock Down) and enter the damage dealt — or, once **Hacked**, use the free tile in the Hacked tab | — | — |
| **Proximity Sensor** | Click the wiring point (10 clicks) for an INTELLECT check — only while *not* already in Lock Down | — | 3 – PROXIMITY SENSOR |
| **Transceiver** | Once **Opened**, open the Internals tab and enter the password | `bananaPhone` | 4 – TRANSCEIVER |
| **Shelter** | Once **Opened**, same tab, enter the password | `bunker` | 5 – SHELTER |
| **Jump Start** | Once **Opened**, same tab, enter the password | `defib` | 6 – JUMP START |
| **Extract Stores** | Once **Opened**, free tile in the Internals tab — empties whatever's left in the machine | — | *(not in the original module — a tool-only addition)* |

A couple of notes on how these actually play out in the tool:

- **Hack the Mainframe** and **Crack It Open** don't need a password — they're just something anyone can attempt by interacting with the machine directly. **Terminal**, **Transceiver**, **Shelter**, and **Jump Start** are the ones you gate behind knowledge, matching their rumors.
- **Terminal** requires the machine to already be **Hacked**; **Transceiver**, **Shelter**, **Jump Start**, and **Extract Stores** all require it to be **Opened** first (via Crack It Open, or Hacking it open without damage).
- **Shelter** additionally needs the machine to be **Hacked** *and* have 6+ Durability at the moment it's triggered — otherwise the attempt just fails outright with no cost. Succeeding disables Transceiver, Jump Start, Extract Stores, Terminal, and the Tools tab entirely (the player's sealed themselves in — nothing else on the machine is reachable anymore).
- There's also a **`hello`** password on the Hacked tab, unlocking a "hello world!" tile — a small easter egg with no mechanical effect, not tied to any rumor.

---

## Machine states

- **Operational** — normal. Vends drinks, everything else is available to attempt.
- **Opened** — the internals are exposed. The Internals tab appears (Transceiver / Shelter / Jump Start / Extract Stores live here); the machine can no longer vend.
- **Hacked** — sticky once achieved; doesn't clear on its own. The Hacked tab appears (Terminal, plus a free Crack It Open); vending still works.
- **Lock Down** — the machine bolts up: a fast red-blinking status light, the scene's key light turning red, and a repeating alarm sound. It can't vend. **Every action on the machine — any hotspot, any tile — makes players clear a ZAP! BODY save first** (success: "you're safe"; failure: 1 stress and 1 damage, straight out of the module's shock rule), and click-gated hotspots only need 1 click instead of their normal count while it's active — the ZAP save alone is punishing enough without also demanding the full click count.

Hacked and Opened are **sticky** — once true, they stay true even if the machine also drops into Lock Down. Don't be surprised if the Hacked or Internals tab is still sitting there after an alarm starts blaring; that's intentional; the machine can be more than one of these at once.

---

## Using it at the table

- **Vend** by clicking the coin slot on the front of the machine; pick a flavour from whatever the current unit's range actually stocks.
- **Drag to orbit, scroll to zoom** — let your players actually look the machine over for the hotspots.
- The **Drinks** tab (bottom-right) logs everything dispensed this session, with its effect, so nobody has to remember what they drank.
- **Tools**, **Hacked**, and **Internals** tabs only appear once they're actually relevant — nothing is spoiled by an empty tab sitting there from the start.
- The **speaker icon**, bottom-left, mutes/unmutes everything.
- If you want to jump straight to a state for a demo or a set-piece without grinding through the rolls, add `?admin=1` to the URL — a small panel appears, top-left, with buttons to force Operational / Opened / Hacked / Lock Down directly.
- **Getting a fresh machine**: simply reload the page — a brand new unit rolls fresh Durability and stores (this one's dead, there's always another one nearby). A full reload also clears the session's Drinks/Tools history and any passwords already used, so if you want a new unit *without* losing that log, use the `?classic` fallback view instead — it has an explicit **New Unit** button that rerolls the machine while leaving that history alone.

---

## Thanks & credits

- Module written by **Shane Vincent** — [ZimmCo Refreshment Beverages on itch.io](https://shanevincent.itch.io/zimmco-refreshment-beverages).
- Vending machine 3D model by [ZwiebelGames](https://sketchfab.com/3d-models/kiosk-machine-retro-horror-vending-automat-300c0c705eea4c0f9d510021c847646f) on Sketchfab.
- Sound effects by [Kyodon](https://pixabay.com/sound-effects/film-special-effects-vending-machine-action-61196/) on Pixabay.
- Built with [Claude](https://claude.com/claude-code).
- This product is based on the Mothership® Sci-Fi Horror Role Playing Game, published by Tuesday Knight Games, and is published under license. MOTHERSHIP® is a registered trademark of Tuesday Knight Games. All rights reserved. For additional information, visit [tuesdayknightgames.com](https://www.tuesdayknightgames.com) or contact contact@tuesdayknightgames.com.

Looking to run this locally, host your own copy, or add hotspots to the model? See [`DEVELOPMENT.md`](DEVELOPMENT.md).
