# Augment System Design

## Core Philosophy

**Goal**: Create infinite build variety through strategic choices. Every run should feel unique based on augment combinations.

**Inspiration**:
- **Teamfight Tactics**: Augment rarity and choice presentation
- **Mega Bonk**: Build-defining augments with clear synergies
- **Hades**: Boons that modify abilities in interesting ways
- **Path of Exile**: Deep theorycrafting and synergy hunting

---

## Augment Acquisition

### When Players Get Augments

**Trigger**: Every player level-up

**Frequency**:
- Level 2, 3, 4, 5... (every single level)
- Average run to Wave 20: ~15-20 augments
- Max level: Uncapped (endless scaling)

### Choice Presentation

**UI Flow**:
1. Player levels up → game pauses (or slows to 10% speed)
2. Screen darkens, augment choices appear
3. Show 3 random augments with rarity-weighted selection
4. Player clicks to select
5. Augment applied immediately, game resumes

**Visual Design**:
- Card-based UI (like TFT)
- Rarity indicated by border color and glow
- Clear description and stat changes
- Synergy indicators (highlights related augments already taken)

---

## Augment Rarity System

### Rarity Tiers

| Rarity | Drop Rate | Power Level | Color |
|--------|-----------|-------------|-------|
| **Common** | 50% | Small stat boosts | Gray/White |
| **Rare** | 30% | Significant boosts, minor mechanics | Blue |
| **Epic** | 15% | Build-defining, major mechanics | Purple |
| **Legendary** | 5% | Run-winning, transformative | Orange/Gold |

### Rarity Scaling Over Time

**Goal**: Early game has more Commons, late game has more Epics/Legendaries

**Formula**:
```
Legendary Chance = 5% + (PlayerLevel * 0.5%)
Epic Chance = 15% + (PlayerLevel * 0.3%)
Rare Chance = 30% - (PlayerLevel * 0.3%)
Common Chance = 50% - (PlayerLevel * 0.5%)
```

**Example**:
- Level 5: Common 47.5%, Rare 28.5%, Epic 16.5%, Legendary 7.5%
- Level 20: Common 40%, Rare 24%, Epic 21%, Legendary 15%

**Cap**: Legendary never exceeds 20%, Common never below 30%

---

## Augment Categories

### 1. Stat Augments (Simple, Common)

**Goal**: Straightforward power increases

**Examples**:
- **+10% Max Health** (Common)
- **+15% Damage** (Common)
- **+20% Movement Speed** (Common)
- **+10% Attack Speed** (Common)
- **+25% Experience Gain** (Rare)
- **+30% Critical Damage** (Rare)

**Design Philosophy**: Boring but effective. Always useful fallback options.

---

### 2. Weapon Modification Augments

**Goal**: Change how weapons behave

**Examples**:

#### Melee Modifications
- **Extended Reach** (Rare): Melee range +50%
- **Whirlwind** (Epic): Melee attacks hit 360° around you
- **Executioner** (Epic): Melee deals 3x damage to enemies below 20% health
- **Lifesteal Blade** (Rare): Melee attacks heal 10% of damage dealt

#### Ranged Modifications
- **Multishot** (Rare): Fire 2 additional projectiles at 50% damage
- **Piercing Arrows** (Rare): Projectiles pierce through 2 enemies
- **Explosive Arrows** (Epic): Projectiles explode on impact (3m AoE)
- **Homing** (Epic): Projectiles curve toward nearest enemy

#### Magic Modifications
- **Expanded Zone** (Rare): AoE radius +50%
- **Lingering Magic** (Rare): AoE effects last 2x longer
- **Chain Lightning** (Epic): Magic damage chains to 2 nearby enemies
- **Spell Echo** (Legendary): 50% chance to cast spell twice

---

### 3. Spell Modification Augments

**Goal**: Enhance or transform spell abilities

**Examples**:
- **Cooldown Reduction** (Rare): All spell cooldowns -20%
- **Spell Power** (Rare): All spell damage +30%
- **Double Cast** (Legendary): 25% chance to cast spell twice per use
- **Spell Vampire** (Epic): Heal 5% of spell damage dealt
- **Nova on Cast** (Epic): Spells create small AoE explosion on cast
- **Mana Shield** (Epic): Convert 50% of spell damage taken into mana cost instead

---

### 4. On-Hit Effect Augments

**Goal**: Add triggered effects to attacks

**Examples**:
- **Burn on Hit** (Rare): 20% chance to burn enemy (10 dmg/sec for 3s)
- **Freeze on Hit** (Rare): 10% chance to freeze enemy (2s freeze)
- **Shock on Hit** (Rare): 15% chance to shock (chains to 2 enemies)
- **Poison on Hit** (Common): 30% chance to poison (5 dmg/sec for 5s)
- **Knockback** (Rare): Hits push enemies back 2 meters
- **Gold Greed** (Rare): 10% chance enemies drop double gold

---

### 5. Defensive Augments

