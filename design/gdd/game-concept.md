# Game Concept: Brainrot Survivors

*Created: 2026-05-14*
*Status: Approved*

---

## Elevator Pitch

> A 3D auto-battler on Roblox where you survive waves of internet-culture enemies
> by assembling an increasingly absurd build of meme weapons — your personal-best
> timer is always visible, your friends can see your records, and every run is a
> chance to discover a broken combination nobody has tried before.

---

## Core Identity

| Aspect | Detail |
| ---- | ---- |
| **Genre** | 3D Survivors-like / Auto-battler / Roguelite |
| **Platform** | Roblox (Roblox Studio + Luau) |
| **Target Audience** | Optimizer-achievers aged 15–24 on Roblox |
| **Player Count** | Single-player match (shared lobby, async competition via leaderboard) |
| **Session Length** | 8–10 minutes per match |
| **Monetization** | Free-to-play; earn Braincells currency in-match; spend in lobby on cosmetics and characters. No pay-to-win. No paid gacha in MVP. |
| **Estimated Scope** | Medium (3–4 months MVP; 5–7 months to v1.0, team of 2–3) |
| **Comparable Titles** | Vampire Survivors, Megabonk, Blox Fruits |

---

## Core Fantasy

You are not just surviving — you are becoming a catastrophe.

Every upgrade card you pick is another layer of internet absurdity attached to your
character. By minute 7, you are surrounded by orbiting meme-orbs, firing a comment
cannon in three directions, leaving a shockwave trail from your Tralalelo Sneakers,
and the screen is barely readable — but *you* know exactly what's happening. You
built this. You made the choices that turned you into this. And somewhere on the
leaderboard, your time is better than it was yesterday.

The game delivers two simultaneous fantasies:
1. **The Chaos Fantasy** — watching your build become an unhinged spectacle
2. **The Optimizer Fantasy** — knowing the chaos is the direct result of smart
   build decisions you made under pressure

---

## Unique Hook

Like Vampire Survivors, AND ALSO every weapon is a collectible internet-culture
artifact with a fragment-evolution mechanic, AND ALSO every session is a live
competition against your own personal bests and your friends' records on a
persistent leaderboard.

The hook creates a second reason to play beyond "try to survive longer":
you are always chasing a number, and the number is always visible.

---

## Visual Identity Anchor

**Direction: Meme Chaos Readable**

*One-line rule:* Everything can be ridiculous, but nothing can be unreadable.

**Supporting visual principles:**
1. **Silhouette clarity over detail** — every enemy type has a distinct shape readable
   at a glance even when 50+ are on screen. Enemies are differentiated by size and
   silhouette, not texture or label.
   *Design test:* If you can tell what an enemy does by its shape in a 64×64 thumbnail,
   it passes. If you need to see the texture, it fails.

2. **Color = function** — enemy roles are color-coded (fast = yellow, tanky = red,
   ranged = blue, explosive = orange). Weapon effects use a distinct palette from
   enemy colors so the player can always distinguish "mine" from "theirs."
   *Design test:* Screenshot the game in grayscale. If all elements blend together,
   the color system failed.

3. **Density with depth** — the screen should feel packed but layered. Background
   effects (glow, particles) are low-opacity; foreground effects (weapon attacks,
   damage numbers) are high-opacity. The player's character is always the
   highest-contrast object on screen.
   *Design test:* A new player watching for 5 seconds should immediately know
   where the player character is.

**Color philosophy:** Bright, saturated primaries for enemies and weapons. Desaturated,
dark-toned arena floor and walls. The arena is the stage; the characters are the show.
No realistic lighting — flat or toon-shaded only.

---

## Player Experience Analysis (MDA Framework)

### Target Aesthetics (What the player FEELS)

| Aesthetic | Priority | How We Deliver It |
| ---- | ---- | ---- |
| **Sensation** (sensory pleasure) | 1 | Momentum-based movement, screen-filling effects, audio feedback on kills |
| **Challenge** (mastery) | 2 | Build optimization, record-chasing, increasing enemy density |
| **Discovery** (secrets, systems) | 3 | Fragment weapon evolutions, rare Brainrot cards, hidden synergies |
| **Expression** (self-expression) | 4 | Distinct build archetypes, cosmetics, character identity |
| **Fellowship** (social) | 5 | Async leaderboard competition, friends' records visible |
| **Fantasy** (make-believe) | 6 | Player-as-internet-catastrophe narrative |
| **Narrative** (story arc) | N/A | Not a story game |
| **Submission** (relaxation) | N/A | Not designed for low-stress play |

