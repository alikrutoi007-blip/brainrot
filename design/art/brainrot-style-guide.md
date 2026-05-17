# Brainrot Survivors Art and Enemy Style Guide

*Created: 2026-05-16*
*Purpose: Claude-facing visual direction handoff for enemies, weapons, classes, and arenas.*
*Status: Draft v1 for user review*

---

## 1. Core Visual Direction

**Style name:** Meme Chaos Readable

Brainrot Survivors should look like a low-poly Roblox fever dream where the internet became a monster factory. The world is absurd, loud, cursed, and funny, but gameplay must stay readable at all times.

The visual target is not realistic horror and not clean sci-fi. It is a chaotic toybox of brainrot enemies, parody multiverse artifacts, neon effects, and dark low-poly arenas.

**One-line rule:** Everything can be stupid, but nothing can be unreadable.

Reference image:

![Brainrot Survivors style frame](style-frame-v1.png)

---

## 2. Enemy Identity: Brainrots

Enemies should be actual brainrot entities, not generic zombies or monsters. They are living fragments of meme culture, corrupted internet trends, fake mascot legends, low-quality viral creatures, and glitchy cursed characters.

They should feel similar in spirit to Megabonk enemies: simple, funny, aggressive, readable, and strange enough that the player immediately wants to screenshot them.

### Enemy Design Rules

1. **Silhouette first**
   - Every enemy must be readable from far away.
   - Shape matters more than face detail.
   - If the enemy is not recognizable as a 64x64 thumbnail, simplify it.

2. **One joke per enemy**
   - Each enemy should have one clear visual gag.
   - Example: huge screaming head, tiny legs, fake luxury glasses, spinning toilet crown, glitch smile, noodle arms.
   - Do not stack five unrelated jokes on one enemy.

3. **Behavior visible in body shape**
   - Fast enemies should be skinny, sharp, stretched, or leaning forward.
   - Tanks should be wide, blocky, heavy, and red-coded.
   - Ranged enemies should have a clear launcher, mouth, antenna, or arm cannon silhouette.
   - Exploders should look unstable, bloated, cracked, or warning-colored.

4. **Funny before scary**
   - The enemies can be cursed, but they should not become realistic horror.
   - Keep them goofy, ugly-cute, and Roblox-safe.

5. **Low detail, high contrast**
   - Big eyes, big mouths, flat colors, chunky geometry.
   - No tiny texture details that disappear in a crowd.

### MVP Enemy Archetypes

| Enemy Type | Gameplay Role | Visual Direction | Color Code |
| --- | --- | --- | --- |
| Basic Brainrot | Standard chaser | Round head, tiny legs, dumb expression | Green or white |
| Speed Brainrot | Fast pressure | Long stretched body, tilted forward, motion streaks | Yellow |
| Tank Brainrot | HP wall | Wide blocky mascot body, heavy feet, slow stomp | Red |
| Ranged Brainrot | Projectile threat | Floating head or arm-cannon creature, clear firing pose | Blue |
| Exploder Brainrot | Area denial | Cracked orange body, warning glow, unstable shaking | Orange |
| Mini-Boss Brainrot | Mid-run spike | Oversized version of a meme creature with one clear attack | Purple accent |
| Final Boss Brainrot | Run climax | Algorithm-infected king/queen/mascot, huge silhouette | Black, white, magenta |

### Brainrot Enemy Roster v1

This roster is based on current Italian brainrot and Roblox brainrot culture, adapted into original, parody-safe enemy designs for Brainrot Survivors. The goal is to capture the recognizable absurdity without directly copying protected characters, logos, or exact meme images.

Reference image:

![Brainrot Survivors enemy roster](enemy-roster-v1.png)

