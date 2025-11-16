# Unity Project Architecture

## Project Structure

### Folder Organization

```
Assets/
├── _Project/                          # All custom game content
│   ├── Art/
│   │   ├── Characters/
│   │   │   ├── Player/
│   │   │   └── Enemies/
│   │   ├── Environments/
│   │   │   ├── Biomes/
│   │   │   └── Props/
│   │   ├── VFX/
│   │   │   ├── Combat/
│   │   │   ├── Spells/
│   │   │   └── UI/
│   │   ├── UI/
│   │   │   ├── Sprites/
│   │   │   ├── Fonts/
│   │   │   └── Icons/
│   │   └── Materials/
│   │       ├── Characters/
│   │       └── Environment/
│   ├── Audio/
│   │   ├── Music/
│   │   ├── SFX/
│   │   │   ├── Combat/
│   │   │   ├── UI/
│   │   │   └── Ambient/
│   │   └── Mixers/
│   ├── Scripts/
│   │   ├── Core/                      # Core systems
│   │   │   ├── GameManager.cs
│   │   │   ├── EventSystem.cs
│   │   │   ├── ObjectPooling.cs
│   │   │   └── SaveSystem.cs
│   │   ├── Player/
│   │   │   ├── PlayerController.cs
│   │   │   ├── PlayerStats.cs
│   │   │   ├── PlayerInput.cs
│   │   │   └── PlayerAnimationController.cs
│   │   ├── Combat/
│   │   │   ├── Weapons/
│   │   │   ├── Spells/
│   │   │   ├── DamageSystem.cs
│   │   │   └── HitDetection.cs
│   │   ├── Enemies/
│   │   │   ├── EnemyBase.cs
│   │   │   ├── EnemyAI.cs
│   │   │   ├── EnemyTypes/
│   │   │   └── EnemySpawner.cs
│   │   ├── Progression/
│   │   │   ├── ExperienceSystem.cs
│   │   │   ├── LevelingSystem.cs
│   │   │   ├── AugmentSystem.cs
│   │   │   └── MetaProgression.cs
│   │   ├── UI/
│   │   │   ├── HUD/
│   │   │   ├── Menus/
│   │   │   └── UIManager.cs
│   │   ├── Multiplayer/
│   │   │   ├── NetworkManager.cs
│   │   │   ├── Matchmaking.cs
│   │   │   └── RankedSystem.cs
│   │   ├── Data/                      # ScriptableObjects
│   │   │   ├── CharacterData.cs
│   │   │   ├── WeaponData.cs
│   │   │   ├── SpellData.cs
│   │   │   ├── AugmentData.cs
│   │   │   └── EnemyData.cs
│   │   └── Utilities/
│   │       ├── Extensions.cs
│   │       ├── Helpers.cs
│   │       └── Constants.cs
│   ├── Prefabs/
│   │   ├── Characters/
│   │   ├── Enemies/
│   │   ├── Weapons/
│   │   ├── VFX/
│   │   └── UI/
│   ├── Scenes/
│   │   ├── _Persistent/               # DontDestroyOnLoad managers
│   │   ├── MainMenu.unity
│   │   ├── CharacterSelect.unity
│   │   ├── Gameplay/
│   │   │   ├── Arena_Biome1.unity
│   │   │   ├── Arena_Biome2.unity
│   │   │   └── Arena_Biome3.unity
│   │   └── Testing/                   # Dev testing scenes
│   ├── Data/                          # ScriptableObject instances
│   │   ├── Characters/
│   │   ├── Weapons/
│   │   ├── Spells/
│   │   ├── Augments/
│   │   ├── Enemies/
│   │   └── GameSettings/
│   └── Resources/                     # Runtime loaded assets
│       └── Configurations/
├── Plugins/                           # Third-party plugins
│   ├── Networking/
│   ├── Analytics/
│   └── Utilities/
├── Settings/                          # Unity project settings
└── TextMesh Pro/                      # TMP essentials
```

---

## Core Architecture Patterns

