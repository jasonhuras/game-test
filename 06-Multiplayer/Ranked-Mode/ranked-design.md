# Ranked Mode Design

## Core Concept

**"Survive Longer, Win Harder"**

Two players enter mirrored arenas simultaneously. As you kill enemies in your arena, weaker versions spawn in your opponent's arena. Last player alive wins. It's a race to build the strongest character while overwhelming your opponent.

---

## Game Flow

### Pre-Match Phase

#### 1. Queue System
- **Solo Queue**: 1v1 ranked
- **Party Queue**: 2v2 ranked (post-launch)
- **Matchmaking**: ELO-based (±100 MMR range)
- **Average Queue Time Goal**: < 2 minutes

#### 2. Ban Phase (Optional, for balance)
- Each player bans 2 augments
- Prevents OP combos (e.g., ban "Glass Cannon" and "Death Defiance")
- 30 seconds to select bans
- Bans are blind (don't see opponent's bans)

#### 3. Character Selection
- **Blind Pick**: Both players select simultaneously
- **Draft Pick** (optional mode): Alternating picks
- 30 seconds to select character
- Shows opponent's choice after both locked in

#### 4. Loading Screen
- Show both players' ranks
- Show character picks
- Displays match info (map, mode)

---

### Match Phase

#### Arena Setup

**Mirrored Arenas**:
- Both players in identical arenas
- Same spawn points, same terrain
- **Cannot see opponent's screen** (UI shows opponent health/wave)

**Visual**:
- Split-screen observer mode (for spectators)
- Player only sees their own arena

#### Starting Conditions

**Both players start with**:
- Selected character (same starting weapon/stats as PvE)
- Level 1
- 0 gold
- Full health

**Match Settings**:
- Wave timer: 60 seconds per wave
- Waves synchronized (both players on Wave 5 simultaneously)
- Boss waves: Every 5 waves (same as PvE)

#### Enemy Spawn Linking System

**Core Mechanic**: Your kills = opponent's problems

**Formula**:
```
For every enemy YOU kill:
→ Spawn 1 weaker enemy in OPPONENT's arena
→ Weaker enemy = 50% health, 75% damage of original
```

**Example**:
- You kill 50 enemies in Wave 5
- Opponent gets 50 bonus enemies spawned (on top of normal wave)
- These enemies are weaker but add pressure

**Strategic Depth**:
- Kill fast → overwhelm opponent
- But you still need to survive your own waves
- Balance aggression vs defense

#### Augment Selection Differences

**PvP Augment Pool**:
- ~70% same as PvE
- ~30% PvP-exclusive or modified

**Banned Augments**:
- Death Defiance (too swingy in 1v1)
- Invincibility effects
- Extreme sustain (infinite healing)

**PvP-Balanced Augments**:
- Lifesteal: 20% (PvE) → 10% (PvP)
- Damage boosts: Reduced by 25%
- Defensive augments: Reduced by 25%

**Reason**: Prevent one-shot builds, promote longer matches

#### Victory Conditions

**Primary**: Last player alive wins

**Tiebreaker** (if both die simultaneously):
1. Player who survived more waves
2. Player with more total kills
3. Player with more damage dealt
4. Coinflip (extremely rare)

**Match Duration**:
- Average: 10-15 minutes
- Minimum: 5 minutes (if one player dies early)
- Maximum: 30 minutes (then forced tiebreaker)

---

### Post-Match Phase

#### Results Screen

**Display**:
- Winner/Loser
- MMR change (+25, -25, etc.)
- New rank (if promoted/demoted)
- Match stats:
  - Waves survived
  - Enemies killed
  - Damage dealt
  - Augments taken (build comparison)
  - Time survived

**Rewards**:
- Ranked points (separate from MMR)
- Cosmetic currency (for PvP-exclusive skins)
- Progress toward seasonal rewards

#### Rematch Option
- Challenge same opponent (both must accept)
- Same MMR stakes
- New bans/picks

---

## Ranking System

### Rank Tiers

| Rank | MMR Range | % of Players | Rewards |
|------|-----------|--------------|---------|
| **Bronze** | 0-999 | 30% | Basic border |
| **Silver** | 1000-1499 | 25% | Silver border, emote |
| **Gold** | 1500-1999 | 20% | Gold border, emote, spray |
| **Platinum** | 2000-2499 | 15% | Platinum border, unique augment skin |
| **Diamond** | 2500-2999 | 7% | Diamond border, character skin |
| **Master** | 3000-3499 | 2% | Master border, weapon skin, title |
| **Grandmaster** | 3500+ | 0.5% | GM border, exclusive character, title |

### MMR System

**Starting MMR**: 1000 (Silver)

**Win/Loss Changes**:
- Win vs equal MMR: +25
- Win vs higher MMR: +30-40
- Win vs lower MMR: +15-20
- Loss vs equal MMR: -25
- Loss vs higher MMR: -15-20
- Loss vs lower MMR: -30-40

**Promotion/Demotion**:
- Promote: Reach next rank's MMR threshold
- Demote: Fall below current rank's MMR - 50 (grace period)

**Decay** (optional):
- Master+ ranks decay if inactive for 7 days
- Lose 10 MMR per day after 7 days inactive

---

## Seasonal System

### Season Structure

**Season Duration**: 3 months

**Season Rewards**:
- Exclusive character skin (for reaching Gold+)
- Weapon skins (for reaching Platinum+)
- Exclusive augment variants (cosmetic only, same stats)
- Profile border
- Ranked spray/emote