| Enemy | Reference Energy | Gameplay Role | Visual Style | Gameplay Behavior |
| --- | --- | --- | --- | --- |
| Tralala Runner | Sneaker shark brainrot | Basic chaser | Shark-like mascot body, oversized cursed sneakers, dumb face | Runs straight at the player in packs |
| Crocodilo Bomber | Crocodile bomber brainrot | Exploder | Chunky crocodile-plane hybrid with orange warning glow | Charges, then detonates near the player |
| Sahur Drummer | Rhythm/stick brainrot | Buffer | Wooden drum-stick creature with pulsing glow | Speeds up nearby enemies in rhythm pulses |
| Cappuccina Spinner | Ballerina coffee brainrot | Swarm dancer | Teacup-headed dancer with spinning skirt silhouette | Moves in curved spinning paths to disrupt kiting |
| Assassino Cup | Tiny coffee assassin brainrot | Elite fast enemy | Small coffee-cup assassin with foam scarf | Performs short dash bursts toward low-HP player |
| Bananini Chimp | Banana chimp brainrot | Jumper | Monkey-banana hybrid with bright yellow silhouette | Leaps over crowds to close distance |
| Patapim Stomper | Heavy stomping brainrot | Tank | Wide blocky stomper with heavy feet | Slow high-HP enemy that emits shockwave rings |
| Larila Mirage | Long-neck glitch brainrot | Ranged trickster | Tall stretched glitch creature with musical/projectile face | Fires slow homing note-like projectiles |
| Ambalabu Doll | Cursed doll brainrot | Slow-zone enemy | Wooden puppet/doll body with stiff arms | Leaves puddles that slow the player |
| Troppi Splitter | Double nonsense brainrot | Splitter | Wobbly two-headed creature | Splits into smaller enemies on death |
| Saturn Cow | Cosmic cow brainrot | Mini-boss | Cow body with fake planet-ring silhouette | Orbits projectiles around itself while chasing |
| Frigo Camel | Fridge camel brainrot | Terrain blocker | Camel/fridge hybrid, blocky and cold-colored | Drops temporary block obstacles in movement lanes |
| Elefanto Crusher | Coconut elephant brainrot | Tank elite | Elephant/coconut hybrid with massive head | Slow charge attack that knocks the player back |
| Dolphina Banana | Banana dolphin brainrot | Projectile wave enemy | Dolphin-banana shape, bright yellow/blue | Sends arcing banana-wave projectiles across arena |
| Celeste Giraffe | Tall blue giraffe brainrot | Sniper | Very tall blue giraffe silhouette | Telegraphs a long-range beam, then zaps |
| Gusini Wing | Goose-plane brainrot | Flying swarm | Small goose-plane shape | Flies over ground enemies and dives at player |
| Algorithm King | Original fusion boss | Final boss | Crowned corrupted brainrot mascot with glitch halo | Summons all enemy types in phases and escalates arena chaos |

### Enemy Roster Implementation Notes

- Start MVP with 5 enemies: `Tralala Runner`, `Crocodilo Bomber`, `Patapim Stomper`, `Larila Mirage`, and `Algorithm King`.
- Add `Sahur Drummer` only after basic enemy AI is stable, because buffers require group-effect logic.
- Add `Troppi Splitter` after object pooling is proven, because split-on-death can multiply entity count quickly.
- Use color-coded materials first, custom models second. Readability matters more than exact meme accuracy.
- For legal and moderation safety, avoid direct names, exact faces, exact audio, real logos, and exact silhouettes from copyrighted media.

---

## 3. Weapon Identity: Multiverse Meme Artifacts

Weapons are not normal swords and guns. They are collectible artifacts from a fake brainrot multiverse: anime-inspired relics, game-inspired tools, comic-style cosmic items, cursed internet objects, and parody meme weapons.

Important legal/art direction rule: **do not directly copy copyrighted characters, names, logos, or iconic exact designs.** Use parody-safe, original versions that players understand without creating direct IP risk.

Example:

- Avoid: "Thanos Glove"
- Use: "Cosmic Snap Glove"
- Avoid: exact anime sword or symbol
- Use: "Cursed Combo Katana" with original shape language

### Weapon Design Rules

1. **Each weapon needs a readable combat pattern**
   - Orbit, beam, dash trail, zone, chain shot, summon, burst, projectile rain.
   - The visual should tell the player what the weapon does.

2. **Rarity changes behavior, not just stats**
   - Rare items should feel more specific.
   - Epic items should define a build.
   - Legendary items should create an objective inside the run.

3. **Legendary weapons can start incomplete**
   - Some legendary artifacts should require fragments, charges, or conditions.
   - This creates a mini-story inside the run.

4. **Effects must have a visual budget**
   - The weapon can be spectacular, but it cannot hide the player or enemy attacks.
   - Prefer chunky readable effects over dense particle noise.

### Starter Weapon Examples

| Weapon | Rarity | Role | Fantasy |
| --- | --- | --- | --- |
| Tralalelo Sneakers | Rare | Mobility and shockwave damage | Cursed speed shoes that make the player slide, dash, and leave impact trails |
| Cosmic Snap Glove | Legendary | Long-term power goal | Starts weak; collect 10 cosmic shards to activate screen-clearing snap pulses |
| Pixel Portal Blaster | Rare | Chain damage | Fires glitch shots that bounce between enemies and open tiny damage portals |
| Anime Rage Headband | Epic | Risk/reward damage | Lower HP means bigger attacks and short rage bursts |
| Cursed Combo Katana | Epic | Close-range snowball | Auto-slashes nearby enemies; combo grows until player takes damage |
| Comment Cannon | Common | Directional projectile spam | Shoots angry comment bubbles at nearest enemies |
| Aura Field | Common | Defensive AoE | Creates a pulsing field around the player for close-range control |

---

## 4. Class System Direction

Full character designs are not required for MVP. The player can remain a simple Roblox avatar while **Class Cards** define gameplay identity.

This keeps scope smaller and lets the game focus on enemies, weapons, effects, and record chasing.

### Recommended Class Model

Classes are collectible loadouts that change:

- starting weapon
- small movement modifier
- passive stat identity
- class icon and color
- optional VFX aura

The class should not require a unique full character model in MVP.

### Safe Gacha Recommendation