### Key Dynamics (Emergent player behaviors)

- Players will experiment with weapon combos to discover synergies, then repeat
  the best run to test if they can execute it faster
- Players will compete with friends' records without being prompted — the visible
  leaderboard creates ambient competition
- Players will screenshot rare Brainrot card combinations and share them on social
  platforms, driving organic discovery
- Players will develop preferred "build archetypes" (speed-based, area-damage,
  summon-heavy) and optimize within those archetypes over many runs

### Core Mechanics (Systems we build)

1. **Movement system** — slippery, momentum-based movement with dash/directional
   input. Skill lives in positioning and horde-funneling, not precision platforming.
2. **Auto-attack system** — weapons fire automatically based on targeting rules
   (nearest enemy, lowest HP, random spread, area). Player never manually fires.
3. **XP → Level → Card pick loop** — enemies drop XP orbs; collecting them levels
   the player; leveling triggers a pause showing 3 upgrade cards (weapon add,
   weapon upgrade, passive modifier, or rare Brainrot card).
4. **Fragment evolution system** — certain weapons spawn collectible fragments on
   the arena. Collecting all fragments of a weapon mid-run triggers its evolved
   form, which has different behavior and visual. (v1.0+, not in MVP)
5. **Leaderboard + record system** — every completed match records survival time,
   enemies killed, and damage output against personal bests and friends' records.
   The current run's pace vs. personal best is displayed during play.

---

## Player Motivation Profile

### Primary Psychological Needs Served

| Need | How This Game Satisfies It | Strength |
| ---- | ---- | ---- |
| **Autonomy** (freedom, meaningful choice) | Three cards every level, hundreds of build paths, no mandatory route | Core |
| **Competence** (mastery, skill growth) | Records prove improvement numerically; build theory rewards study | Core |
| **Relatedness** (connection, belonging) | Friends' records visible in lobby; shared build discoveries on social | Supporting |

### Player Type Appeal (Bartle Taxonomy)

- [x] **Achievers** — Records, personal bests, rare card collection, boss kills
- [x] **Explorers** — Fragment evolution discovery, hidden synergies, rare card mechanics
- [ ] **Socializers** — Secondary (leaderboard competition, not co-op)
- [x] **Killers/Competitors** — Leaderboard, time records, damage numbers

### Flow State Design

- **Onboarding curve**: First match is forgiving — low enemy density, frequent
  level-ups, common cards only. The game is fully legible within 90 seconds.
  No tutorial text: mechanics are discovered through play.
- **Difficulty scaling**: Enemy density increases logarithmically. Wave composition
  shifts from monoculture (early) to mixed behavior types (mid) to high-threat
  combinations (late). The final boss is a skill check that the player should
  feel genuinely challenged by.
- **Feedback clarity**: Kill count, damage numbers, current level, and
  personal-best delta are always visible on HUD. The player always knows they
  are ahead of or behind their best time.
- **Recovery from failure**: Death sends the player immediately to the post-match
  screen with their stats and earned Braincells. Re-queuing is one button press.
  No loading screens between runs in MVP.

---

## Core Loop

### Moment-to-Moment (30 seconds)
The player moves through the arena (slippery, momentum-based — sliding around
enemy clusters, not through them). Weapons fire automatically. XP orbs drop from
kills and drift slowly toward the player; the player steers toward dense clusters
to vacuum them. The 30-second loop is: **move → survive → collect → move**.
Every 20–40 seconds an XP threshold is hit → level up → card pick (3–5 second pause).

### Short-Term (5–10 minutes)
Level-ups come quickly in the first 2 minutes (levels 1–8), then slow as
the XP curve steepens. By level 6 the player has 2–3 weapons and a passive
or two — the build identity is forming. At the 4-minute mark a mid-boss
enemy spawns: killing it drops a bonus card draw. The "clicking moment"
(when the build starts obviously working) hits around minutes 4–5. From
this point the player is optimizing positioning to keep the build fed.

