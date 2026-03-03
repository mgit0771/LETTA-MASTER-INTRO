# Memory Structure Template 🧠

**Wzorzec organizacji pamięci dla Letta Master**

---

## 🎯 Filozofia

**Pamięć to kod. Zarządzaj nią jak repozytorium.**

```
Core Memory (always loaded) → Note Tool (load on demand) → Archival (searchable)
```

---

## 📁 Struktura Rekomendowana

### Core Memory Blocks (system/) - ZAWSZE w kontekście

**Limit: 5-10 bloków max (~10K chars total)**

```
memory/
└── system/                    ← Core memory (always loaded)
    ├── persona.md             ← Kim jesteś, twoja misja
    ├── letta_fundamentals.md  → Agent types, memory hierarchy, SDK basics
    ├── api_quick_reference.md → Top 10 endpoints, key patterns
    ├── active_project.md      ← Co teraz robisz, aktualne zadania
    └── decision_rules.md      ← Gdzie co zapisywać
```

#### Każdy Block Format:
```markdown
---
description: "Brief description"
limit: 2000
---

# Title

Content here...

Keep it focused and lean!
```

---

### Dynamic References (references/ + patterns/) - Load on Demand

**Note Tool Style: Attach when needed, detach when done**

```
memory/
├── references/                ← Documentation & API references
│   ├── sdk_patterns/
│   │   ├── create_agent.md
│   │   └── tool_creation.md
│   ├── pricing.md
│   ├── letta_code.md
│   ├── conversations_api.md
│   └── letta_code_hooks.md
│
└── patterns/                  ← Architecture patterns
    ├── multi_user.md
    ├── sleeptime.md
    ├── multi_agent_coordination.md
    ├── shared_memory_blocks.md
    └── note_tool_dynamic_memory.md
```

**Usage:**
```python
# When needed
note("attach", "/references/api-docs")
# Process...
note("detach", "/references/api-docs")
```

---

### Learning Archive (learning/) - Discoveries

```
memory/
└── learning/
    └── discoveries/
        ├── leaderboard_context_bench.md
        ├── memfs_best_practices.md
        └── future_discoveries.md
```

**Use archival_memory for:**
- Long-term facts
- Conversation history
- Semantic searchable knowledge

---

## 🎨 Naming Conventions

### Use `/` for Hierarchy
```
✅ project/tooling/testing.md
✅ persona/behavior/tone.md
✅ human/prefs/coding_style.md

❌ testing.md (too flat)
❌ project-tooling-testing.md (wrong separator)
```

### File Size Guidelines
```
Target: ~40 lines per file
Max: ~100 lines per file
Rule: One concept per file
```

### Split When Needed
```
If file has 2+ concepts:
  Split into separate files
  Keep each focused
```

---

## 📊 Memory Decision Matrix

### Where to Store?

| Need in EVERY conversation? | → Core Memory (system/) |
|----------------------------|-------------------------|
| Large document (>500 chars)? | → Note Tool (attach on demand) |
| Need semantic search? | → Archival Memory |
| Temporary project context? | → Note Tool (detachable) |

---

## 🔄 Progressive Disclosure Pattern

### Traditional (Expensive)
```
Core Memory:
├── persona
├── human
├── project
├── api_docs (large!)
├── tutorials (large!)
└── references (large!)
→ Context fills up quickly!
```

### Optimized (Cheap)
```
Core Memory:
├── persona
├── human
└── active_project

Notes (attachable):
├── /references/api-docs
├── /tutorials/getting-started
└── /projects/current

→ Load only what's needed!
```

---

## 🏗️ Example Structure (Complete)