Use gameplay-earned class capsules or class unlocks, not paid Robux gacha in MVP.

Allowed direction for MVP:

- Earn Braincells by playing.
- Spend Braincells on class unlock attempts or direct unlocks.
- Classes affect playstyle, but should be balanced.
- Cosmetics can be monetized later through direct purchase.

Avoid for MVP:

- Robux paid random class rolls.
- Pay-to-win class power.
- Extremely low odds for gameplay-critical classes.

### Starter Class Cards

| Class | Starting Weapon | Passive Identity | Visual Icon |
| --- | --- | --- | --- |
| Speed Freak | Tralalelo Sneakers | Faster movement, weaker defense | Neon shoe with motion streak |
| Glitch Mage | Pixel Portal Blaster | More chain/projectile effects | Broken pixel eye |
| Tanky Mascot | Aura Field | More HP, slower acceleration | Blocky mascot helmet |
| Combo Maniac | Cursed Combo Katana | Bonus damage while untouched | Slash counter icon |
| Summon Kid | Comment Swarm | Extra small helper projectiles | Tiny floating comment faces |

---

## 5. Arena and Environment Style

The arena should be the stage, not the star. It must support readability and movement.

### Environment Direction

Use dark, desaturated, low-poly arenas with bright enemy and weapon colors on top.

The first arena should feel like a corrupted internet playground:

- dark grid floor
- neon hazard lines
- broken billboard screens
- fake ads with unreadable symbols, not real brands
- glitch portals at the edges
- chunky low-poly props
- simple ramps or obstacles only if they do not harm movement flow

### Arena Rules

1. **No clutter in movement lanes**
   - Props should sit near edges or outside the main combat path.
   - The player must always have space to kite.

2. **Background lower contrast than gameplay**
   - Enemies, XP, player, and attacks must pop more than the environment.

3. **No precision platforming**
   - Movement is for positioning, not jumps over death pits.

4. **Use landmarks**
   - Each arena should have 3-5 large visual landmarks so players feel movement through space.

---

## 6. Color Language

Color should communicate function.

| Element | Suggested Color Language |
| --- | --- |
| Player core | White or cyan highlight, highest contrast |
| Player attacks | Cyan, magenta, green, white |
| Basic enemies | Green/white |
| Fast enemies | Yellow |
| Tank enemies | Red |
| Ranged enemies | Blue |
| Exploders | Orange |
| Bosses | Purple, black, magenta accents |
| XP orbs | Bright cyan or lime |
| Rare drops | Gold or rainbow shimmer |
| Arena | Muted gray, purple-gray, dark blue-gray |

Do not let enemy colors and player attack colors fully overlap. The player must know what is safe and what is dangerous.

---

## 7. VFX Readability Rules

Brainrot Survivors should become visually explosive by minute 7, but the chaos must stay layered.

### VFX Layers

1. **Player position layer**
   - Always visible.
   - Highest contrast outline or glow.

2. **Enemy threat layer**
   - Enemy bodies and enemy projectiles.
   - Must not be hidden by player VFX.

3. **Player attack layer**
   - Satisfying, bright, but partially transparent when large.

4. **Background flavor layer**
   - Glitch, billboards, distant particles.
   - Low opacity only.

### VFX Budget

For MVP, keep weapon effects chunky and reusable:

- no dense particle clouds around the player for more than 0.5 seconds
- no full-screen flashes except level-up, boss death, or legendary activation
- no tiny particles as primary feedback
- prefer rings, arcs, trails, bursts, and icons

---

## 8. Claude Implementation Notes

When Claude creates or requests assets, use this style guide as the source of truth.

### Asset Naming Suggestions

- `enemy_basic_brainrot`
- `enemy_speed_brainrot`
- `enemy_tank_brainrot`
- `enemy_ranged_brainrot`
- `enemy_exploder_brainrot`
- `weapon_tralalelo_sneakers`
- `weapon_cosmic_snap_glove`
- `weapon_pixel_portal_blaster`
- `class_speed_freak`
- `class_glitch_mage`

### Roblox Production Constraints

- Favor MeshPart or simple Model assemblies.
- Avoid high-poly models.
- Avoid unique heavy textures per enemy.
- Avoid Humanoid-driven swarm enemies for large crowds.
- Use color/material swaps for variants.
- Keep hitboxes simple and larger than visuals when needed.
- Build enemies so they can be pooled and reused.

### First Asset Pack to Make

For the next design pass, define:

1. 5 enemy silhouettes
2. 5 weapon icons or prop concepts
3. 5 class card icons
4. 1 arena mood board
5. 1 VFX language sheet

---

## 9. Open Decisions for User Review

1. Should classes be unlocked by direct Braincells purchase, gameplay achievements, or earned random capsules?
2. Should brainrot enemies reference current memes directly, or should they be mostly original parody creatures?
3. Should legendary weapons use fragment collection in MVP, or only in v1.0?
4. Should the first arena be "Corrupted Internet Arena", "Cursed Mall", or "Algorithm Desert"?
