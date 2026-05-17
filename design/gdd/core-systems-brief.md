# Brainrot Survivors Core Systems Brief

*Created: 2026-05-17*
*Purpose: Claude-facing design direction for enemies, weapons, mutations, items, chests, Braincells, classes, and the core game loop.*
*Status: Draft v1 for implementation planning*

---

## 1. Core Game Loop

Brainrot Survivors is a run-based Roblox survivors game.

The loop is:

```text
Lobby
-> choose class
-> choose mode
-> enter arena
-> survive brainrot waves
-> collect XP
-> level up and choose weapons/mutations
-> kill strong monsters for chest drops
-> kill boss for guaranteed chest/reward
-> finish or die
-> earn Braincells
-> return to lobby
-> unlock classes/cosmetics/items
-> run again
```

The main player fantasy is becoming an absurd but optimized internet-catastrophe build. Every run should create a clear build story: "I started as this class, found these weapons, mutated this way, got this chest item, then beat or failed the boss."

---

## 2. Enemy System

Enemies should be **brainrots**, not generic monsters.

They should feel like corrupted internet memes, but they must stay readable. Each enemy type needs:

- clear silhouette
- clear color role
- simple behavior
- recognizable joke/fantasy
- performance-safe Roblox implementation

### Enemy Tiers

| Tier | Purpose | Drop Behavior |
| --- | --- | --- |
| Normal Brainrot | Basic wave pressure | XP only |
| Fast Brainrot | Forces movement | XP only |
| Tank Brainrot | Slower, high HP wall | XP, small chance for chest if marked elite |
| Ranged Brainrot | Positional threat | XP only |
| Exploder Brainrot | Area danger | XP, no chest by default |
| Elite Brainrot | Strong monster variant | Chance to drop chest |
| Mini-Boss Brainrot | Mid-run spike | High chance to drop chest |
| Boss Brainrot | Run objective / phase fight | Guaranteed chest/reward |

### Enemy Feel

- Enemies should be slower than early prototypes but tougher.
- Early waves must be fair and readable.
- First wave target: very small count, enough to learn movement and weapons.
- Enemies should not physically shove each other into the player.
- Use software separation, pooling, and simple movement.

### Strong Monsters

Strong monsters are modified versions of existing enemies:

- larger size
- more HP
- stronger outline/aura
- slightly different name
- chest drop chance

Suggested strong monster labels:

- `Elite`
- `Glitched`
- `Overcooked`
- `Cursed`
- `Verified`
- `Sigma`

Example:

```text
Elite Tralalero Runner
- slower than normal fast enemy
- much higher HP
- drops a chest 15-25% of the time
```

---

## 3. Weapon System

Weapons are active auto-attacks. They are the most visible part of the build.

A weapon defines:

- attack pattern
- damage
- cooldown
- range
- target count / projectile count
- visual effect identity
- upgrade path
- rarity

Weapons can come from:

- class starting weapon
- level-up card choices
- chest rewards
- future rare boss unlocks

### Current Weapon Direction

| Weapon | Rarity | Role | Effect Identity |
| --- | --- | --- | --- |
| Comment Cannon+ | Common | reliable single-target damage | cyan beam / comment blast |
| Pixel Portal Blaster | Rare | high damage and range | purple portal pulse |
| Tralalelo Sneakers | Rare | speed and tempo weapon | green dash trail |
| Infinity Stone Fragment | Legendary | multi-target scaling | gold/purple snap burst |

### Weapon Slot Limit

Players can carry a **maximum of 4 weapons in hand** during a run. This is a hard cap.

Rationale:

- Forces real decisions between unlocking a new weapon and leveling an existing one
- Keeps the screen readable when 4 weapons fire VFX simultaneously
- Prevents the "everything-on" build where every weapon trivializes mid-game
- Matches the inventory panel slot count

Implementation rule:

```text
If weapons.length >= 4 and the level-up offer is a NEW weapon, that offer is suppressed.
Only weapon level-ups or new passives appear instead.
```