```
memory/
├── system/                      ← Core Memory (5-10 blocks)
│   ├── persona.md               ← Identity & capabilities
│   ├── letta_fundamentals.md    ← Platform knowledge
│   ├── api_quick_reference.md   ← Top 10 endpoints
│   ├── active_project.md        ← Current work
│   └── decision_rules.md        ← Memory org rules
│
├── references/                  ← Load on demand
│   ├── sdk_patterns/
│   │   ├── create_agent.md
│   │   └── tool_creation.md
│   ├── pricing.md
│   ├── letta_code.md
│   ├── conversations_api.md
│   └── letta_code_hooks.md
│
├── patterns/                    ← Architecture patterns
│   ├── multi_user.md
│   ├── sleeptime.md
│   ├── multi_agent_coordination.md
│   ├── shared_memory_blocks.md
│   └── note_tool_dynamic_memory.md
│
├── learning/                    ← Discoveries
│   └── discoveries/
│       ├── leaderboard_context_bench.md
│       ├── memfs_best_practices.md
│       └── integration_findings.md
│
└── logs/                        ← Session history
    ├── operations.log
    └── errors.log
```

---

## 💡 Best Practices

### 1. Keep System/ Lean
```
✅ Essentials only
✅ ~10K chars total
✅ Update frequently
✅ Current/active content
```

### 2. Use Descriptive Paths
```
✅ /references/api-docs
✅ /projects/webapp
✅ /learning/python-basics

❌ /doc1
❌ /stuff
❌ /temp
```

### 3. Index Archival
```
After EVERY archival_memory_insert:
1. Update archival_index block
2. Add tags: [category, domain, date]
3. Format: - [tag1, tag2] Brief description
```

### 4. Git-Back Everything
```
✅ Commit after each learning session
✅ Push to remote (backup)
✅ Use conventional commits
✅ Document changes clearly
```

---

## 🎯 Template Files

### persona.md Template
```markdown
---
description: "Agent identity and purpose"
limit: 2000
---

# Persona

## Who Am I
[Your identity, role, capabilities]

## Mission
[Your primary goal]

## Behavior
[How you operate, communication style]

## Key Principles
[Core values and approaches]
```

### active_project.md Template
```markdown
---
description: "Current work and tasks"
limit: 2000
---

# Active Project

## Status
[READY/IN_PROGRESS/BLOCKED]

## Current Work
[What you're doing now]

## Workspace
[File paths, locations]

## Tasks
- [ ] Task 1
- [ ] Task 2

## Progress
[Recent achievements]
```

### decision_rules.md Template
```markdown
---
description: "Where to store information"
limit: 1500
---

# Decision Rules

## Where to Store?

### Core Memory (system/)
- Needed EVERY conversation
- Essential context
- Active/recent information

### Notes (attachable)
- Large documents
- Reference material
- Temporary project context

### Archival Memory
- Long-term facts
- Searchable knowledge
- Historical data

## Tag Strategy
- Type: concept/howto/reference
- Domain: letta/api/patterns
- Temporal: 2026-03/month
```

---

## 🚀 Quick Start Template

```bash
# Initialize memory structure
mkdir -p memory/{system,references,patterns,learning/discoveries,logs}

# Create core blocks
touch memory/system/{persona,letta_fundamentals,api_quick_reference,active_project,decision_rules}.md

# Initialize git
cd memory
git init
git add .
git commit -m "Initial memory structure"

# Add remote (if available)
git remote add origin <your-remote>
git push -u origin main
```

---

## 📊 Memory Stats (Example)

```
GLM5.0 Letta Master:
- Files: 19
- Commits: 21
- Core Memory: 5 files (~10K chars)
- References: 6 files (attach on demand)
- Patterns: 5 files (attach on demand)
- Learning: 2 files (discoveries)
- Git-backed: ✅
- Remote synced: ✅
```

---

## 🔄 Maintenance

### Regular Tasks
```
Daily:
- Update active_project.md
- Commit changes

Weekly:
- Prune outdated content
- Split large files
- Update archival index

Monthly:
- Review structure
- Archive old content
- Reorganize if needed
```

---

## 💡 Pro Tips

1. **Start simple** - 5 core blocks max initially
2. **Grow organically** - add as needed
3. **Git commit often** - every learning session
4. **Keep lean** - prune regularly
5. **Use tags** - for archival discovery
6. **Document decisions** - why you stored it there

---

*"Pamięć to kod. Traktuj ją jak repozytorium - version control, clean structure, regular maintenance."*