**Goal**: Increase survivability

**Examples**:
- **Thick Skin** (Common): +15% Damage Reduction
- **Second Wind** (Rare): Heal 30% health when dropping below 20% (60s cooldown)
- **Dodge Chance** (Rare): 10% chance to dodge attacks
- **Thorns** (Rare): Reflect 20% of damage taken
- **Auto-Barrier** (Epic): Gain shield for 20% max health every 30 seconds
- **Death Defiance** (Legendary): Survive lethal damage once per run, heal to 50%

---

### 6. Mobility Augments

**Goal**: Improve movement and positioning

**Examples**:
- **Swift Feet** (Common): +20% Movement Speed
- **Dash Mastery** (Rare): Dash cooldown -50%
- **Phase Dash** (Epic): Dash leaves damaging trail (50 dmg/sec)
- **Blink Strike** (Epic): Dash through enemies, damaging them
- **No Collision** (Legendary): Walk through enemies (take 50% less damage)

---

### 7. Summon/Pet Augments

**Goal**: Add allies or passive damage sources

**Examples**:
- **Summon Familiar** (Epic): Summon a pet that attacks enemies (50 dmg/sec)
- **Spirit Wolves** (Epic): Summon 2 wolves that follow and attack
- **Turret** (Rare): Place stationary turret that shoots enemies (30 dmg/sec, 20s duration, 40s cooldown)
- **Guardian Angel** (Legendary): Summon invincible angel that blocks projectiles

---

### 8. Economy Augments

**Goal**: Increase rewards and meta progression

**Examples**:
- **Treasure Hunter** (Rare): +50% gold drops
- **Experience Boost** (Rare): +25% XP gain
- **Lucky Drop** (Epic): 5% chance for enemies to drop rare items
- **Compound Interest** (Legendary): Gain 1 gold per second per 100 gold held

---

### 9. Synergy Augments (Build-Around)

**Goal**: Create powerful combos with specific builds

**Examples**:

#### Critical Strike Build
- **Assassin's Focus** (Epic): +20% Crit Chance, -20% Max Health
- **Razor Sharp** (Rare): Crits reduce spell cooldowns by 1 second
- **Cascade** (Legendary): Crits have 50% chance to trigger another attack

#### Fire Build
- **Pyromaniac** (Rare): All damage converted to fire damage, +25% fire damage
- **Inferno** (Epic): Enemies burning take 2x damage from all sources
- **Phoenix Rebirth** (Legendary): On death, explode and revive with 50% health (once per run)

#### Tank Build
- **Juggernaut** (Epic): +50% Max Health, -10% Movement Speed
- **Retaliation** (Rare): Deal damage equal to 10% max health when hit
- **Unstoppable** (Legendary): Cannot be slowed, frozen, or stunned

#### Speed Build
- **Velocity** (Epic): +30% Movement Speed, +20% Attack Speed
- **Momentum** (Rare): Gain 1% damage per second of continuous movement (max 50%)
- **Sonic Boom** (Legendary): Moving leaves damaging trail

---

## Synergy System

### How Synergies Work

**Tag System**: Each augment has tags (Fire, Critical, Summon, Defense, etc.)

**Synergy Detection**:
- When picking augment, check for matching tags
- Highlight synergies in UI
- Apply bonus effects for multiple tags

**Example**:
```
Augments Taken:
1. Burn on Hit (Tags: Fire, OnHit)
2. Pyromaniac (Tags: Fire, Damage)
3. Inferno (Tags: Fire, Damage)

Synergy Bonus: "Flame Lord"
- 3 Fire augments → All fire damage +30% extra
- Visual: Character has flame aura
```

### Synergy Tiers

**2-Augment Synergy**: Small bonus (10-15% boost)
**3-Augment Synergy**: Medium bonus (25-30% boost)
**5-Augment Synergy**: Large bonus (50%+ boost, unique mechanic)

**UI Indicator**: Show synergy progress ("Fire: 2/5 for Inferno Lord")

---

## Augment Balance Philosophy

### Power Budget

**Common**: 100 power points
**Rare**: 200 power points
**Epic**: 400 power points
**Legendary**: 800 power points

**Example Conversion**:
- 10% damage = 100 points
- 1% crit chance = 50 points
- 1% movement speed = 25 points
- On-hit effect = 150-300 points

### Negative Trade-offs (High Risk, High Reward)

**Examples**:
- **Glass Cannon** (Legendary): +100% Damage, -50% Max Health
- **Berserker** (Epic): +50% Damage, cannot heal
- **Time Bomb** (Legendary): +200% Damage, die in 5 minutes
- **All In** (Epic): +75% Damage, damage taken +50%

### Augment Exclusions (Mutually Exclusive)

**Example**:
- Can't have both "Pyromaniac" (all fire) and "Ice Mage" (all ice)
- Can't have both "Glass Cannon" and "Juggernaut" (opposing philosophies)

**UI**: Grayed out or doesn't appear if excluded augment taken