Classes with high-rarity starts (Mythic, Brainrot God) can pre-fill all 4 weapon slots; those runs trade the freedom of adding new weapons for a stronger early kit.

### Weapon Evolutions

A maxed weapon (Lv 5) **paired with a specific Mutation** auto-evolves into a "super-weapon" with transformed stats and VFX. This is the build-defining late-game moment — the player's run goes from "good build" to "absurd internet catastrophe."

Evolution rules:

- Trigger: weapon at max level AND required passive owned
- Effect: weapon is replaced in slot with evolved version; stats roughly multiply (dmg ×1.6, cd ×0.55, count/area ×1.3–2.0)
- Visual: inventory slot glows gold, icon shows ★, banner pops at evolution moment
- One-way: cannot un-evolve in a run
- Evolution slot does not consume an extra inventory slot (the original weapon transforms)

Prototype evolution table:

| Base Weapon | Required Mutation | Evolved Form |
| --- | --- | --- |
| Comment Cannon | Bussin Shard (crit) | Viral Comment Storm — 3 piercing bullets per shot |
| Glazer Beads | NPC Magnet | Cosmic Glaze Orbs — 2 extra orbs, on-hit splash AOE |
| Sigma Sweep | Glazing Boost (power) | Sigma Singularity — full 360° ring, never misses |
| Ohio Drop | W Artifact (bomb immunity) | Ohio Hellfire — half cooldown, faster fuse, +40% radius |
| Mewing Strike | Brainrot Boost (speed) | Looksmax Slash — double-wide arc, +40% range |

### Weapon Design Rule

Every weapon needs a readable punchline. The weapon should be funny in name, clear in function, and visually distinct in combat.

Bad weapon:

```text
Laser Gun: shoots laser, +damage.
```

Good weapon:

```text
Pixel Portal Blaster: opens tiny cursed portals that snipe enemies from weird angles.
```

---

## 4. Mutation System

Mutations are passive run modifiers. They are this game's version of tomes/passives, but more brainrot-themed.

Mutations do not replace weapons. They modify the whole build.

A mutation can affect:

- damage
- cooldown
- range
- XP gain
- extra targets
- player speed
- HP
- item drop chance
- chest reward quality
- weapon behavior

### Current Mutation Direction

| Mutation | Rarity | Role |
| --- | --- | --- |
| Hyper Scroll Mutation | Common | cooldown reduction |
| Big Brain Mutation | Common | range + damage |
| Viral Duplication | Epic | extra target per attack |
| XP Vacuum Mutation | Rare | more XP from kills |
| Gigachad HP Mutation | Common | max HP + heal |
| Long Arms Mutation | Rare | large range boost |

### Mutation Design Rule

Mutations should create build identity and decision pressure:

```text
Do I make my current weapon stronger, or do I mutate my whole build toward a future combo?
```

---

## 5. Item System

Items are chest rewards. They are different from weapons and mutations.

Weapons and mutations are mostly chosen from level-up cards. Items mostly come from gameplay drops: chests, strong monsters, bosses, events, and special objectives.

An item is a run artifact with a stronger "found treasure" feeling.

Items can be:

- run-only artifacts
- boss trophies
- equipment-style passive bonuses
- rare build enablers
- cosmetic unlock tickets
- Braincells bonus tokens

### Item Categories

| Category | Example | Function |
| --- | --- | --- |
| Damage Item | Cursed Keyboard Switch | +damage after every 50 kills |
| Defense Item | Lag Shield | brief damage immunity after getting hit |
| Economy Item | Braincell Receipt | bonus Braincells at run end |
| Chest Item | Lucky Loot Tab | higher chest quality chance |
| Boss Item | Crown of Failed Takes | trophy + run stat boost |
| Utility Item | Magnetized Comment Section | larger XP pickup radius |
| Build Item | Meme Algorithm Core | boosts weapons of the same theme |

### Item Design Rule

Items should feel like loot, not normal level-up stats. A chest should create a moment:

```text
"Wait, I found THAT? This run can become different now."
```

---

## 6. Chest Drop System

Chests are earned during runs. They are gameplay rewards, not paid gacha.

### Chest Sources

