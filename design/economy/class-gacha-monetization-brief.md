# Brainrot Survivors Class Gacha and Monetization Brief

*Created: 2026-05-16*
*Purpose: Claude-facing economy direction for lobby flow, Braincells, class gacha, and monetization.*
*Status: Draft v1 for user review*

---

## 1. Core Monetization Direction

Brainrot Survivors should be monetizable, but the monetization should support the core fantasy instead of replacing skill.

The main paid loop is:

```text
Buy or earn Braincells -> open Class Capsules -> unlock classes -> choose a class before a run -> play the run -> earn more Braincells and records
```

Classes can give a strong starting identity and early-game advantage, but they should not automatically win the run. After the first minutes, the player still needs to:

- survive enemy waves
- collect XP
- choose upgrade cards intelligently
- build around weapon synergies
- dodge bosses and dangerous enemy patterns
- optimize for time, damage, and leaderboard records

**Design position:** Paying can give the player more options and a stronger start, but the run is still won through build decisions and gameplay execution.

---

## 2. Lobby Flow

The game starts in a shared social lobby. The lobby is where players see other players, show off classes/cosmetics, choose modes, spend Braincells, and enter runs.

### Lobby Functions

The lobby should include:

- Play portal / mode select
- Class selection
- Class capsule machine
- Braincells shop
- Leaderboard boards
- Personal best display
- Cosmetic preview area
- Future seasonal/event board

### Player Flow

```text
Join game
-> spawn in shared lobby
-> collect daily reward / check records
-> choose class or roll class capsule
-> choose game mode
-> enter run
-> earn Braincells and rewards
-> return to lobby
-> upgrade collection / reroll / try again
```

The lobby should feel like a corrupted internet arcade: neon signs, class capsule machines, glitch portals, record boards, and brainrot statues.

---

## 3. Game Modes

Players choose modes from the lobby. Modes control difficulty, reward rate, and leaderboard rules.

### MVP Modes

| Mode | Purpose | Braincells Reward | Leaderboard |
| --- | --- | --- | --- |
| Normal Run | Main 8-10 minute survivors run | Standard | Personal and global |
| Hard Run | Higher enemy density and stronger boss | Higher | Separate hard leaderboard |
| Practice Run | Test class/weapons without pressure | Reduced or none | No leaderboard |

### Future Modes

| Mode | Purpose |
| --- | --- |
| Daily Seed | Same card RNG and enemy schedule for everyone that day |
| Boss Rush | Short mode focused on boss fights |
| Endless Brainrot | Survival score mode after final boss |
| Event Mode | Seasonal mode with limited drops |

### Competitive Safeguard

If paid class gacha affects early-game power, leaderboards should eventually separate:

- **Standard Leaderboard:** all classes allowed
- **F2P/Normalized Leaderboard:** only earned/unlocked classes or normalized class stats
- **Daily Seed Leaderboard:** fixed class or fixed allowed pool

This lets the game monetize strongly while still giving competitive players a fair arena.

---

## 4. Braincells Currency

Braincells are the main progression currency.

### How Players Earn Braincells

Players earn Braincells by:

- completing runs
- killing bosses
- beating personal records
- clearing harder modes
- daily/weekly challenges
- seasonal events
- duplicate class conversion

### How Players Spend Braincells

Players spend Braincells on:

- Class Capsules
- direct class unlocks, if enabled
- cosmetic class skins
- aura colors
- weapon VFX skins
- emotes
- future event items

### Robux Purchase Direction

Braincells can be sold for Robux as a premium acceleration product.

If Braincells can be bought with Robux and spent on Class Capsules, then Class Capsules become **paid random items** under Roblox policy. This means implementation must include:

- visible numerical odds before purchase
- Roblox Maturity & Compliance disclosure
- `PolicyService:GetPolicyInfoForPlayerAsync(player)`
- blocking paid random item interaction when `ArePaidRandomItemsRestricted == true`
- region/age-safe fallback purchase options

Fallback for restricted players:

- direct class purchase
- cosmetic shop
- battle pass
- earned-only capsule track

---

## 5. Class Gacha Design

Class gacha is the main collection system.

Each class determines:

- starting weapon
- starting passive
- early-game strength curve
- drawback or weakness
- visual icon
- optional aura/cosmetic identity

### Important Balance Rule

Rare classes can have stronger starts or more unusual mechanics, but each class needs a weakness.

Example:

```text
Legendary class = stronger early identity, not guaranteed win.
Common class = stable and easy to use.
Rare class = sharper playstyle.
Epic class = build-defining with downside.
Legendary class = powerful quest/start condition, but risky or scaling-dependent.
```

### Example

