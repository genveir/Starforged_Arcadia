# The Document Store

Campaign material lives in two places. Project files (this document, the rules documents, house rules) are read-only and stable. Everything that changes during play lives in the document store, reached through the localMCP tools. The `localmcp-document-store` skill covers how to read, search and write the store; this document covers how Arcadia is laid out in it and the conventions for what goes where.

## Categories

`Arcadia` is the parent category and holds these leaf categories:

- **Arcadia.State.** `game-state.md`, `player-character.md` and `ship.md`.
- **Arcadia.Vows.** One document per open vow: its terms and its story. Written when a vow is sworn, when its story moves on, and archived when it is fulfilled or forsaken.
- **Arcadia.Tasks.** One document per open task: its terms and its story. Written when a task is made, when its story moves on, and archived when it is finished or cancelled.
- **Arcadia.People.** One document per NPC worth a record, connection or not, plus `unnamed-people.md` and a document for each group, such as a crew or a household.
- **Arcadia.Places.** One document per location established in play: a station, a settlement, a planet, a derelict. A place's parts (decks, districts, rooms) are `##` sections of its document. Each summary says where the place is as well as what it is, so the index reads as a map.
- **Arcadia.Setting.** The truths of the setting, factions, institutions, technology and anything else about how the setting works, one document per topic.
- **Arcadia.Races.** One document per alien race established in play: what they are like, how they live and govern themselves, and how they treat outsiders.
- **Arcadia.Oracles.** The Starforged oracle tables, one document per table, plus any the player has added. Not indexed, and split across 25 leaves; see Oracles below.
- **Arcadia.Sessions.** Narrative session summaries, one document per session, numbered `session_001.md`, `session_002.md`, and so on.
- **Arcadia.SessionNotes.** Rulings and anything else worth noting that is not part of the session's story, one document per session, numbered to match its summary: `notes_001.md` goes with `session_001.md`. Not indexed.

Search `Arcadia` when you do not know where something lives, and a leaf when you do.

## Oracles

`Arcadia.Oracles` is a parent of 25 leaf categories holding the Starforged oracle tables, one document per table, plus any the player has added. None are indexed, so `search_index` will not find them. All roll ranges are fully written out at width 2, e.g. "| 01, 02, 03 |", not "|1-3|", and "00" not "100". Use `find_text` with the leaf, the oracle filename and your roll (`11`, not `|11|`) to get just the row you need. To find a table, use `list_documents` on a leaf, or `find_text` on `Arcadia.Oracles`. The leaves are:

- **Core.** Action, Theme, Descriptor and Focus.
- **Characters**, **Creatures**, **Factions**, **Settlements**, **Starships**, **Space**, **Derelicts**, **Vaults** and **LocationThemes.** The tables for each kind of subject.
- **CharacterCreation** and **Misc.** Character creation prompts, and story complications, clues, anomaly effects and combat actions.
- **Moves.** The oracles used by moves, such as Ask the Oracle and Pay the Price.
- **Planets.General.** Planet class, peril and opportunity.
- **Planets.Desert**, **Planets.Furnace**, **Planets.Grave**, **Planets.Ice**, **Planets.Jovian**, **Planets.Jungle**, **Planets.Ocean**, **Planets.Rocky**, **Planets.Shattered**, **Planets.Tainted** and **Planets.Vital.** One leaf per planet class: atmosphere, settlements, observed from space, features and life.

A filename is the table's path within its leaf, joined with underscores: `Core/Action.md`, `Derelicts/Access_Feature.md`, `Planets.Desert/Settlements_Core.md`. Where a result points to another table it says so, as in "(see Factions/Legacy.md)". A line under a table headed "cannot be rolled on this table (choose only)" lists results that can be picked but not rolled. Tables the player adds go in their own leaf under `Arcadia.Oracles`, in the same format, not into the Starforged leaves.

## Sections

Anything edited on its own gets its own `##` section. In Arcadia that includes each person's entry in `unnamed-people.md`, each room or space in `ship.md`, and each clock in `game-state.md`.

## Session summaries

Session summaries are written to be searched. The `#` title is the session number and a short label for where the session took place or what it was about: `# Session 7: Refit at Kessel Drift`. Below the title, give each scene its own `##` section. A new scene starts when the character changes place, company or task. Search results label a chunk only with the title and its `##` header, so each header must make sense on its own and say what happened and who was there, for example `## Installing the galley stove with Teo` or `## Ambush in the debris field, the Varga crew`. Do not use `###` headers. Keep a scene to a few paragraphs, and split a longer one at a natural turn.

Note the moves and their outcomes briefly in the scene where they happened, in italics at the end of the paragraph: *(Face Danger +edge: weak hit, health 5 → 4.)*

Keep the summary to the story of the session. Rulings and anything else worth noting go in the session's notes document in `Arcadia.SessionNotes`, created with `add_document`, not indexed, with the same number and the same `#` title as the summary.

## Archiving

Archive finished vows and tasks with `archive_document`, once anything worth keeping is in the session summary. Archiving cannot be undone by you.

## Every fact has exactly one home

Do not copy a value into a second document.

- **game-state.md**: the character's current location and situation, active campaign clocks (one `##` section each), active threats, and open narrative threads.
- **player-character.md**: stats, condition meters, momentum, impacts, assets other than the command vehicle and its modules, legacy tracks and experience, satisfaction, skills, any pending +1 on the next action die roll, and personal gear. It holds progress as lists: vow progress (rank and ticks), task progress (boxes and ticks, with any carryover rates noted on the line), and connections (role, rank, progress, bonded or not). Progress lives here and nowhere else. Also backstory and character notes.
- **ship.md**: the command vehicle. Its name, its asset abilities, integrity, troubles (battered, cursed), the ship's supply track, modules and their status, and support vehicles. Then one `##` section per room or space aboard, recording what it is like now: the galley that finally works, the garden bay, the bunk with the terrible mattress. This is where the ship becoming a home is written down.
- **Vow documents**: rank, the vow as sworn, who it was sworn to, and the story so far. No progress. The summary says what the vow is and where it stands in one line.
- **Task documents**: urgency, complexity, boxes, carryover, any standing rulings, and the story so far. No ticks. The summary says what the task is and where it stands in one line.
- **People documents**: static facts only. Identity, role, where they are usually found, appearance and manner, and what has been established about them in play. No connection rank or progress. A person met but not yet worth a document has an entry in `unnamed-people.md`; when they earn one, give them their own and remove their entry with `delete_document_section`.
- **Group documents**: people who arrive and leave together, such as a crew, a household or a cell, share one document in `Arcadia.People`, named for the group, with one `##` section per named member and one for the group as a whole. A member who earns their own document gets one that points to the group document, and their section is removed from it. The group document is kept after the group leaves.
- **Place documents**: locations established at the table. Each place lives in one document only; another place's document may name it and point to it, but does not repeat its description. The ship is not a place document; it lives in `ship.md`.
- **Setting documents**: how the setting works, as established at the table. A faction document describes the faction, not the times the character dealt with it.
- **Race documents**: how an alien race lives, governs itself and treats outsiders, as established at the table. How a race acts in a particular sector goes in that sector's place document.
- **Session summaries**: narrative only. What happened, not where things stand.