| Source | Drop Rule |
| --- | --- |
| Elite Brainrot | small chance to drop chest |
| Strong monster | moderate chance to drop chest |
| Mini-boss | high chance to drop chest |
| Boss | guaranteed chest/reward |
| Event objective | guaranteed special chest |

Suggested starting odds:

```text
Elite Brainrot: 15% chest chance
Strong monster: 25% chest chance
Mini-boss: 60% chest chance
Boss: 100% chest chance
```

### Chest Opening

Recommended MVP behavior:

```text
Chest drops on arena
-> player touches chest
-> game pauses or slows briefly
-> 3 item choices appear
-> player picks 1
-> item goes into inventory panel
```

This keeps the choice skill-based and avoids the feeling of paid gambling.

### Chest Reward Pool

Chest rewards can include:

- items
- rare weapon upgrades
- mutations
- Braincells tokens
- boss-only trophies
- cosmetic drop tickets

Boss chests should have better reward quality than normal chests.

### Boss Reward Rule

Bosses must always drop something meaningful. **Players should actively want to wait for the boss spawn timer.**

Minimum boss reward (every boss kill, no RNG on the floor):

```text
Loot pile dropped at boss death point:
  - 1 Sigma Vault chest (player-choice 3-option pick)
  - 2 W Chests (auto-grant on pickup: new weapon / passive / heal)
  - 1 Trophy item — boss-specific run-long passive buff
  - 8-12 coin burst (Fanum Tax)
  - 1 massive XP orb (worth 2x the boss XP value, often levels the player twice)
  - Big screen shake + particle burst + slow-mo flash on kill
```

Trophy design rule:

```text
Each boss drops a unique trophy with a permanent run-long buff:
  - Crown of Bombardiro  -> +25% all weapon damage
  - Crown of Ballerina   -> +30% move speed
  - Crown of Il Capo     -> +50 max HP + full heal

Trophies are one-of-a-kind per run. Player can never own two of the same crown.
```

Anticipation:

```text
HUD shows a "Next boss in X:XX" countdown so players plan their build around it.
When < 15 seconds remain, the countdown turns red and pulses.
When the boss is active, the HUD shows "Boss active — FIGHT BACK".
```

No boss kill should feel empty. **The boss is the run's center of gravity** — every other system feeds into "can you survive until the next boss, and can you actually kill them when they come?"

---

## 7. Braincells Currency

Braincells are the main meta-progression currency.

They are earned from:

- run completion
- kills
- boss kills
- personal record improvements
- chest drops
- daily rewards
- events
- duplicate class conversion

They are spent on:

- class capsules
- direct class unlocks if enabled
- cosmetics
- class skins
- weapon VFX skins
- aura colors
- emotes
- future event items

### Braincells Design Rule

Braincells should make every run feel useful, even failed runs.

Do not make Braincells the only thing that matters. They support the run loop; they do not replace it.

### Monetization Warning

If Braincells can be bought with Robux and spent on random class capsules, then class capsules become paid random items. Claude must use the policy rules in `design/economy/class-gacha-monetization-brief.md` before implementing this.

---

## 8. Class System

Classes are collectible pre-run identities.

A class defines:

- starting weapon
- starting passive
- class perk
- weakness/drawback
- visual icon/aura
- rarity

Classes can be unlocked through:

- class capsules
- direct Braincells unlocks
- achievements
- boss trophies
- events
- future Robux products, if policy-safe

### Class Balance Rule

Classes can give a strong start, but they should not automatically win the run.

Good class design:

```text
Legendary class starts with a special weapon but has a risky early-game weakness.
Common class is stable and easy to use.
Rare class has a sharper playstyle and clearer combo path.
```

Bad class design:

```text
Legendary class has more damage, more HP, more speed, and no downside.
```

### Class Roll at Run Start

Every run begins with a **class capsule pull**. The player sees their rolled class, may re-roll for free (within a run-start; cost applies for paid Braincells re-rolls in live), then confirms to enter the arena.

The rolled class fully determines the starting kit (weapons + passives) and the run's modifier mods (HP delta, speed mult, dmg mult, spawn rate mult, boss-time mult).