### 1. Entity Component System (Hybrid)

**Approach**: Use Unity's GameObject/Component model with ECS-like patterns for performance-critical systems.

```csharp
// Example: Stats Component
public class StatsComponent : MonoBehaviour
{
    [SerializeField] private EntityStats baseStats;
    private EntityStats currentStats;
    private List<StatModifier> modifiers = new List<StatModifier>();

    public void AddModifier(StatModifier mod) { /* ... */ }
    public void RecalculateStats() { /* ... */ }
}

// Example: Health Component
public class HealthComponent : MonoBehaviour
{
    private StatsComponent stats;
    private float currentHealth;

    public void TakeDamage(float amount) { /* ... */ }
    public void Heal(float amount) { /* ... */ }
}
```

**Why**:
- Easy to understand and debug
- Works well with Unity's tools
- Can optimize critical paths later with DOTS if needed

### 2. ScriptableObject-Based Data Architecture

**All game content defined as ScriptableObjects**:

```csharp
[CreateAssetMenu(menuName = "Game/Weapon")]
public class WeaponData : ScriptableObject
{
    public string weaponName;
    public WeaponType type;
    public float baseDamage;
    public float attackSpeed;
    public GameObject prefab;
    public Sprite icon;
    // ... more data
}
```

**Benefits**:
- Designer-friendly (edit in Inspector)
- Easy to balance (no code changes)
- Hot-reloadable
- Version control friendly

### 3. Event-Driven Architecture

**Global Event System**:

```csharp
// Events.cs
public static class GameEvents
{
    public static event Action<int> OnPlayerLevelUp;
    public static event Action<EnemyBase> OnEnemyKilled;
    public static event Action<float> OnPlayerDamaged;
    public static event Action<AugmentData> OnAugmentSelected;
    // ... more events
}

// Usage
GameEvents.OnEnemyKilled?.Invoke(enemy);
GameEvents.OnPlayerLevelUp += HandleLevelUp;
```

**Why**:
- Decouples systems
- Easy to add new features
- Great for UI updates and reactions

### 4. Manager Pattern

**Core Managers (Singleton or Service Locator)**:

```csharp
public class GameManager : MonoBehaviour
{
    public static GameManager Instance { get; private set; }

    public WaveManager WaveManager { get; private set; }
    public ProgressionManager ProgressionManager { get; private set; }
    public UIManager UIManager { get; private set; }

    private void Awake()
    {
        if (Instance != null) Destroy(gameObject);
        else Instance = this;
        DontDestroyOnLoad(gameObject);

        InitializeManagers();
    }
}
```

**Key Managers**:
- GameManager (orchestrates everything)
- WaveManager (enemy spawning, difficulty)
- ProgressionManager (XP, leveling, augments)
- UIManager (screen management)
- AudioManager (sound/music)
- SaveManager (persistence)
- InputManager (input abstraction)

### 5. Object Pooling for Performance

**Critical for hundreds of enemies**:

```csharp
public class ObjectPool<T> where T : Component
{
    private Queue<T> pool = new Queue<T>();
    private T prefab;
    private Transform parent;

    public T Get() { /* ... */ }
    public void Return(T obj) { /* ... */ }
}

// Usage
public class EnemySpawner : MonoBehaviour
{
    private ObjectPool<Enemy> enemyPool;

    public void SpawnEnemy(Vector3 position)
    {
        Enemy enemy = enemyPool.Get();
        enemy.transform.position = position;
        enemy.Initialize();
    }
}
```

**Pool Everything**:
- Enemies
- Projectiles
- VFX particles
- Damage numbers
- Experience orbs

---

## Core Systems Design

### Player System

**Components**:
- `PlayerController` - Movement, input handling
- `PlayerCombat` - Weapon management, spell casting
- `PlayerStats` - Health, damage, speed, etc.
- `PlayerProgression` - XP, leveling
- `PlayerInventory` - Weapons, spells, augments

**Input System**:
- Use Unity's new Input System
- Support keyboard/mouse and gamepad
- Input actions: Move, Aim, Attack, Spell1-4, Dash, Pause

