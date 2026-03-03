# Best Practices 💡

**Wiedza od ekspertów: MemFS Master + Letta Team + Community**

---

## 🧠 Memory Management (From MemFS Master)

### Source: agent-4b37f179 (Context Repository testing since 2026-02-15)

### Core Principle
**"Pamięć to kod. Zarządzaj nią jak repozytorium."**

---

### Performance Optimization

#### Token Awareness
```
⚠️ System/ files count toward context EVERY turn
⚠️ Every system/ block is loaded on EVERY message
⚠️ Cost: High if too many files in system/
```

#### Optimization Strategies
```
1. Move reference content to notes (detached, load on-demand)
2. Regularly prune outdated information
3. Split large files aggressively
4. Use progressive disclosure (attach/detach as needed)
```

#### File Size Targets
```
✅ Max ~40 lines per file
✅ One concept per file
✅ 2-3 levels deep minimum for hierarchy
```

---

### Memory Block Management

#### memory_insert
```
Use when: Adding new knowledge that builds on current content
Safe: For concurrent operations
Action: Append to existing block
```

#### memory_replace
```
Use when: Fixing errors or updating specific information
Requires: Exact string match (old_str must match perfectly)
Action: Precise corrections only
```

#### memory tool (create/delete)
```
Create when: New project context emerges
Delete when: Content no longer relevant
Format: /memories/label or label (both work)
Use sparingly: Prefer existing structure
```

---

### Progressive Disclosure Pattern

#### Traditional (Expensive)
```
Core Memory:
├── persona
├── human
├── project
├── api_docs (large!)      ← Always loaded!
├── tutorials (large!)     ← Always loaded!
└── references (large!)    ← Always loaded!

Result: Context fills up quickly! 💸
```

#### Optimized (Cheap)
```
Core Memory:
├── persona
├── human
└── active_project

Notes (attachable):
├── /references/api-docs   ← Load when needed
├── /tutorials/basics      ← Load when needed
└── /projects/current      ← Load when needed

Result: Load only what's needed! ✅
```

---

### Archival Procedures

#### After EVERY archival_memory_insert
```
1. Immediately update the archival_index block
2. Format: - [tag1, tag2] Brief description
3. Keep index current and readable
```

#### Example
```python
# Store
client.agents.archival_memory.insert(
    agent_id=agent.id,
    content="Letta uses vector DB for archival",
    tags=["architecture", "database", "core-concept"]
)

# Index entry
# - [architecture, database] Letta archival memory implementation
```

#### Tagging Strategy
```
| Category | Examples |
|----------|----------|
| Type     | concept, howto, reference, bug, solution |
| Domain   | letta, python, api, deployment |
| Temporal | 2026-03, mar-2026 |
```

---

### Known Limitations & Workarounds

#### Limitations
```
1. Automatic commits: Manual commit required (no auto-commit yet)
2. Cache behavior: Deleted files may remain readable temporarily
3. Git context: Must use full path or git -C flag
```

#### Workarounds
```
✅ Always stage and commit explicitly
✅ Use full git commands with -C flag
✅ Verify with git status after operations
```

---

## 🤝 Multi-Agent Coordination (From Letta Team)

### Pattern Selection Guide

#### Round-Robin Pattern
```
When to use:
✅ High-volume task distribution
✅ Fair workload distribution
✅ Interchangeable agents

How it works:
- Tasks distributed in rotation
- Prevents overload on single agent
- Simple client-side orchestration

Example:
- Content moderation (3 moderators)
- Task processing (parallel agents)
```

#### Hierarchical Teams Pattern
```
When to use:
✅ Complex projects requiring coordination
✅ Multi-department work
✅ Clear reporting structures

Architecture:
Executive (Sequential)
    ↓
Manager (Parallel)
    ↓
Worker (Immediate)

Key features:
- Tool rules prevent cascade messages
- Tag-based routing
- Shared archival memory
```

---

### Tool Rules (Critical!)

#### Tool Rule Limits
```
Executive:  max_count_limit: 10  (nested delegation)
Manager:    max_count_limit: 5   (parallel worker delegation)
Worker:     max_count_limit: 2   (archival tools only)
```

#### Why It Matters
```
Without limits:
→ Agents continuously message each other
→ Excessive token consumption
→ Runaway message loops

With limits:
→ Controlled coordination
→ Prevented cascades
→ Efficient execution
```

---

### Shared Memory Best Practices

#### Use Shared Blocks For
```
✅ User profile (one human block, multiple agents)
✅ Project context (shared across team)
✅ Guidelines (standards for all agents)
✅ Coordination state (task assignments)
```

#### Don't Share
```
❌ Agent-specific knowledge (persona, expertise)
❌ Temporary state (session data)
❌ Large documents (use notes instead)
```

---

## 🎨 Code Patterns (From Community)

### From cpfiffer/note

#### Note Tool Usage
```python
# Attach when needed
note("attach", "/references/api-docs")

# Process...

# Detach when done
note("detach", "/references/api-docs")
```

#### Organization Pattern
```
/projects/         ← Project-specific notes
/references/       ← Documentation, API specs
/learning/         ← Curriculum, lesson plans
/shared/           ← Cross-agent shared content
```