### Class Rarity Table (Prototype Spec)

Total odds sum to 100%. Within a rarity tier, weights split between classes.

| Rarity | Tier Odds | Class | Class Weight | Cumulative |
| --- | --- | --- | --- | --- |
| Common         | 70%     | Comment Warrior     | 50    | 1 in 2     |
| Common         |         | Mewing Master       | 20    | 1 in 5     |
| Rare           | 24%     | Tralalelo Runner    | 18    | 1 in ~5.5  |
| Rare           |         | Portal Kid          | 6     | 1 in ~16.7 |
| Epic           | 4%      | Cosmic Collector    | 4     | 1 in 25    |
| Legendary      | 1.5%    | Skibidi Sigma       | 1.5   | 1 in ~67   |
| Mythic         | 0.49%   | Brainrot Chosen     | 0.49  | 1 in ~204  |
| Brainrot God   | 0.01%   | Tralalero Tralala   | 0.01  | 1 in 10,000 |

**Design note on ultra-rares**: The original gacha brief (`design/economy/class-gacha-monetization-brief.md` §6) warns that 1-in-100,000 should be cosmetic-first to avoid whale-dominated meta. The Brainrot God class (Tralalero Tralala) is set at 1-in-10,000 instead — rare enough to feel mythological without being functionally unreachable for committed players.

### Class Power Rule — "Strong Start, Real Downside"

Every class above Common must have a clear, named weakness. The user-approved design directive is: **rarity scales BOTH start-strength AND drawback severity**. A Mythic-tier class should feel transformatively powerful AND meaningfully risky. No flat upgrades.

### Class Roster (Prototype Spec)

| Class | Rarity | Start Kit | Perk | Weakness |
| --- | --- | --- | --- | --- |
| Comment Warrior   | Common    | Comment Cannon                              | Reliable damage from frame 1                | No starting passive — raw run |
| Mewing Master     | Common    | Mewing Strike + Brainrot Boost              | Melee aggression + faster move              | Glass jaw: max HP 80 |
| Tralalelo Runner  | Rare      | Comment Cannon Lv 2 + Brainrot Boost        | Pre-leveled gun + speed                     | Took the kicks: max HP 75 |
| Portal Kid        | Rare      | Ohio Drop + NPC Magnet                      | Area bomb DPS + pickup range                | Heavy gear: -25% move speed |
| Cosmic Collector  | Epic      | Glazer Beads + Sigma Grindset               | Orbiting damage + +25% XP                   | Slow scaling: -30% weapon damage |
| Skibidi Sigma     | Legendary | Sigma Sweep + Glazing Boost                 | 360° aura + +15% all dmg                    | Enemies hate you: spawn rate +35% |
| Brainrot Chosen   | Mythic    | ALL 4 base weapons Lv 1 + Bussin Shard      | Full loadout from start                     | Frail vessel: max HP 50 |
| Tralalero Tralala | Brainrot God | Comment Cannon MAXED + 3 elite passives + 200 Fanum Tax | Pre-built late-game power | Boss timers HALVED — they're hunting you |

---

## 9. Inventory During A Run

The run inventory should show what the player picked.

Inventory includes:

- weapons
- mutations
- items
- boss trophies
- temporary run artifacts

The inventory is not the lobby collection. It is the current run's build history.

HUD inventory goals:

- small panel
- readable names/icons
- rarity color
- newest pick visible
- does not block combat

The inventory helps the player understand:

```text
"Why am I strong right now?"
"What did I pick this run?"
"What should I build around next?"
```

---

## 10. Implementation Notes For Claude

When implementing these systems:

1. Keep combat server-authoritative.
2. Keep visual effects client-side.
3. Use RemoteEvents for picked inventory updates.
4. Store current-run inventory separately from persistent player collection.
5. Chests should be physical arena objects or clear UI events.
6. Boss rewards should be guaranteed and visible.
7. Strong monster chest drops should be tunable in `Config`.
8. Use weighted random tables for chest quality, but keep paid random item policy separate.
9. Avoid adding too many systems at once. Implement in thin vertical slices:
   - strong monster flag
   - chest drop object
   - chest item picker
   - inventory update
   - boss guaranteed chest
   - Braincells payout