### Session-Level (one match + lobby)
A full match is 8–10 minutes. Survival until the final boss → boss kill (or
death) → post-match screen: time, damage, enemies killed, Braincells earned,
and position vs. personal best and friends' records. The hook that brings
the next session is: "I could beat that time if I'd taken the second option
on level 7." One button re-queues. Total lobby-to-lobby session: 10–12 minutes.

### Long-Term Progression
Braincells earned from matches are spent in the lobby on:
- New characters (each has a different starting weapon and passive)
- Cosmetic skins for existing characters
- Emotes, trails, pet companions (visual only)
- "Starter bonuses" (small quality-of-life boosts, not power advantages)

Records are tracked per-character and globally. The long-term goal is
the global leaderboard and the personal collection of characters and cosmetics.
The game is "done" when you've topped your personal record for every character
and collected all rare cosmetics — but new content (weapons, characters, seasonal
events) extends this indefinitely.

### Retention Hooks
- **Curiosity**: New cards appear rarely; fragment evolutions unlock entirely
  different weapon behaviors. Players return to see what they haven't found yet.
- **Investment**: Braincells accumulate; records are persistent. Progress is not
  lost between sessions.
- **Social**: Friends' records are visible on the lobby screen. Silent ambient
  competition ("They beat my time. I need another run.").
- **Mastery**: The personal-best delta shown during play makes improvement
  viscerally visible. Beating your record produces a clear in-game celebration.

---

## Game Pillars

### Pillar 1: Every Second Is Readable
In the visual chaos, the player always knows what's killing them and what's
saving them. Spectacle serves legibility, not the other way around.

*Design test*: If we're debating a flashier weapon effect vs. a more readable
one, this pillar says choose the readable one.

### Pillar 2: Build Smarter, Not Harder
Mechanical skill matters, but a well-designed build always punches above raw
reaction speed. An optimizer who thinks about synergies should outperform a
reflexes-only player in equal time.

*Design test*: If we're debating whether a mechanic rewards optimization or
just reflexes, choose optimization.

### Pillar 3: Chaos Has a Punchline
Every enemy, weapon, and effect should be legible as a joke — the game is
maximally absurd but intentionally so. "Ridiculous" is not an accident; it
is the design.

*Design test*: If we're debating a weapon name or visual, choose the one that
makes the player laugh out loud and roll their eyes simultaneously.

### Pillar 4: The Record Is Always in View
Players always know their current pace vs. personal best. The competitive layer
is ambient and constant — not a mode you opt into.

*Design test*: If we're debating whether to surface a stat or hide it during
play, surface it.

### Pillar 5: A Run Is Never Wasted
Even a death at minute 2 produces: Braincells earned, a card seen for the
first time, a new idea for the next run. No run is a loss.

*Design test*: If we're debating whether a mechanic punishes failure or
rewards persistence, reward persistence.

### Anti-Pillars (What This Game Is NOT)

- **NOT a precision platformer**: Movement is a positioning tool, not a skill
  test. No death pits, precision jumps, or platform puzzles. These would
  break flow and contradict the "chaos" fantasy.
- **NOT a story game**: There is no narrative to follow. No cutscenes, dialogue
  trees, or lore-gated progression. Brainrot lore is atmosphere, not content.
- **NOT pay-to-win**: Match power comes from in-match build choices only. Robux
  buys cosmetics, never stats or weapon unlocks. This is non-negotiable.
- **NOT a slow burn**: Matches must feel explosive within 30 seconds. No
  "ramping up" phase longer than one minute.

---

## Inspiration and References