---

## Augment Reroll System (Optional)

**Mechanic**: Spend gold to reroll augment choices

**Cost**: 50 gold (scales: 50 → 100 → 200)
**Limit**: 2 rerolls per level-up
**Strategy**: Save rerolls for important levels or hunting specific augments

---

## PvP Augment Adjustments

### Banned in PvP
- Death Defiance (unfair in 1v1)
- Invincibility effects
- Extreme healing (breaks balance)

### PvP-Only Augments
- **Duelist** (Epic): +30% damage vs players, -30% vs enemies
- **Bulwark** (Rare): -20% damage taken from players
- **Executioner's Edge** (Legendary): Instantly kill players below 10% health

### Separate Balance Values
- Some augments have different stats in PvP vs PvE
- Example: "Lifesteal" = 20% in PvE, 5% in PvP

---

## Technical Implementation

### Augment Data Structure

```csharp
[CreateAssetMenu(menuName = "Game/Augment")]
public class AugmentData : ScriptableObject
{
    public string augmentName;
    public string description;
    public AugmentRarity rarity;
    public Sprite icon;

    [Header("Tags")]
    public List<AugmentTag> tags; // Fire, Crit, Summon, etc.

    [Header("Effects")]
    public List<AugmentEffect> effects;

    [Header("Exclusions")]
    public List<AugmentData> exclusiveWith;

    public void Apply(PlayerStats player)
    {
        foreach (var effect in effects)
            effect.ApplyEffect(player);
    }
}
```

### Effect Types

```csharp
public abstract class AugmentEffect
{
    public abstract void ApplyEffect(PlayerStats player);
}

// Example: Stat Modifier
public class StatModifierEffect : AugmentEffect
{
    public StatType stat; // Health, Damage, Speed, etc.
    public float value;
    public ModifierType type; // Additive, Multiplicative

    public override void ApplyEffect(PlayerStats player)
    {
        player.AddModifier(stat, value, type);
    }
}

// Example: On-Hit Effect
public class OnHitEffect : AugmentEffect
{
    public float chance; // 0.0 to 1.0
    public GameObject effectPrefab; // VFX
    public float damage;
    public StatusEffectType statusEffect; // Burn, Freeze, etc.

    public override void ApplyEffect(PlayerStats player)
    {
        player.combat.onHitCallbacks += TriggerEffect;
    }

    private void TriggerEffect(Enemy enemy)
    {
        if (Random.value <= chance)
        {
            enemy.ApplyStatusEffect(statusEffect, damage);
            SpawnVFX(effectPrefab, enemy.transform.position);
        }
    }
}
```

### Synergy Detection

```csharp
public class SynergyManager : MonoBehaviour
{
    private Dictionary<AugmentTag, int> tagCounts = new Dictionary<AugmentTag, int>();
    private List<SynergyBonus> activeBonuses = new List<SynergyBonus>();

    public void OnAugmentAcquired(AugmentData augment)
    {
        foreach (var tag in augment.tags)
        {
            tagCounts[tag]++;
            CheckForSynergies(tag);
        }
    }

    private void CheckForSynergies(AugmentTag tag)
    {
        // Check if tag count hits synergy threshold
        if (tagCounts[tag] == 3)
            ActivateSynergy(tag, SynergyTier.Tier1);
        else if (tagCounts[tag] == 5)
            ActivateSynergy(tag, SynergyTier.Tier2);
    }
}
```

---

## Augment Content Goals

### MVP (Launch)
- **50+ augments total**
  - 25 Common
  - 15 Rare
  - 8 Epic
  - 2 Legendary

### Post-Launch (6 months)
- **100+ augments**
  - Seasonal augments
  - Character-specific augments
  - Community-designed augments

---

## Balancing Augments

### Data to Track
- **Pick Rate**: How often augment is chosen
- **Win Rate**: How often runs with this augment succeed
- **Power Spike**: At what wave does augment shine
- **Synergy Rate**: How often picked with related augments

### Balance Levers
- Adjust rarity (move OP augment from Rare → Legendary)
- Reduce values (30% → 20%)
- Add cooldowns/limitations
- Add trade-offs (gain damage, lose defense)

### Community Feedback
- Weekly balance surveys
- Streamer/content creator input
- Ranked mode data (separate from PvE)

---

## Future Augment Ideas

- **Curse Augments**: Negative effects that make game harder for greater rewards
- **Evolving Augments**: Change form as you level (Rare → Epic → Legendary)
- **Set Augments**: Specific combinations unlock secret bonuses
- **Blessing/Curse System**: Every augment has opposite version
- **Random Augment Events**: Special "Chaos" rounds with randomized augment

---

**Related Documents**:
- `/04-Content-Design/Augments/augment-list.md` - Complete augment database
- `/02-Game-Design/Core-Systems/synergy-system.md` - Synergy mechanics
- `/12-Analytics/augment-balance-tracking.md` - How to track and balance augments