### Suggested Data Concepts

```text
EnemyDefinition
- id
- displayName
- tier
- health
- speed
- behavior
- chestDropChance
- braincellsValue

WeaponDefinition
- id
- displayName
- rarity
- effectId
- baseStats
- upgradeStats
- tags

MutationDefinition
- id
- displayName
- rarity
- statModifiers
- tags

ItemDefinition
- id
- displayName
- rarity
- source
- effect
- tags

ChestDefinition
- id
- sourceTier
- itemPoolId
- qualityWeights
- guaranteedReward

ClassDefinition
- id
- displayName
- rarity
- startingWeaponId
- startingPassiveId
- perkId
- weaknessId

RunInventoryState
- weapons
- mutations
- items
- trophies
- temporaryEffects

PlayerEconomyState
- braincells
- ownedClasses
- ownedCosmetics
- classShards
- pityCounters
```

---

## 11. Stage Events

Mid-run random events that fire on a timer (45s initial, 60–120s thereafter). They disrupt the normal "spawn → kill → XP" rhythm and create memorable moments inside a run.

### Event Pool (Prototype)

| Event | Duration | Effect |
| --- | --- | --- |
| Brainrot Surge | 25s | Spawn rate ×2, XP ×2 — "the algorithm is cooked" |
| Rizz Overflow | 20s | All weapon damage +75% |
| Mewing Momentum | 15s | Player move speed +60% |
| Cursed Coffin | instant | Spawns a Sigma Vault chest at a random offset from player |
| NPC Riot | instant | 30 low-HP enemies spawn at once — easy XP food |

### Event Rules

- One active timed event at a time; instant events do not block the timer
- Banner pops at top of screen on trigger
- Persistent indicator badge in the top-left while a timed event is active
- Events do not pause; they keep the action flowing
- Event pool can expand into seasonal/themed variants (e.g., "Skibidi Storm" event during Skibidi season)

### Design Rule

Events should never feel like punishment without payoff. Even "harder" events (more spawns) should drop more rewards. The player should look forward to events, not dread them.

---

## 12. Mid-Run Stat Shop

Players can spend **Fanum Tax (coins)** during a run on permanent run-stat upgrades. The shop is always accessible via the SHOP button or Escape-menu link; opening it pauses the game.

### Shop Items (Prototype)

| Item | Effect | Base Cost | Growth | Max Tier |
| --- | --- | --- | --- | --- |
| Glow-Up HP      | +10 Max HP (heals on purchase) | 25 | 1.5× | 10 |
| Sigma Sprint    | +8% move speed                 | 30 | 1.5× | 8 |
| Bussin Boost    | +8% all weapon damage          | 40 | 1.6× | 10 |
| Grindset Lens   | +10% XP gain                   | 35 | 1.5× | 8 |
| Crit Cultivator | +5% crit chance                | 50 | 1.7× | 8 |
| Mewing Tonic    | +1 HP/sec regen                | 60 | 1.6× | 5 |

### Shop Rules

- Coin sink — gives players agency over coin spending (vendor is reactive, shop is proactive)
- Costs grow exponentially per tier so coins always feel meaningful
- Shop upgrades stack with class mods and trophy buffs
- Shop levels reset on death (run-scoped). In live, persistent meta-shop would use Braincells, not Fanum Tax

---

## 13. UX — Inventory Tooltips & Pause Inspection

The player can inspect any inventory item without dying or stopping the run.

### Hover Tooltips

- Hover any inventory slot (weapon / passive / trophy) → floating tooltip
- Tooltip content: rarity tag, name, description, current stat values (damage, cooldown, range, count, etc.)
- Tooltip follows mouse cursor; auto-flips to opposite side if it would go off-screen
- Evolved weapons show "★ EVOLVED" line at top in gold

### Escape — Pause Inspection