| Reference | What We Take From It | What We Do Differently | Why It Matters |
| ---- | ---- | ---- | ---- |
| Vampire Survivors | Auto-attack loop, XP → level → card pick, wave escalation | 3D arena, momentum movement, fragment evolution, leaderboard | Proves the core loop is fun at scale (30M+ copies) |
| Megabonk | Momentum-based 3D movement, arena layout, record-chasing psychology, chest unlocks | Auto-combat instead of manual, meme theme, Roblox platform | Proves the movement feel and record psychology work |
| Blox Fruits | Deep Roblox build variety, rare unlocks driving long-term engagement | Auto-battler format, meme aesthetics, shorter session length | Proves Roblox audience pays for build depth and rarity |
| Dota 2 (Crownfall) | Proximate goals with meaningful unlock rewards, completionist arcs | Not a MOBA; the mechanism is the card pick, not hero picks | Validates that optimizer-achievers will grind hard for the right reward |
| Genshin Impact | Gacha pull excitement, rare discovery, character collection | No paid gacha; rarity comes from gameplay drops and card odds | Proves the psychology works; we achieve it through gameplay, not payment |

**Non-game inspirations**: Internet meme culture (Tralalelo Tralala, Skibidi Toilet,
NPC TikTok), brainrot video aesthetic (overlapping stimuli, loud transitions, no pause),
anime upgrade sequences (power-up visual language), PS1-era low-poly aesthetic (readable
shapes, no texture complexity).

---

## Target Player Profile

| Attribute | Detail |
| ---- | ---- |
| **Age range** | 15–24 primary; 13–14 secondary |
| **Gaming experience** | Mid-core to hardcore; has played build-crafting games |
| **Time availability** | 20–40 minute sessions; plays in bursts |
| **Platform preference** | Roblox (PC or mobile); also plays Steam games |
| **Current games they play** | Blox Fruits, Pet Simulator X, Vampire Survivors, Genshin Impact |
| **What they're looking for** | A build-crafting game with short sessions, competitive edge, and meme identity |
| **What would turn them away** | Pay-to-win mechanics; poor performance (lag with enemies); unreadable visual chaos; no sense of progress |

---

## Technical Considerations

| Consideration | Assessment |
| ---- | ---- |
| **Engine** | Roblox Studio + Luau. Not a choice — platform mandate. |
| **Key Technical Challenges** | Server-client split (Roblox RemoteEvents pattern); enemy performance at scale (50–100 entities); DataStoreService for persistent records; object pooling from day one |
| **Art Style** | Low-poly / PS1-inspired / toon-shaded. No PBR materials. Silhouette-first design. |
| **Art Pipeline Complexity** | Low-Medium — Roblox asset ecosystem provides a baseline; custom models for characters, weapons, and enemies |
| **Audio Needs** | Moderate — short sound effects for kills, level-ups, card picks, and boss phases. Looping background track per arena. No adaptive audio in MVP. |
| **Networking** | Roblox client-server model. Damage and enemy state computed on server; visual effects spawned on client. Leaderboard via DataStoreService. |
| **Content Volume (MVP)** | 1 arena, 1 character, 5 weapons, 15 upgrade cards, 5 enemy types, 1 boss, ~8–10 minute match length |
| **Procedural Systems** | Wave composition is procedural (enemy type ratios shift by time); upgrade card draws are weighted random. Arena layout is static in MVP. |

---

## Risks and Open Questions

### Design Risks
- **Build variety from 5 weapons may feel thin** — 5 weapons × 3 upgrade levels × 10 passive cards
  creates limited combinatorial space. Mitigation: ensure each weapon's upgrade path changes
  its targeting behavior, not just its damage number.
- **Record-chasing may not hook casual players** — players who don't care about leaderboards
  need a reason to return. Mitigation: Braincells meta-progression gives a secondary loop that
  doesn't require competitive motivation.
- **Chaos overwhelms readability before minute 5** — late-game builds produce so many
  simultaneous effects that pillar 1 breaks. Mitigation: establish visual budget rules
  (max N simultaneous particle emitters per weapon) from the start.

### Technical Risks
- **Enemy performance at scale** — 80+ enemies with individual movement on a Roblox server
  will lag without careful architecture. Object pooling and simple vector-to-player movement
  (no pathfinding) must be built in from day one, not retrofitted.
- **Roblox learning curve for first-time developers** — Roblox Studio's server/client model,
  RemoteEvents, DataStoreService, and anti-exploit patterns are specific and non-obvious.
  Expect 3–4 weeks of platform learning before productive feature development.