```text
Cosmic Collector
Rarity: Legendary
Starting weapon: Cosmic Snap Glove
Advantage: cosmic shards spawn more often
Weakness: weak early damage until shards are collected
Result: paid player can start with a rare path, but still needs to survive and build correctly
```

---

## 6. Class Capsule Odds Proposal

These odds are a starting point and should be tuned.

| Rarity | Chance |
| --- | --- |
| Common | 65% |
| Rare | 25% |
| Epic | 8.5% |
| Legendary | 1.45% |
| Mythic / Brainrot | 0.05% |

If the user wants a true "1 in 100,000" class, it should be cosmetic-first or prestige-first, not required for competitive power.

Recommended use:

```text
1 in 100,000 = ultra-rare class skin, aura, title, or flex variant
1 in 1,000 to 1 in 5,000 = rare gameplay class target
```

Reason: if the best gameplay class is 1 in 100,000, most players will never see it, and whales may dominate the perceived meta.

---

## 7. Pity and Duplicate System

Paid or high-value gacha needs pity to avoid player frustration.

### Pity Proposal

| Rarity | Pity |
| --- | --- |
| Rare | guaranteed every 10 rolls |
| Epic | guaranteed every 40 rolls |
| Legendary | guaranteed every 150 rolls |
| Mythic / Brainrot | no hard pity in MVP, or very high pity only for cosmetics |

### Duplicate Conversion

Duplicates should never feel wasted.

Duplicate rewards can become:

- Class Shards
- class skin progress
- aura color unlocks
- titles
- profile badges
- pity progress

Example:

```text
Duplicate Common -> 5 Class Shards
Duplicate Rare -> 25 Class Shards
Duplicate Epic -> 100 Class Shards
Duplicate Legendary -> 500 Class Shards + special aura token
```

---

## 8. Monetization Products

### Recommended Products

| Product | Monetization Type | Risk | Notes |
| --- | --- | --- | --- |
| Braincells packs | Developer Product | Medium | Strong revenue; triggers paid random item rules if used on capsules |
| Class Capsules | Random item sink | High | Requires odds disclosure and PolicyService if Braincells are purchasable |
| Direct class unlock | Developer Product | Lower | Good fallback for restricted players |
| Class skins | Cosmetic | Low | Best whale/flex product |
| Weapon VFX skins | Cosmetic | Low | Strong for visual status |
| Battle pass | Seasonal | Low-Medium | Good long-term revenue |
| VIP | Game Pass / subscription-style benefits | Medium | Should avoid direct leaderboard power |
| Private servers | Roblox private server | Low | Good for friends/testing |

### Products to Avoid Early

- paid rerolls during a live run
- paid revives for leaderboard runs
- paid damage multipliers
- paid leaderboard boosts
- paid-only weapons with no gameplay unlock path

These damage trust in competitive records.

---

## 9. Leaderboard Integrity

Because Brainrot Survivors has competitive records, monetization must not make records feel fake.

### Rule

Paid power can exist in the collection layer, but leaderboard modes must be clear.

Suggested labels:

- `Open Records`: any unlocked class allowed
- `Normalized Records`: fixed class stats / fixed class pool
- `Daily Seed`: same RNG seed and limited class selection

If the game only has one leaderboard, players may accuse it of being pay-to-win if paid Braincells can roll legendary classes.

---

## 10. Claude Implementation Notes

When implementing this system, Claude should treat the following as non-negotiable:

1. If Braincells are purchasable and can buy capsules, capsules are paid random items.
2. Paid random items require visible odds before purchase.
3. Paid random items require `PolicyService` checks.
4. Restricted users need a non-random fallback shop.
5. Class power should be front-loaded identity, not automatic victory.
6. Leaderboard rules should be explicit in UI and data storage.
7. Never sell direct leaderboard score, damage multiplier, or boss kill advantage.

### Suggested Data Concepts

```text
ClassDefinition
- id
- displayName
- rarity
- startingWeaponId
- passiveId
- drawbackId
- iconId
- allowedInNormalizedMode

CapsuleDefinition
- id
- costBraincells
- oddsByRarity
- pityRules
- restrictedFallbackProductId

PlayerEconomyState
- braincells
- ownedClasses
- classShards
- pityCounters
- purchaseHistory

LeaderboardRunRecord
- mode
- classId
- paidRandomEligibleAtRunStart
- normalizedRulesetId
- time
- damage
- kills
```

---

## 11. Open Decisions

1. Should Braincells be directly purchasable in MVP, or added in v1.0?
2. Should class capsules have a legendary pity counter from day one?
3. Should there be a separate F2P/Normalized leaderboard at launch?
4. Should the rarest 1-in-100,000 reward be a gameplay class, cosmetic variant, aura, or title?

