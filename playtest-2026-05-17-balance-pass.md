# Playtest Report — Balance & Game-Feel Pass

*Date: 2026-05-17*
*Target: `brainrot-survivors-demo.html`*
*Scope: Tuning-only pass. No rewrites. All Codex life-polish preserved (WebAudio SFX, sound toggle, event toasts, damage flash, low-HP vignette, player trail, ambient arena pixels, lobby feed).*

---

## What Changed

### 1. First-wave fairness (`LEVELS`, `mkGame`, `updateSpawner`)
- **3-second initial spawn grace** (`spawnTimer:3` in `mkGame`). Player gets time to see their class kit before the first enemy spawns.
- **Softer spawn ramp**: ramp interval increased from every 20s → every 25s. `spawnRate` no longer doubles as quickly.
- **Per-level spawn cap** (`maxSpawn` field on each level):
  - L1: 4 / sec  (was implicitly 14)
  - L2: 6 / sec
  - L3: 8 / sec
  - L4: 10 / sec
  - L5: 12 / sec
  - L6+: 13–14 / sec
- **Slightly slower L1 enemies** (`spdMult: 1.0 → 0.92`). New players aren't run down before they shoot anything.
- Higher-level `spdMult` and `hpMult` curves were also pulled down ~5% across the board so the climb from L2→L6 feels less spiky.

### 2. XP / level-up pacing (`XP_THRESHOLDS`)
- Old early curve: `50, 110, 190, 290, 410, 560`
- New early curve: `30, 75, 140, 220, 320, 440`
- ~40% faster first level-up; first 5 level-ups all land sooner so the build starts forming inside the first minute. Late game thresholds tightened slightly so endless still scales.

### 3. Weapon balance (`WEAPONS`)
| Weapon | Change | Why |
| --- | --- | --- |
| Comment Cannon | base dmg 50 → **55**, max-level cd 0.6 → **0.55** | Reliable backbone needed a tiny buff to keep up after Sigma Sweep nerf. |
| Glazer Beads | base dmg 25 → **32**, +12/lvl, hitCd 0.5 → **0.42** | Orbiting weapon was underperforming vs sweep; faster re-hit lets it punch through hordes. |
| Sigma Sweep | base dmg 20 → **14**, +12/lvl, rotSpd slowed slightly | Was clearly best-in-slot — sustained 100 DPS AoE on a 45° arc. Now 70 DPS — still strong, no longer auto-pick. |
| Ohio Drop | fuse 1.8s → **1.5s**, dropCd at max 0.75s → **0.7s** | Drop felt sluggish — faster fuse makes the burst feel responsive. |
| Mewing Strike | base dmg 60 → **45**, +20/lvl | Top single-direction DPS with no real downside. Still strong, just no longer dominant. |

### 4. Mutations
**No changes this pass.** Build variety already comes from weapon-vs-passive choice tension at level-up, not from the passive pool itself. All 10 passives stay one-shot grants and each has a clear identity. Adding more right now would dilute the decision rather than sharpen it.

### 5. Boss / event pacing
**No changes this pass.** Codex's polish already added boss-defeat toast, gold flash, and chest SFX (see `killBoss()` at line ~1654). Boss countdown HUD already telegraphs the spawn. With the gentler spawn cap, players reach bosses with healthier builds.

### 6. Lobby
**No changes this pass.** Codex already added a dynamic `Next goal:` line that reads:
- "Clear Level N to unlock the next arena" while progressing,
- "Collect X/8 classes" after all 8 levels are cleared,
- "Push endless mode and chase a cleaner build" once both are done.

That covers the "show what to do next" requirement.

---

## Current First-3-Minute Pacing (Level 1, expected)

| Time | What's happening |
| --- | --- |
| 0:00–0:03 | Player spawns, sees class card resolved, no enemies on screen. Time to learn movement and watch starting weapon auto-fire. |
| 0:03–0:15 | First 1–3 runners spawn (1/sec base rate). Player learns weapon hit feel, picks up first XP gem. |
| 0:15–0:30 | **First level-up** lands (~30 XP from 4–5 kills). Player sees their first upgrade card. Build direction starts. |
| 0:30–1:00 | 6–8 runners on screen, second level-up around 0:50. Spawn rate still 1/sec on L1 (4-cap not yet reached). |
| 1:00–1:30 | **Third level-up** — first chance to evolve a path. First Mid Chest drops (8% per kill). |
| 1:30–2:00 | Level 1 wraps up. Player walks into Results screen with first build, 100+ Braincells, L2 unlocked. |
| 2:00–3:00 | Player picks L2 from select, rolls a new class capsule, fights against runners + fast (yellow diamonds) for the first time. |

---

## What Still Feels Weak

1. **L1 has no boss** — winning feels anticlimactic. The transition from "survive 2 min" to "you cleared it!" is flat. A 30-second "encore wave" or a single Elite enemy at 1:45 would give L1 a real climax.

2. **Coin economy is invisible early.** Players earn Fanum Tax during a run but the only spend point (mid-run vendor) doesn't appear until 2:00. On L1 (2 min total), most players will never see the vendor. Either trigger the first vendor at 1:00 on L1 specifically, or make L1 chests drop slightly more coins as a visible reward.

3. **Build forming by 3:00, but no clear power spike yet.** The player has 2–3 level-ups by then but evolution gates require Lv 5 weapon + specific passive, which won't trigger until ~minute 6. There's a long mid-game flat zone. Consider adding a mid-tier "minor evolution" or a chest that can grant a weapon free level on pickup.

4. **Spawn rate cap is hard at L1 (4/sec).** This makes the final 30s of L1 less intense than it could be. Could ease the cap up to 5/sec for the last 30 seconds of L1 to give the level a finishing crescendo.

5. **No audio feedback on level-up itself.** Codex added card hover/confirm SFX but the moment of "you leveled up!" doesn't have a distinct sting. Easy add for next pass.

---

## Next Recommended Step

**Add an L1 climax + first-vendor-on-L1.**

- Spawn an Elite Tralala Runner (2× HP, gold outline) at 1:30 on L1. Drops a guaranteed Mid Chest. Gives the level a clear "boss-lite" moment without changing the level structure.
- Trigger the first mid-run vendor at 1:00 on L1 specifically (special-case the timer). Player sees the coin economy exists, sees the SKIP button, learns the pattern before it matters on L3+.

Both are small additions to existing systems (no new mechanics), and they fix the two biggest "this feels flat" problems in the first 3 minutes.

---

## Files Touched

- `brainrot-survivors-demo.html`
  - `LEVELS` (8 entries): added `maxSpawn`, retuned `hpMult` / `spdMult` / `spawnMult` curves
  - `XP_THRESHOLDS`: lowered early curve
  - `WEAPONS`: rebalanced `comment_cannon`, `glazer_beads`, `sigma_sweep`, `ohio_drop`, `mewing_strike`
  - `mkGame()`: initial `spawnTimer:3` for spawn grace
  - `updateSpawner()`: softer ramp + per-level `maxSpawn` cap

No other files modified. No Codex polish reverted. Syntax verified with `node --check`.