- **DataStoreService rate limits** — persistent leaderboard and currency storage must be
  batched and debounced to avoid Roblox API throttling.

### Market Risks
- **No pure 3D survivors-like on Roblox at scale yet** — this validates the gap but also
  means no proven playbook. First-mover advantage exists but so does first-mover risk.
- **Meme content ages quickly** — specific meme references (Tralalelo, Skibidi) can
  feel dated within 6 months. Mitigation: design the weapon/enemy system to be easily
  updated; treat specific memes as skinnable content, not hardcoded identity.

### Scope Risks
- **Fragment/evolution system complexity** — this mechanic was deferred from MVP but adds
  significant implementation depth. Do not bring it into MVP scope under time pressure.
- **Leaderboard anti-exploit** — Roblox leaderboards are exploitable. Server-authoritative
  stat tracking is required from day one. Adding anti-cheat to a shipped game is much harder.

### Open Questions
- **Does the movement feel work on Roblox physics?** — The slippery momentum feel from
  Megabonk requires careful Roblox physics tuning. Prototype this in week 1 before anything else.
- **What's the right card draw frequency?** — Too frequent = no tension; too rare = slow.
  Needs playtesting in the prototype phase. Starting hypothesis: level-up every 40–60 kills.
- **Can 5 weapons sustain 10 runs before feeling repetitive?** — Prototype test: play 10 runs
  with 5 weapons and count how many feel meaningfully different. If fewer than 7, add 2 more
  weapons before shipping MVP.

---

## MVP Definition

**Core hypothesis**: Players find the auto-battler build loop engaging for complete
8–10 minute sessions on Roblox, and return for a second run within the same session.

**Required for MVP**:
1. Movement system — slippery momentum, dash, arena boundaries
2. 5 weapons (3 common, 2 rare) with 3 upgrade levels each via card picks
3. 15 upgrade cards (weapon upgrades + 5 passive modifiers)
4. 5 enemy types with distinct behaviors (rusher, tank, fast, ranged, exploder)
5. XP orb system — collect → level up → card pick pause
6. Final boss at 8 minutes with distinct attack patterns
7. Post-match screen: time, kills, damage, Braincells earned
8. Personal best comparison on post-match screen
9. Braincells currency earned per match (lobby shop deferred to v1.0)
10. Basic leaderboard (top 10 scores, persistent via DataStoreService)

**Explicitly NOT in MVP**:
- Fragment/incomplete weapon evolution system
- Multiple characters (1 character only)
- Lobby shop / Braincells spending
- Friends' records comparison (global leaderboard only)
- Multiple arenas
- Cosmetics
- Co-op or multiplayer match modes

### Scope Tiers

| Tier | Content | Features | Timeline |
| ---- | ---- | ---- | ---- |
| **MVP** | 1 arena, 1 character, 5 weapons, 15 cards, 5 enemy types, 1 boss | Core loop, XP system, card picks, leaderboard, personal best | 3–4 months (team of 2–3, learning platform) |
| **v1.0** | 2–3 characters, 10+ weapons, lobby shop | Fragment evolution, Braincells shop, cosmetics, friends' records | +2–3 months |
| **Full Vision** | 4+ arenas, 30+ weapons, seasonal events | Legendary card tier, rare boss drops, event items, additional characters | 6–9 months total |

---

## Next Steps

- [ ] Run `/setup-engine` — configure Roblox Studio + Luau as the engine in CLAUDE.md and populate the engine reference docs
- [ ] Run `/prototype movement-and-combat` — **first priority before any GDDs**. The slippery momentum movement on Roblox physics must be validated before designing systems around it. Test: does the movement feel right? Can 50 enemies be rendered at acceptable performance?
- [ ] Run `/art-bible` — establish the Meme Chaos Readable visual identity before any asset production or system GDDs reference art
- [ ] Run `/map-systems` — decompose the concept into individual systems with dependencies (combat, XP, upgrades, enemies, meta-progression, leaderboard)
- [ ] Run `/design-system` for each system identified in `/map-systems`, in dependency order
- [ ] Run `/review-all-gdds` — cross-system consistency check
- [ ] Run `/gate-check` — validate readiness before architecture work