**End-of-Season**:
- Soft MMR reset (compress toward 1500)
- Keep rank borders as legacy cosmetics
- New seasonal rewards announced

**Mid-Season Patch**:
- Balance changes based on data
- New PvP augments introduced
- Bug fixes and QoL improvements

---

## 2v2 Ranked Mode (Post-Launch)

### Differences from 1v1

**Team Coordination**:
- Voice chat (optional)
- Ping system for communication
- Shared enemy linking (both teams' kills spawn enemies for opponents)

**Victory Condition**:
- Last team with any player alive wins

**Additional Strategy**:
- Support builds (buff ally)
- Tank builds (draw aggro)
- DPS builds (kill fast)

**Matchmaking**:
- Solo queue (random teammate)
- Duo queue (pre-made team)
- Separate MMR from 1v1

---

## Anti-Cheat & Fair Play

### Cheating Prevention

**Server-Side Validation**:
- All damage calculated server-side
- Augment selections validated
- Impossible stat values rejected

**Anti-Cheat Software**:
- Integrate Easy Anti-Cheat or BattlEye
- Detect memory manipulation
- Detect unauthorized mods

**Reporting System**:
- In-game report button
- Report categories: Cheating, Griefing, Harassment
- Review by moderators (or automated flagging)

### Fair Play Rules

**Penalties**:
- Disconnect/AFK: -50 MMR, 10-minute queue timeout
- Repeated offenses: Escalating bans (1 hour → 24 hours → 7 days → permanent)
- Cheating: Permanent ban

**Honor System** (optional):
- Endorse opponent for good sportsmanship
- Gain honor points → unlock cosmetic rewards

---

## Spectator Mode (Optional)

### Features
- Watch high-MMR matches live
- Fog-of-war (can't see opponent's screen until revealed)
- Free camera mode
- Rewind/replay matches

### Use Cases
- Learn from top players
- Content creation (streamers)
- Tournament broadcasts

---

## Competitive Integrity

### Design Pillars for Ranked

1. **Skill-Based**: Better players win more often
2. **Fair Matchmaking**: Games feel balanced
3. **No Pay-to-Win**: Cosmetics only, no stat advantages
4. **Transparent**: Clear MMR system, no hidden mechanics
5. **Evolving**: Regular balance patches based on data

### Balancing Ranked vs PvE

**Separate Balance Patches**:
- Augments can have different values in PvP
- Some augments only exist in PvE
- Some weapons/spells adjusted for PvP

**Why**: PvE is about fun and power fantasy; PvP is about competitive balance. They have different needs.

---

## Monetization (Optional, Cosmetic Only)

### Ranked-Exclusive Cosmetics

**Battle Pass** (seasonal):
- Free track: Basic rewards (sprays, emotes)
- Paid track ($10): Skins, borders, exclusive augment visuals
- No gameplay advantages, purely cosmetic

**Ranked Cosmetic Shop**:
- Buy with "Ranked Points" (earned from matches)
- Character skins
- Weapon skins
- Emotes, sprays, borders

**Important**: Never sell stat boosts or augments. Cosmetic only.

---

## Technical Implementation

### Networking Requirements

**Recommended**: Photon Fusion or Unity Netcode

**Architecture**: Client-Server (authoritative server)

**Synchronized Data**:
- Player positions (10Hz)
- Player health (on change)
- Enemy spawn events (on spawn)
- Augment selections (on selection)
- Death events (immediate)

**Client-Side Prediction**:
- Movement (smooth, rollback if mispredicted)
- Enemy positions (not critical, server-authoritative)

**Latency Handling**:
- Input buffering (100ms)
- Lag compensation (rewinding world state)
- Interpolation for smooth movement

### Server Costs

**Rough Estimate**:
- 1 match = 2 players = ~15 minutes = ~$0.05 server cost
- 1000 concurrent players = 500 matches = ~$25/hour
- Budget accordingly for player base

**Scaling**:
- Auto-scaling cloud servers (AWS, Google Cloud)
- Regional servers (NA, EU, Asia) for low latency

---

## Leaderboards

### Global Leaderboard
- Top 100 players by MMR
- Updated hourly
- Displays: Rank, Name, MMR, W/L ratio, Main character

### Friends Leaderboard
- Compare with friends
- See who's climbing fastest

### Regional Leaderboards
- NA, EU, Asia, etc.
- Region-specific competition

---

## Tournaments (Future)

### Official Tournaments
- Quarterly tournaments (top 64 players)
- Prize pool (cash or cosmetics)
- Broadcast on Twitch/YouTube

### Community Tournaments
- Tools for community-run events
- Custom lobbies
- Spectator mode support

---

## Future Ranked Ideas

- **Placement Matches**: Play 10 matches to determine starting rank
- **Duo Queue**: Play with a friend in 1v1 (separate leaderboard)
- **Ranked Challenges**: Daily/weekly missions for bonus points
- **Grandmaster Showcases**: Featured matches of top players
- **Custom Game Modes**: Variant rules (double augments, boss rush, etc.)

---

**Related Documents**:
- `/06-Multiplayer/Networking/networking-architecture.md` - Technical networking details
- `/06-Multiplayer/Ranked-Mode/balance-philosophy.md` - PvP balance approach
- `/12-Analytics/ranked-metrics.md` - Tracking ranked health and balance
