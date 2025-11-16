# Combat System Design

## Core Combat Philosophy

**Goal**: Make every attack feel impactful while maintaining the fast-paced, screen-filling chaos of survivor-likes.

**Inspirations**:
- **V Rising**: Deliberate combat, ability timing, combos
- **Hades**: Responsive controls, satisfying hit feedback
- **Diablo 3**: Flashy abilities, power fantasy
- **Vampire Survivors**: Overwhelming enemy counts, power escalation

---

## Player Controls

### Movement
- **Input**: WASD (keyboard) or Left Stick (gamepad)
- **Speed**: Base 5 m/s, scales with augments
- **Feel**: Responsive, tight controls (no momentum/drift)
- **Collision**: Pushback from enemies (can't get stuck)

### Aiming
- **Keyboard/Mouse**: Aim with mouse cursor (twin-stick style)
- **Gamepad**: Right stick aims, snap-to-nearest if stick neutral
- **Reticle**: Visible crosshair showing aim direction

### Dodge/Dash
- **Input**: Spacebar or B button
- **Cooldown**: 3 seconds (base)
- **Distance**: 4 meters
- **Duration**: 0.3 seconds
- **I-frames**: 0.2 seconds of invincibility
- **Visual**: Trail effect, whoosh sound

---

## Weapon System

### Weapon Types

#### 1. Melee (Close Range)
**Examples**: Sword, Axe, Spear

**Behavior**:
- Attack in cone/arc in front of player
- Hits all enemies in range
- High damage, short range
- Visual: Slash VFX, weapon trail

**Stats**:
- Damage: 50 (base)
- Range: 2 meters
- Attack Speed: 1.5 attacks/sec
- Cleave: 180° arc

**Playstyle**: High risk, high reward. Get close for maximum damage.

#### 2. Ranged (Projectile)
**Examples**: Bow, Crossbow, Guns

**Behavior**:
- Fire projectiles toward aim direction
- Projectiles travel until hitting enemy or max range
- Can pierce enemies with augments
- Visual: Arrow/bullet projectile, muzzle flash

**Stats**:
- Damage: 30 (base)
- Range: 15 meters
- Attack Speed: 2.0 attacks/sec
- Projectile Speed: 20 m/s
- Pierce: 0 (base)

**Playstyle**: Safe, consistent damage from distance. Kite enemies.

#### 3. Magic (Area Effect)
**Examples**: Staff, Wand, Tome

**Behavior**:
- Create AoE effects around player or at cursor
- Linger effects (fire pools, ice zones)
- Multi-target damage
- Visual: Spell circles, elemental effects

**Stats**:
- Damage: 25 (base, ticks every 0.5s)
- Range: 8 meters
- Attack Speed: 1.0 casts/sec
- AoE Radius: 3 meters
- Duration: 2 seconds

**Playstyle**: Zone control, consistent AoE damage. Positioning-focused.

#### 4. Summoner (Minions)
**Examples**: Necromancer Staff, Spirit Totems

**Behavior**:
- Summon autonomous minions that attack enemies
- Max summons cap (3-5 base)
- Minions follow player
- Visual: Summon animation, minion models

**Stats**:
- Summon Health: 100
- Summon Damage: 15/hit
- Summon Attack Speed: 1.0/sec
- Max Summons: 3 (base)
- Summon Duration: Permanent (until killed)

**Playstyle**: Passive damage, pet management. Safe and consistent.

#### 5. Hybrid (Combo Weapons)
**Examples**: Spellblade, Gunblade

**Behavior**:
- Alternates between melee and ranged attacks
- Combo system (3-hit melee → ranged finisher)
- Visual: Mix of weapon trail and projectiles

**Stats**:
- Melee Damage: 40
- Ranged Damage: 30
- Attack Speed: 2.0/sec
- Range: Melee 2m, Ranged 10m

**Playstyle**: Flexible, adaptive to situation. Rewards combo execution.

---

## Spell System

### Spell Slots
- **Max Slots**: 4 (unlocked progressively: start with 2, unlock 3rd at Wave 10, 4th at Wave 20)
- **Cooldowns**: Individual per spell (5-30 seconds)
- **Casting**: Instant cast (no channels for pacing)

### Spell Categories

#### Offensive Spells
**Goal**: Burst damage, combo with weapons

- **Fireball**: Launch explosive projectile
  - Damage: 150
  - AoE: 4 meters
  - Cooldown: 8 seconds

- **Lightning Strike**: Instant damage at cursor
  - Damage: 200
  - AoE: 2 meters
  - Cooldown: 10 seconds
  - Bonus: Chain to nearby enemies

- **Frost Nova**: Freeze enemies around player
  - Damage: 50
  - AoE: 6 meters
  - Duration: 2 seconds freeze
  - Cooldown: 12 seconds

#### Defensive Spells
**Goal**: Survivability, create space

- **Barrier**: Absorb damage shield
  - Shield: 200 HP
  - Duration: 5 seconds
  - Cooldown: 15 seconds

- **Teleport**: Instant repositioning
  - Range: 10 meters
  - I-frames: 0.3 seconds
  - Cooldown: 10 seconds

- **Time Slow**: Slow all nearby enemies
  - AoE: 10 meters
  - Slow: 50%
  - Duration: 4 seconds
  - Cooldown: 20 seconds

#### Utility Spells
**Goal**: Enhance capabilities, support builds

- **Blood Rage**: Increase damage, reduce defense
  - Damage Boost: +50%
  - Defense: -25%
  - Duration: 8 seconds
  - Cooldown: 20 seconds

- **Life Steal Aura**: Heal on damage dealt
  - Life Steal: 20% of damage
  - AoE: 5 meters (affects player)
  - Duration: 10 seconds
  - Cooldown: 25 seconds

- **Summon Spirit**: Temporary strong ally
  - Summon Health: 500
  - Summon Damage: 50/hit
  - Duration: 15 seconds
  - Cooldown: 30 seconds

---

## Combo System

### Weapon + Spell Synergies

**Design Goal**: Reward players for timing spells with weapon attacks.

**Examples**:
- **Melee + Frost Nova**: Freeze enemies → guaranteed melee hits
- **Ranged + Lightning Strike**: Weaken enemies → finish with arrows
- **Magic Staff + Fire Spell**: Double fire damage (synergy bonus)

### Combo Multiplier (Optional System)

**Trigger**: Hit enemies without getting hit
- 10 hits: 1.1x damage multiplier
- 25 hits: 1.25x multiplier
- 50 hits: 1.5x multiplier
- Resets on taking damage

**Visual**: Combo counter on HUD, screen effects at milestones

---

## Damage Types & Resistances

### Damage Types
1. **Physical**: Melee weapons, projectiles
2. **Magic**: Spells, elemental effects
3. **True Damage**: Ignores resistances (rare)

### Enemy Resistances (Optional Complexity)

**Example**:
- Armored Knight: 50% Physical resistance, 0% Magic resistance
- Mage Enemy: 0% Physical, 50% Magic resistance
- Boss: 25% all resistances

**UI**: Damage numbers color-coded (white = normal, red = reduced, orange = bonus)

---

## Critical Hits & Status Effects

### Critical Hits
- **Base Chance**: 5%
- **Damage Multiplier**: 2x
- **Visual**: Larger damage number, special sound, brief slow-mo (0.1s)
- **Can be increased**: Augments like "Critical Strike Chance +10%"

### Status Effects

**Burn (Fire)**:
- Damage over time: 10/sec for 3 seconds
- Visual: Fire particles on enemy

**Freeze (Ice)**:
- Stop movement: 2 seconds
- Visual: Blue ice effect, shatter on death

**Shock (Lightning)**:
- Chain damage: Spreads to 2 nearby enemies
- Visual: Lightning arc between enemies

**Poison**:
- Damage over time: 5/sec for 5 seconds
- Stacks up to 3x
- Visual: Green bubbling effect

**Bleed (Physical)**:
- Damage per movement: 2 damage per meter moved
- Duration: 5 seconds
- Visual: Red blood trail

---

## Hit Feedback & Game Feel

### Visual Feedback
- **Damage Numbers**: Float up from enemy, color-coded by damage type
- **Hit VFX**: Slash marks, impact sparks, blood splatter (age-appropriate)
- **Enemy React**: Flinch animation, knockback on heavy hits
- **Screen Shake**: Subtle shake on player damage, bigger on critical hits

### Audio Feedback
- **Hit Sound**: Satisfying "thwack" or "slash" sound
- **Crit Sound**: Deeper, more impactful sound
- **Spell Cast**: Unique sound per spell (whoosh, crackle, boom)
- **Enemy Death**: Death cry, satisfying thud

### Tactile Feedback (Gamepad)
- **Light Rumble**: On weapon hit
- **Heavy Rumble**: On taking damage
- **Pulse Rumble**: During ability cast

### Hit Stop (Frame Freeze)
- **On Critical**: 0.05 seconds freeze for impact
- **On Kill**: Slight time dilation (0.1s at 50% speed)
- **Toggle**: Option in settings (some players dislike hit stop)

---

## Difficulty Scaling

### Enemy Stats Progression

**Wave-Based Scaling**:
```
Wave 1:  Enemy Health = 100, Damage = 10
Wave 10: Enemy Health = 250, Damage = 20
Wave 20: Enemy Health = 500, Damage = 35
Wave 30: Enemy Health = 1000, Damage = 50
```

**Formula**:
```
Health = BaseHealth * (1 + (Wave * 0.15))
Damage = BaseDamage * (1 + (Wave * 0.1))
```

### Enemy Count Scaling

**Enemies Per Wave**:
```
Wave 1:  10 enemies
Wave 10: 50 enemies
Wave 20: 100 enemies
Wave 30: 200 enemies
```

### Player Power Scaling

**Must match or exceed enemy scaling**:
- Augments provide 20-50% power per level
- Weapons upgrades provide 2x-3x power by Wave 20
- Spell upgrades via augments

**Balance Goal**: Player feels increasingly powerful, but challenge remains

---

## Combat Balancing Principles

1. **Player Should Win Most Encounters**: This is a power fantasy, not Dark Souls
2. **Skill Should Matter**: Dodging, positioning, ability timing increase success
3. **Builds Should Feel Different**: A crit build plays differently than a tank build
4. **No Mandatory Meta**: Multiple viable strategies
5. **Comeback Mechanics**: Player can recover from mistakes (healing drops, defensive spells)

---

## PvP Combat Adjustments (Ranked Mode)

### Differences from PvE

**Damage Scaling**:
- All damage reduced 50% in PvP (otherwise instant kills)
- Spell cooldowns increased 50%
- Dodge cooldown reduced (more mobility)

**Banned Augments**:
- "Invincibility on spawn"
- "Instant kill chance"
- Any augment that removes player agency

**PvP-Specific Augments**:
- "Anti-Player Damage +20%"
- "Reduce incoming player damage 10%"
- "Steal health on player hit"

**Balance Separately**: PvP and PvE have different augment pools and values

---

## Technical Implementation Notes

### Hit Detection Methods

**Melee**: `Physics.OverlapSphere` in arc
```csharp
Collider[] hits = Physics.OverlapSphere(player.position, range, enemyLayer);
foreach (var hit in hits)
{
    if (IsInArc(hit.transform.position, player.forward, 180f))
        hit.GetComponent<Health>().TakeDamage(damage);
}
```

**Projectile**: Raycasts or moving colliders
```csharp
RaycastHit hit;
if (Physics.Raycast(origin, direction, out hit, range, enemyLayer))
{
    hit.collider.GetComponent<Health>().TakeDamage(damage);
}
```

**AoE**: `Physics.OverlapSphere` at point
```csharp
Collider[] hits = Physics.OverlapSphere(spellPosition, aoeRadius, enemyLayer);
foreach (var hit in hits)
    hit.GetComponent<Health>().TakeDamage(damage);
```

---

## Future Combat Expansion Ideas

- **Weapon Ultimate Abilities**: Super powerful attack every 60 seconds
- **Parry/Block System**: Timed defensive mechanic
- **Elemental Combos**: Fire + Ice = Steam (bonus effect)
- **Weapon Switching**: Equip 2 weapons, swap on hotkey
- **Execution Moves**: Finish low-health enemies with bonus reward

---

**Related Documents**:
- `/04-Content-Design/Weapons/weapon-list.md` - All weapon designs
- `/04-Content-Design/Spells/spell-list.md` - All spell designs
- `/02-Game-Design/Augments/augment-system.md` - How augments modify combat
