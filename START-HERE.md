# START HERE - Game Design Overview

Welcome to your game design repository! This document provides a roadmap to navigate all the planning documentation.

---

## 🎮 What Is This Game?

A **3D isometric action roguelike** that combines:
- **V Rising's** deep combat mechanics (weapons, spells, combos)
- **Vampire Survivors'** addictive wave-based loop
- **Teamfight Tactics'** strategic augment choices
- **Competitive ranked mode** with unique PvP twist

**Core Loop**: Fight waves of enemies → level up → choose augments → build power → eventually die → unlock new content → repeat

---

## 📁 Repository Structure

### Essential Documents (Read First)

1. **`/01-Vision/game-vision.md`**
   - High-level vision, design pillars, success criteria
   - **Start here to understand the "why"**

2. **`/02-Game-Design/Core-Systems/core-loop.md`**
   - Detailed gameplay loop (moment-to-moment, run, long-term)
   - **Start here to understand the "what"**

3. **`/08-Production/roadmap.md`**
   - Development phases, milestones, timelines
   - **Start here to understand the "when" and "how"**

4. **`/03-Technical-Design/Unity-Architecture/project-structure.md`**
   - Unity implementation strategy, architecture patterns
   - **Start here to understand the technical "how"**

---

### System Design Documents

**Combat & Gameplay**:
- `/02-Game-Design/Combat/combat-system.md` - Weapons, spells, damage, feel
- `/02-Game-Design/Augments/augment-system.md` - Build variety, synergies, progression

**Multiplayer**:
- `/06-Multiplayer/Ranked-Mode/ranked-design.md` - Competitive PvP, matchmaking, seasons

**Progression**:
- `/05-Progression/Meta-Progression/progression-systems.md` - Unlocks, currency, long-term goals

---

### Content Design Templates

Use these templates when creating new content:
- `/04-Content-Design/Characters/character-design-template.md`
- (Create similar templates for weapons, spells, augments as needed)

---

### Creative Brainstorming

- `/01-Vision/expansion-ideas.md` - Future features, game modes, content ideas

---

## 🚀 Quick Start Guide

### If You're Starting Development

1. **Read** `/01-Vision/game-vision.md` (15 min)
2. **Read** `/08-Production/roadmap.md` (20 min)
3. **Skim** `/03-Technical-Design/Unity-Architecture/project-structure.md` (10 min)
4. **Set up Unity project** following the folder structure
5. **Start Pre-Production Phase 0** (see roadmap)

### If You're Designing Content

1. **Read** `/02-Game-Design/core-loop.md` (15 min)
2. **Read** relevant system doc (combat, augments, etc.) (20 min)
3. **Use templates** in `/04-Content-Design/` to create new content
4. **Save designs** in appropriate folder

### If You're Brainstorming Ideas

1. **Read** `/01-Vision/game-vision.md` (know the pillars)
2. **Read** `/01-Vision/expansion-ideas.md` (get inspired)
3. **Add your ideas** to expansion-ideas.md or create new docs
4. **Align ideas** with design pillars (satisfying combat, strategic depth, etc.)

---

## 🎯 Design Pillars (Remember These Always)

1. **Satisfying Combat** - Every attack should feel impactful
2. **Strategic Depth** - Meaningful choices, build variety
3. **Clear Progression** - Always working toward something
4. **Competitive Integrity** - Skill-based, fair, rewarding (for ranked mode)

**Every design decision should support at least one pillar.**

---

## 📊 Development Phases Overview

| Phase | Duration | Goal | Key Deliverable |
|-------|----------|------|-----------------|
| **Phase 0: Pre-Production** | 4-8 weeks | Validate concept | Playable prototype |
| **Phase 1: Vertical Slice** | 12-16 weeks | Prove quality | Polished 20-min experience |
| **Phase 2: Core Content** | 16-24 weeks | Build MVP | Feature-complete PvE game |
| **Phase 3: Multiplayer** | 12-20 weeks | Add ranked mode | PvP beta build |
| **Phase 4: Polish & Launch** | 8-12 weeks | Ship quality | 1.0 Release |
| **Phase 5: Post-Launch** | Ongoing | Support & expand | Live service content |

**Total Estimated Time**: 12-18 months (varies by team size)

---

## ✅ Pre-Production Checklist

Before writing any game code, complete these:

### Planning
- [x] Read game vision document
- [x] Read core loop document
- [x] Read technical architecture document
- [ ] Assemble team (or solo dev plan)
- [ ] Set up project management (Trello, Jira, etc.)
- [ ] Create detailed production schedule

### Technical Setup
- [ ] Set up Unity project (version 2022 LTS or newer)
- [ ] Configure version control (Git + Git LFS)
- [ ] Set up folder structure (see technical doc)
- [ ] Install essential packages (TextMesh Pro, Input System, etc.)
- [ ] Create basic scene structure

### Prototype Goals
- [ ] Implement basic player movement (WASD, mouse aim)
- [ ] Create one weapon type (melee or ranged)
- [ ] Implement basic enemy AI (follow player)
- [ ] Create wave spawner (spawn X enemies)
- [ ] Add experience/leveling system
- [ ] Build simple augment selection (3 choices on level up)
- [ ] **Playtest and validate: "Is this fun?"**

**GO/NO-GO Decision**: If prototype isn't fun, iterate or pivot before full production.

---

## 🎨 Content Creation Priority