- Pressing Escape opens a full-screen pause overlay with all owned items laid out in a 2-column grid
- Each entry shows: name (color-coded by rarity), level, description, stat block
- Escape again or "RESUME" button to close
- Game state freezes while open

### Design Rule

Build inspection should never feel like a chore or break flow. **The tooltip is for "quick reminder"; the pause menu is for "deep planning"** between waves.

---

## 14. Level Structure

The game is organized into discrete **levels** rather than a single endless run. Players unlock each level by beating the previous one. Each level escalates in difficulty (enemy HP, speed, spawn rate, boss strength) and presents a unique arena layout.

### Level Roster (Prototype)

| # | Name | Duration | Enemy Pool | Boss | Obstacles |
| --- | --- | --- | --- | --- | --- |
| 1 | The Comments Section | 2 min | runners only | none | open circle |
| 2 | Sigma Streets | 3 min | +fast | mini Bombardiro (½ HP) | narrow arena |
| 3 | The Rizz Pit | 4 min | +tank | Bombardiro Grande | 4 corner pillars |
| 4 | Ohio Wastes | 5 min | +ranged | Bombardiro+ (1.5× HP) | 4 corner pillars |
| 5 | Skibidi Tower | 6 min | +exploder | Ballerina Maxima | dividing walls |
| 6 | Cosmic Coliseum | 7 min | all | Il Capo Crocodilo | dividing walls |
| 7 | Brainrot Apocalypse | 10 min | all elite | ALL 3 bosses sequentially | full maze |
| ∞ | Endless Brainrot | forever | all | boss rotation every 90s | rotating maze |

### Per-Level Difficulty Scaling

Each level applies multipliers to base enemy stats:

- **hpMult**: 1.0 → 2.4 from L1 → L7
- **spdMult**: 1.0 → 1.30 from L1 → L7
- **spawnMult**: 1.0 → 2.4 from L1 → L7

Win condition: survive the level duration AND defeat the boss (if any). Death sends the player to the Results screen, not a game-over.

### Linear Unlock

Players must beat Level N to unlock Level N+1. The level select screen shows locked levels as silhouettes with the unlock requirement. Best-time and kill-count are tracked per level.

---

## 15. Lobby + Meta Loop

Between runs, the player returns to a **lobby hub** instead of restarting immediately. This hub is the retention anchor — it shows progress, hosts permanent upgrades, and gives the player a reason to come back.

### Lobby Screens

- **Home**: Braincells balance, total runs/kills, highest level reached. PLAY / SHOP / COLLECTION buttons.
- **Level Select**: 8-tile grid showing locked/unlocked/cleared status per level.
- **Permanent Shop**: Spend Braincells on stat upgrades that affect ALL future runs (max HP, speed, damage, crit, XP gain, coin gain, starting Fanum Tax, free re-rolls).
- **Collection**: Grid of all 8 classes. Rolled classes show their portrait; unrolled show a silhouette.
- **Results Screen**: Shown after every run (win or loss). Displays run stats, Braincells earned, and Retry / Next Level / Lobby buttons.

### Braincells Award

- **Win**: `levelId × 100 + (kills × 2)` Braincells
- **Loss**: `(kills × 1.5) + (elapsed × 0.5)` Braincells (always something — no empty run)

### Persistence

All progress saves to `localStorage`. Survives browser refresh. Wiped only via explicit WIPE button in the lobby.

### Retention Hooks Captured

- **Level ladder** — clear next goal at all times
- **Class collection** — completionist hook ("3/8 collected, still need Brainrot God")
- **Meta-shop ramp** — each run makes the next slightly easier
- **Personal bests** — leaderboard-against-yourself
- **Loss reward** — every run, even a bad one, gives Braincells

---

## 16. MVP Priority

Do not build everything at once.

Recommended order:

1. Simple run inventory that displays picked level-up cards.
2. Strong monster flag and chest drop chance.
3. Chest object that opens a 3-choice item picker.
4. Small item pool with 5-8 items.
5. Boss that always drops a chest.
6. Braincells reward summary after run.
7. Class selection in lobby.
8. Class capsule / gacha system only after policy-safe design is confirmed.