### Combat System

**Damage Flow**:
```
Attacker (Weapon/Spell) → DamageInfo → HitDetection → Defender (Health)
```

**DamageInfo Structure**:
```csharp
public struct DamageInfo
{
    public GameObject source;
    public float baseDamage;
    public DamageType type; // Physical, Magic, True
    public bool isCritical;
    public Vector3 hitPoint;
    public Vector3 hitNormal;
}
```

**Hit Detection**:
- Raycasts for projectiles
- Sphere/capsule overlaps for melee
- Layermasks to optimize checks
- Damage numbers spawned on hit

### Enemy System

**Base Enemy Class**:
```csharp
public abstract class EnemyBase : MonoBehaviour
{
    protected EnemyData data;
    protected HealthComponent health;
    protected EnemyAI ai;

    public abstract void Initialize(EnemyData data);
    public abstract void OnDeath();
}
```

**AI System**:
- Simple state machine (Idle, Chase, Attack, Dead)
- NavMesh for pathfinding (or custom grid-based)
- Target acquisition (find nearest player)
- Attack patterns per enemy type

**Spawning**:
- Wave-based spawning
- Spawn zones around arena
- Difficulty scaling (more enemies, stronger variants)
- Boss spawning logic

### Augment System

**Augment Application**:
```csharp
[CreateAssetMenu(menuName = "Game/Augment")]
public class AugmentData : ScriptableObject
{
    public string augmentName;
    public string description;
    public AugmentRarity rarity;
    public Sprite icon;
    public List<AugmentEffect> effects;

    public void Apply(PlayerStats stats)
    {
        foreach (var effect in effects)
            effect.Apply(stats);
    }
}

// Example effect
public class StatModifierEffect : AugmentEffect
{
    public StatType stat;
    public float value;
    public ModifierType type; // Additive, Multiplicative

    public override void Apply(PlayerStats stats)
    {
        stats.AddModifier(new StatModifier(stat, value, type));
    }
}
```

**Synergy System**:
- Check for tag combinations
- Apply bonus effects when tags match
- Example: "Fire" + "Fire" + "Fire" → "Inferno" bonus

### Wave System

**Wave Manager**:
```csharp
public class WaveManager : MonoBehaviour
{
    private int currentWave = 0;
    private float waveTimer;
    private List<EnemySpawnData> currentSpawnList;

    public void StartWave()
    {
        currentWave++;
        GenerateSpawnList();
        BeginSpawning();
    }

    private void GenerateSpawnList()
    {
        // Based on wave number, difficulty curve, biome
        // Example: Wave 5 = 20 melee, 10 ranged, 1 boss
    }
}
```

**Difficulty Scaling**:
- Enemy count increases
- Enemy stats scale (health, damage)
- New enemy types introduced
- Boss frequency increases

---

## Performance Optimization Strategy

### Target Performance
- **60 FPS** with 200+ enemies on screen
- **30 FPS minimum** in worst case (500+ enemies)

### Optimization Techniques

**1. Object Pooling** (covered above)

**2. GPU Instancing**
- Use GPU instancing for enemy meshes
- Shared materials with GPU instancing enabled
- Reduces draw calls dramatically

**3. LOD (Level of Detail)**
- 3 LOD levels for characters
- Distant enemies use lower poly models
- Aggressive culling based on distance

**4. Occlusion Culling**
- Bake occlusion data for environments
- Disable rendering for off-screen objects

**5. Physics Optimization**
- Use layers and layer masks
- Reduce physics timestep frequency
- Simple colliders (spheres/capsules)
- Consider disabling physics for distant enemies

**6. Update Loop Optimization**
```csharp
// Instead of Update() for every enemy
public class EnemyUpdateManager : MonoBehaviour
{
    private List<EnemyBase> enemies = new List<EnemyBase>();

    private void Update()
    {
        // Update enemies in batches
        // Or stagger updates (update 1/3 each frame)
        for (int i = 0; i < enemies.Count; i++)
        {
            if (i % 3 == Time.frameCount % 3)
                enemies[i].CustomUpdate();
        }
    }
}
```