### MVP Content (Must Have for 1.0)

**Characters**: 3
- 1 Tank (easy, forgiving)
- 1 DPS (balanced, fun)
- 1 Mage (ranged, safe)

**Weapons**: 5 types
- Melee (sword)
- Ranged (bow/gun)
- Magic (staff)
- Summon (necromancer staff)
- Hybrid (spellblade)

**Spells**: 8 abilities
- 3 Offensive (Fireball, Lightning, Frost Nova)
- 3 Defensive (Barrier, Teleport, Time Slow)
- 2 Utility (Blood Rage, Summon Spirit)

**Augments**: 50+
- 25 Common (stat boosts)
- 15 Rare (meaningful upgrades)
- 8 Epic (build-defining)
- 2 Legendary (run-winners)

**Biomes**: 3
- Crimson Forest (starter)
- Frozen Wastes (mid)
- Volcanic Hellscape (late)

**Enemies**: 10 types + 3 bosses

---

## 🧪 Testing & Validation

### What to Test

**Pre-Production**:
- Does combat feel good?
- Is the core loop engaging?
- Can we handle 200+ enemies at 60fps?

**Vertical Slice**:
- Is the game fun for 20 minutes straight?
- Do augments create meaningful choices?
- Is difficulty curve balanced?

**Production**:
- Is there enough content variety?
- Are all characters viable?
- Is meta progression satisfying?

**Beta**:
- Are there game-breaking bugs?
- Is multiplayer stable?
- Is ranked mode fair and fun?

### Feedback Channels
- Internal playtests (weekly)
- Closed alpha (friends, family)
- Closed beta (community sign-ups)
- Open beta (public stress test)
- Streamers/content creators (marketing + feedback)

---

## 📈 Success Metrics

### Development Milestones
- ✅ Prototype complete (Week 8)
- ⬜ Vertical slice complete (Week 24)
- ⬜ Alpha build (Week 48)
- ⬜ Beta build (Week 68)
- ⬜ 1.0 Launch (Week 80)

### Post-Launch KPIs
- **Day 1 Retention**: > 40%
- **Day 7 Retention**: > 20%
- **Average Session**: > 30 minutes
- **Steam Rating**: > 4.0/5.0 stars
- **Ranked Participation**: > 25% of active players

---

## 🛠️ Tools & Resources

### Recommended Unity Assets
- **DOTween**: Animation/tweening
- **TextMesh Pro**: UI text (included)
- **Unity Input System**: Modern input handling
- **Photon Fusion** or **Unity Netcode**: Multiplayer (choose one)
- **Post Processing Stack**: Visual effects
- **Cinemachine**: Camera control

### Project Management
- **Trello** or **Notion**: Task tracking
- **Miro**: Design brainstorming
- **GitHub Projects**: Issue tracking (if using GitHub)

### Communication
- **Discord**: Team chat, community
- **Google Docs**: Shared documents (supplement to this repo)

---

## 🎓 Learning Resources

### Game Design
- "The Art of Game Design: A Book of Lenses" by Jesse Schell
- "Rules of Play" by Katie Salen and Eric Zimmerman
- GDC talks on roguelikes and action games

### Unity Development
- Unity Learn (official tutorials)
- Brackeys (YouTube, Unity basics)
- CodeMonkey (YouTube, game systems)

### Combat Feel
- "Game Feel" by Steve Swink
- Analyze Hades, Diablo 3, V Rising combat

### Balancing
- "Game Balance" by Ian Schreiber
- Data-driven balancing (track stats, iterate)

---

## 💡 Design Philosophy Reminders

### Do's
✅ Prototype fast, iterate often
✅ Focus on feel first, balance later
✅ Playtest constantly (weekly minimum)
✅ Use data to guide balance decisions
✅ Keep scope realistic (cut features if needed)
✅ Prioritize player fun over designer ego

### Don'ts
❌ Add features without purpose (scope creep)
❌ Balance before core feel is right
❌ Ignore playtest feedback
❌ Make assumptions (validate with data)
❌ Commit to features you can't deliver
❌ Forget the design pillars

---

## 🗺️ Next Steps

### Immediate (This Week)
1. Review all essential documents
2. Set up Unity project
3. Create basic prototype scene
4. Implement player movement

### Short-Term (This Month)
1. Complete technical prototype
2. Playtest internally
3. Validate core loop
4. Make GO/NO-GO decision

### Medium-Term (Next 3 Months)
1. Build vertical slice
2. External playtesting
3. Refine based on feedback
4. Prepare for production

---

## 📞 Need Help?

### Questions to Ask Yourself
- "Does this feature support a design pillar?"
- "Can we realistically implement this?"
- "Have we validated this with playtesting?"
- "What's the minimum viable version of this?"

### When Stuck
1. Re-read the vision document (remember the "why")
2. Look at reference games (Vampire Survivors, Hades, V Rising)
3. Playtest what you have (get fresh perspective)
4. Cut scope if needed (better to ship small than not ship at all)

---

## 🎉 You're Ready!

You now have a comprehensive game design plan. Remember:
- **Start small** (prototype first)
- **Iterate constantly** (fail fast, learn faster)
- **Stick to the vision** (but be flexible on execution)
- **Have fun** (if you're not excited, players won't be either)

**Good luck, and happy developing!** 🚀

---

**Last Updated**: 2025-11-16
**Version**: 1.0
**Status**: Pre-Production Planning Complete
