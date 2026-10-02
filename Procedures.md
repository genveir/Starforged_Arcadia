# Arcadia: Procedures

Procedures for rolling up sectors, planets, settlements and people. They draw on the Starforged oracles in `Arcadia.Oracles` but are not the book's procedures; where they differ, these win.

## General

**Rolling.** Every oracle roll is a `roll_dice` call with its own `purpose`, read as the d100. Where a procedure calls for a d6, read the action die. Find the row with `find_text` on the table's leaf and filename. Show each roll and the row it landed on, as with any other roll.

**Results are prompts.** Interpret every result in the light of what is already established. When a result contradicts an established fact, or makes no sense next to another result, pick a fitting row instead of rerolling, and say so.

**Roll only what play needs.** Each procedure is split into layers. Roll a layer when the character learns that much, not before. A planet the crew only sees from long range never gets its atmosphere rolled.

**Human or alien.** Outside human space, settlement, character and faction results are read as alien or mixed (see `House Rules.md` and `neighbouring-peoples.md`). The name tables are human; alien names come from the people's own setting document.

**Pauses.** Anything a procedure produces that falls on the worldbuilding pause list in `How To Run.md` is a draft until the player confirms it. That is always true of a new people, a sector's holder, and a person rolled at the full tier. Use placeholders until then.

## Regions

A sector's region says how firmly its local people hold it. It is not a distance from human space.

- **Core.** Someone's heartland. Dense settlement, traffic, patrols and defences. Rich and dangerous to raid.
- **Frontier.** Borderland. Held loosely, or contested between peoples. Settlements are fewer and more exposed.
- **Periphery.** Wild space. Nobody truly holds it. Few people, old ruins, and whatever lives out there.

Tables that vary by region have the region in their filename: `Space/Sighting_Core.md`, `Settlements/Population_Frontier.md`, `Planets.Ice/Settlements_Periphery.md`, and so on.

## Sector

**When the carrier arrives in a new sector, or the expedition gets hold of charts of one**, roll it up as follows.

1. **Region.** Usually this is already known: the company chose where to go. Otherwise decide it, or roll d100: 01–30 Core, 31–70 Frontier, 71–00 Periphery.
2. **Holder.** Who holds the sector.
   - Core: one people.
   - Frontier: d100. 01–50 held loosely by one people; 51–00 contested between two.
   - Periphery: d100. 01–70 nobody; 71–00 claimed by a people who do not enforce it.

   For each people involved, if any are already known, Ask the Oracle whether it is one of them (Likely if they border this sector, 50/50 otherwise). A new people is a pause.
3. **Chart name.** The human name on the expedition charts: `Space/Sector_Name_Prefix.md` plus `Space/Sector_Name_Suffix.md`. The locals' name for it comes when the holder is worked out.
4. **Where the carrier waits.** Pick a holding position in deep space, out of the way of the holder's traffic: empty space, a nebula, a debris field, the shadow of a dead star. Roll `Space/Stellar_Object.md` if the system's star matters.
5. **Charted locations.** What the charts, long-range surveys or local intelligence show. Core 4, Frontier 3, Periphery 2. For each, roll `Space/Sighting_<Region>.md` and follow its references:
   - Planet: the planet procedure, first layer only.
   - Settlement: the settlement procedure, first layer only.
   - Descriptor + Focus: `Core/Descriptor.md` and `Core/Focus.md`.
   - Starship, derelict, vault or creature: a one-line note from the relevant leaf's first-look table, if it has one, and nothing more until play reaches it.

   For each location, note whether the route from the carrier is charted (Set a Course) or not (Undertake an Expedition), and roughly how far it is. There is no map; these notes are the map.
6. **What makes it hard.** Roll `Core/Action.md` and `Core/Theme.md`, read as what makes this sector dangerous or difficult for a raiding crew right now. If it would make a good campaign clock, propose one.

More locations emerge in play, from the same Sighting table, as the crews range further.