**7. Spatial Partitioning**
- Grid-based for enemy queries
- Only check nearby enemies for AI
- Broadphase before expensive checks

**8. Asset Optimization**
- Texture atlasing
- Compressed textures
- Mesh optimization (reduce verts)
- Audio compression

---

## Networking Architecture (For Ranked Mode)

### Recommended Solution: **Photon Fusion** or **Unity Netcode for GameObjects**

**Architecture**: Client-Server (Authoritative Server)

**Why**:
- Prevents cheating
- Centralized game state
- Fair gameplay

### Network Flow
```
Player 1 Client → Server → Player 2 Client
```

**What to Synchronize**:
- Player positions
- Player health
- Enemy spawn events (server-authoritative)
- Augment selections
- Death events

**What NOT to Synchronize**:
- Individual enemy positions (client-side prediction)
- VFX/SFX (local only)
- UI state

### Ranked System Design

**ELO/MMR System**:
- Starting MMR: 1000
- Win: +20-30 MMR
- Loss: -20-30 MMR
- Matchmaking within ±50 MMR range

**Server Authority**:
- Server spawns all enemies
- Server validates kills
- Server determines winner
- Client sends inputs only

---

## Data Persistence

### Save System

**What to Save**:
- Unlocked characters
- Unlocked weapons/spells
- Meta currency amount
- Permanent upgrades purchased
- Statistics (runs, kills, time played)
- Settings (volume, controls, graphics)

**Save Format**: JSON (serialized with Unity's JsonUtility or Newtonsoft.Json)

**Save Location**:
- `Application.persistentDataPath`
- Cloud save (optional, Steam Cloud, Epic Cloud)

**Save Structure**:
```csharp
[System.Serializable]
public class SaveData
{
    public List<string> unlockedCharacters;
    public List<string> unlockedWeapons;
    public int currency;
    public Dictionary<string, bool> achievements;
    public PlayerStats statistics;
    public SettingsData settings;
}
```

---

## Third-Party Asset Recommendations

### Must-Have
- **DOTween**: Tweening animations (UI, VFX)
- **Odin Inspector** (optional): Better inspector and serialization
- **TextMesh Pro**: Already included, for UI text

### Recommended
- **Amplify Shader Editor** or **Shader Graph**: Custom shaders
- **Post Processing Stack**: Visual polish
- **Cinemachine**: Camera control
- **Rewired**: Advanced input (if new Input System insufficient)

### Networking
- **Photon Fusion**: Fast-paced action networking
- **Unity Netcode for GameObjects**: Free, Unity-official

### Audio
- **FMOD** or **Wwise**: Advanced audio (overkill for small team, use Unity Audio Mixer first)

---

## Development Tools & Workflow

### Version Control
- **Git** with **Git LFS** (for large assets)
- `.gitignore` configured for Unity
- **GitHub** or **GitLab** for hosting

### Project Management
- **Trello**, **Jira**, or **Notion** for task tracking
- **Miro** or **FigJam** for design brainstorming

### Testing
- **Unity Test Framework**: Unit tests for critical systems
- **QA sessions**: Weekly playtest builds

### CI/CD
- **Unity Cloud Build** or **GitHub Actions**: Automated builds
- Nightly builds for testing

---

## Next Steps

1. **Set up Unity project** with this folder structure
2. **Implement core player controller** (movement, rotation, camera)
3. **Build basic enemy** (follow player, take damage, die)
4. **Create wave spawner** (spawn X enemies at Y interval)
5. **Add weapon system** (single weapon type)
6. **Playtest and validate feel**

---

**Related Documents**:
- `/03-Technical-Design/Systems/combat-system-tech.md` - Combat implementation details
- `/03-Technical-Design/Systems/networking-architecture.md` - Multiplayer technical design
- `/03-Technical-Design/Performance/optimization-guide.md` - Performance best practices