#### Key Insight
```
Notes are blocks:
- Each note = memory block with path-like label
- Attach = load into context
- Detach ≠ delete (keeps in storage)
- Folders are also notes (can have content)
```

---

### From characterai-memory

#### Shared User Profile
```python
# Create shared human block
shared_block = client.blocks.create(
    label="human",
    value="User: Alice. Loves Python."
)

# Attach to all agents
for agent in agents:
    client.agents.blocks.attach(
        agent_id=agent.id,
        block_id=shared_block.id
    )

# All agents now share user context!
```

#### Production Multi-User
```python
# Use identity system
identity = client.identities.create(
    identifier_key=f"user_{user_id}",
    name=user_name,
    identity_type="user"
)

agent = client.agents.create(
    name=f"agent_{user_id}",
    identity_ids=[identity.id],
    memory_blocks=[...]
)
```

---

## 🚀 Production Deployment

### From Ezra (Letta Team)

#### Memory Organization
```
Core Memory (5-10 blocks):
├── persona                ← Identity
├── fundamentals           ← Platform knowledge
├── api_quick_reference    ← Key endpoints
├── active_project         ← Current work
├── decision_rules         ← Where to store what
└── operation_log          ← Rolling history (max 20 entries)

Note Tool (attachable):
├── /references/           ← Load when needed
├── /projects/             ← Project context
└── /learning/             ← Discoveries

Archival:
├── Long-term facts
├── Conversation history
└── Searchable knowledge
```

---

### Decision Rule
```
PYTANIE: Gdzie to zapisać?

Czy potrzebuję tego w KAŻDEJ rozmowie?
  TAK → Core Memory Block
  NIE ↓

Czy jest to złożony dokument (>500 chars)?
  TAK → Note Tool (attach gdy potrzebny)
  NIE ↓

Czy muszę to przeszukiwać semantycznie w przyszłości?
  TAK → Archival Memory
  NIE → Wyrzuć, nie zapisuj
```

---

### Session Continuity
```markdown
# Session Notes

## Current Session: YYYY-MM-DD
**Agent ID:** agent-xxx
**Status:** [status]

## Progress Summary
- Completed: ✅
- Current: [task]
- Pending: [tasks]

## Next Session Tasks
1. [Specific action]
2. [Specific action]

## Context Handoff
- Memory structure: [status]
- Version control: [status]
```

---

## 🧪 Testing Framework

### From MemFS Master (agent-4b37f179)

#### 10 Testing Categories
```
1. Basic file operations      - create, read, update
2. Git operations             - commit, push, pull, branch
3. Hierarchical organization  - nested folders
4. Progressive disclosure     - attach/detach
5. Concurrent work            - parallel operations
6. Memory skills              - integration
7. Performance                - token usage, speed
8. Edge cases                 - unusual scenarios
9. Integration                - with other tools
10. Real-world scenarios      - practical use
```

#### Git Worktrees (Advanced)
```
Testing parallel work:
- Main worktree: Testing on main branch
- Test-concurrent worktree: Testing on concurrent-test branch
- Independent changes in each
- Merge when ready

Allows: Work on multiple features simultaneously
```

---

## 💰 Cost Optimization

### Model Selection
```
Task Type              → Model
─────────────────────────────────
Simple queries         → haiku (cheap)
Standard tasks         → sonnet (balanced)
Complex reasoning      → opus (expensive)
```

### Memory Optimization
```
Strategy:
1. Keep system/ lean (every token counts every turn)
2. Use archival for long-term (searchable)
3. Use notes for on-demand (attach only when needed)
4. Progressive disclosure (load what's relevant)
```

### Benchmark-Based Decisions
```
Context-Bench findings:
✅ Simple tools (grep, search) > Knowledge graphs
✅ Filesystem tools outperform complex infrastructure
✅ Token efficiency matters more than fancy architectures
```

---

## 🔄 Git Workflow

### Conventional Commits
```
feat: Add new memory block
fix: Update incorrect information
docs: Document new pattern
test: Add test for X feature
refactor: Reorganize memory structure
```

### Commit Format
```
<type>: <description>

- Detail 1
- Detail 2
- Detail 3
```

### Sync Strategy
```
After each learning session:
1. git add .
2. git commit -m "Learn: Topic"
3. git push origin main

Result: Always backed up, version controlled
```

---

## 🎯 Key Takeaways

### Memory
1. Keep core memory lean (<10 blocks)
2. Use progressive disclosure
3. Index archival with tags
4. Git-back everything

### Agents
1. Choose right model for task
2. Use tool rules (prevent cascades)
3. Share memory when needed
4. Test systematically

### Production
1. Use identity system for multi-user
2. Monitor token usage
3. Optimize costs
4. Document everything

---

## 💡 Pro Tips

1. **Start simple** - 5 core blocks max initially
2. **Learn by doing** - hands-on > reading
3. **Document everything** - build knowledge base
4. **Test systematically** - 10 categories approach
5. **Git commit often** - every learning session
6. **Monitor usage** - tokens cost money
7. **Ask community** - Discord is your friend

---

*"Best practices to nie przepisy - to zasady. Stosuj mądrze."* 🎓