**Record.** One document in `Arcadia.Places` for the sector, with a `##` section for the overview, the holder, the carrier's holding position, and each charted location. A location that gets developed in play gets its own place document, and the sector's section shrinks to a line pointing to it.

## Planet

**When a planet is sighted, charted or approached**, roll it up in layers.

**Layer 1: sighted.**

1. **Class.** `Planets.General/Class.md`.
2. **Chart name.** The sector's chart name and a numeral in order of charting, e.g. *Ashen Abyss 3*. A crew may give it a nickname that sticks; that becomes its name.

**Layer 2: in orbit.**

3. **Observed from space.** `Planets.<Class>/Observed_From_Space.md`, once or twice.
4. **Atmosphere.** `Planets.<Class>/Atmosphere.md`.
5. **Life.** `Planets.<Class>/Life.md`. This decides whether later perils and opportunities come from the lifebearing or the lifeless tables.
6. **Settlements.** `Planets.<Class>/Settlements_<Region>.md`. For each settlement, the settlement procedure, first layer.
7. **Prize.** What an expedition would want here. On a settled world, `Settlements/Projects.md` for what they make or keep. Otherwise `Core/Descriptor.md` and `Core/Focus.md`, read as something worth taking.

**Layer 3: planetside.**

8. **Feature.** `Planets.<Class>/Feature.md`, once per landing site that matters.
9. **Perils and opportunities.** Not rolled in advance. In play, use `Planets.General/Peril_Lifebearing.md` or `Peril_Lifeless.md`, and the matching opportunity table, as the moves call for them.

**Record.** A planet that only reached layer 1 is a line in its sector's document. From layer 2 it gets its own document in `Arcadia.Places`, whose summary names its sector.

## Settlement

**When a settlement is sighted or reached**, roll it up in layers. Read every result as alien or mixed outside human space.

**Layer 1: sighted.**

1. **Location.** `Settlements/Location.md`, unless it is already known.
2. **Population.** `Settlements/Population_<Region>.md`.

**Layer 2: approach and contact.**

3. **First look.** `Settlements/First_Look.md`, once or twice.
4. **Initial contact.** `Settlements/Initial_Contact.md`, when the crew makes contact.
5. **Authority.** `Settlements/Authority.md`.
6. **Projects.** `Settlements/Projects.md`, once or twice.

**Layer 3: when it matters.**

7. **Trouble.** `Settlements/Trouble.md`, when the crew learns what is wrong there.

**Name.** From the people who live there. Until they are worked out, a placeholder from the chart: *the orbital at Ashen Abyss 3*.

**Record.** As a section of its planet's or sector's document until it is developed in play, then its own document in `Arcadia.Places`.

## People

**When the character meets someone new**, roll them up at one of two tiers.

**Quick tier**, for anyone who is unlikely to recur. No pause.

1. **First look.** `Characters/First_Look.md`, once or twice.
2. **Disposition.** `Characters/Disposition.md`. See the note below for aliens meeting humans.
3. **Name.** If they need one: for humans, `Characters/Name_Given_Name.md` and `Characters/Name_Family_Name.md`, or `Characters/Name_Callsign.md` for a spacer; for aliens, from their people's naming note, or a descriptive placeholder until there is one.

**Full tier**, for anyone named, given a role or likely to recur. This is a pause: the results are a draft until confirmed.

4. Everything in the quick tier.
5. **Role.** `Characters/Role.md`.
6. **Goal.** `Characters/Goal.md`.
7. **Revealed aspect.** Not rolled at first meeting. Roll `Characters/Revealed_Aspect.md` when the character comes to know them better: through Develop Your Relationship, a profound moment, or Gather Information about them.

**Disposition toward humans.** Humanity is distrusted by everyone. When an alien meets a human crew and nothing has changed their view, roll Disposition twice and take the higher number; the table runs from helpful at the low end to hostile at the high end. Once something has changed their view, roll once, or decide.

**Record.** Quick tier: an entry in `unnamed-people.md`. Full tier, once confirmed: their own document in `Arcadia.People`.
