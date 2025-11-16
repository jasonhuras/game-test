# Core Gameplay Loop

## High-Level Loop

```
Main Menu → Character Select → Run Start → Survive Waves → Make Choices → Grow Stronger →
Eventually Die → Unlock Rewards → Spend Currency → Character Select...
```

## Moment-to-Moment Gameplay (10 seconds)

1. **Player Actions**:
   - Move with WASD/joystick
   - Aim with mouse/right stick
   - Use weapon attacks (auto or manual)
   - Cast spells (cooldown-based)
   - Dodge/dash ability

2. **Enemy Behavior**:
   - Spawn in waves around the arena
   - Pursue player
   - Attack when in range
   - Drop experience orbs on death

3. **Feedback Loop**:
   - Hit enemies → See damage numbers, visual effects
   - Take damage → Screen shake, health indicator
   - Kill enemies → Experience orbs, satisfying sound/VFX
   - Level up → Immediate power spike, choice moment

## Short-Term Loop (2-5 minutes)

### Wave Structure
- **Wave Duration**: 60-90 seconds
- **Enemy Density**: Gradually increases
- **Difficulty Curve**: New enemy types introduced every 3-5 waves
- **Boss Waves**: Every 5 waves (0:05, 0:10, 0:15, etc.)

### Progression Within Run
1. Kill enemies → Gain experience
2. Level up → Choose augment (every level)
3. Find/craft weapons → Swap loadout
4. Discover spells → Expand ability options
5. Collect gold → Use in between waves or special shops

### Augment Choice Moments
**Trigger**: Player levels up
**Presentation**: Pause or slow-time, show 3 augment options
**Rarity Distribution**:
- Common (50% chance)
- Rare (30% chance)
- Epic (15% chance)
- Legendary (5% chance)

**Choice Time**: Unlimited (game paused/slowed)

## Medium-Term Loop (15-30 minutes = Full Run)

### Run Structure

**Phase 1: Early Game (0-10 minutes)**
- Goal: Establish core build direction
- Focus: Survive, pick foundational augments
- Difficulty: Low, learning phase
- Key Moments: First weapon choice, initial augment synergies

**Phase 2: Mid Game (10-20 minutes)**
- Goal: Optimize build, find synergies
- Focus: High-value augment choices, weapon upgrades
- Difficulty: Ramping, requires active play
- Key Moments: Build "comes online", power spikes

**Phase 3: Late Game (20-30 minutes)**
- Goal: Maximize power, perfect build
- Focus: Min-maxing, survival
- Difficulty: Extreme, screen-filling enemies
- Key Moments: Peak power fantasy, final boss

**Phase 4: End Game (30+ minutes)**
- Goal: See how long you can last
- Focus: Pure survival, testing limits
- Difficulty: Endless scaling
- Key Moments: Personal best times, leaderboard pushes

### Run Completion
**Success Outcomes**:
- Reached Wave X → Unlock achievement
- Defeated Boss Y → Unlock character/weapon
- Earned Z gold → Spend in meta progression

**Failure Outcomes**:
- Keep all gold/experience earned
- Unlock progress saved
- Stats recorded (furthest wave, time survived, kills)

## Long-Term Loop (Hours/Days/Weeks)

### Meta Progression System

**Character Unlocks**:
- Start with 1 character
- Unlock others through achievements (reach Wave 10, defeat boss, etc.)
- Each character has unique starting weapon and stats

**Weapon Unlocks**:
- Discover in runs (low chance)
- Unlock permanently by finding once
- Can appear in future runs

**Spell Unlocks**:
- Find spell tomes during runs
- Permanently added to spell pool

**Augment Unlocks**:
- Some augments locked behind progression
- Unlock by achieving specific feats
- Expands build variety over time

**Account Progression**:
- Player level (cosmetic, shows dedication)
- Achievements (guided objectives)
- Statistics tracking (kills, runs, time played)
- Leaderboards (fastest Wave X clear, longest survival)

### Meta Currency: "Soul Essence" (Placeholder Name)

**How to Earn**:
- Dropped by enemies during runs
- Bonus for wave milestones
- Bonus for achievements
- Keeps 100% on death

**How to Spend**:
- Unlock characters (high cost)
- Unlock weapons (medium cost)
- Unlock spells (medium cost)
- Permanent stat boosts (small, expensive, optional)
  - +5% max health
  - +5% damage
  - +5% movement speed
  - (Caps to prevent becoming OP, like 20% max each)

### Daily/Weekly Engagement

**Daily Challenges**:
- Special modifiers (double boss health, limited spell slots, etc.)
- Bonus rewards for completion
- Leaderboard for fastest clear

**Weekly Rotations**:
- Featured character (bonus XP)
- Featured augment pool (curated synergies)
- Special event biomes

## Ranked Mode Loop (Separate from Main Loop)

### Pre-Match
1. Queue for 1v1 or 2v2
2. Ban phase (each player bans 2 augments - prevents OP combos)
3. Character selection (blind pick or draft)
4. Load into mirrored arenas

### Match Flow
1. Both players start simultaneously
2. Kill enemies in your arena → gain power
3. Each enemy killed → spawns weaker enemy in opponent's arena
4. First player to die → loses
5. Tiebreaker: Most kills, most damage, etc.

### Ranked Progression
- **Ranking System**: Bronze → Silver → Gold → Platinum → Diamond → Master
- **Match Duration**: ~10-15 minutes
- **Rewards**: Cosmetics, exclusive augments (sidegrade power), titles

## Design Considerations

### Player Retention Hooks
1. **Short-term**: "One more run" - quick sessions, clear goals
2. **Medium-term**: "Unlock that character" - meta progression gates
3. **Long-term**: "Climb the ladder" - ranked competitive play

### Balancing PvE and PvP
- **Separate augment pools**: Some augments only in PvE, others only PvP
- **Different balance patches**: PvP nerfs don't affect PvE fun
- **Modes can exist independently**: Players can enjoy one without the other

### Accessibility vs Depth
- **Easy to learn**: Tutorial teaches basics in 5 minutes
- **Hard to master**: Deep build optimization, competitive play
- **Skill floor**: Anyone can have fun in PvE
- **Skill ceiling**: Top players dominate in ranked

---

**Related Documents**:
- `/02-Game-Design/Combat/combat-system.md` - Detailed combat mechanics
- `/02-Game-Design/Augments/augment-system.md` - Augment design philosophy
- `/05-Progression/Meta-Progression/progression-systems.md` - Unlock trees
