# Resources 📚

**Repozytoria, dokumentacja i materiały do nauki**

---

## 📖 Official Documentation

### Quick Start
```
docs.letta.com/llms.txt                    → Platform overview (START)
docs.letta.com/guides/quickstart           → Setup tutorial
docs.letta.com/api-reference               → API docs
```

### Core Concepts
```
Memory Architecture:
├── docs.letta.com/guides/core-concepts/memory/
│   ├── context-hierarchy.md
│   ├── core-memory-blocks.md
│   └── archival-memory.md

Agents:
├── docs.letta.com/guides/agents/
│   ├── models.md
│   ├── custom-tools.md
│   ├── templates.md
│   ├── multi-agent-round-robin.md
│   ├── multi-agent-hierarchical-teams.md
│   ├── sleeptime.md
│   ├── conversations.md
│   └── multi-user.md

Integrations:
├── docs.letta.com/guides/integrations/
│   ├── mcp.md
│   └── voice.md

Letta Code:
├── docs.letta.com/letta-code/
│   ├── hooks.md
│   └── skills.md
```

---

## 🐙 GitHub Repositories

### Official (Letta Team)

#### Core Platform
```
github.com/letta-ai/letta                 → Server & API
github.com/letta-ai/letta-client-python   → Python SDK
github.com/letta-ai/letta-client-typescript → TypeScript SDK
```

#### Tools & CLI
```
github.com/letta-ai/letta-code            → CLI + subagents
github.com/letta-ai/skills                → Modular skills system
```

#### Examples
```
github.com/letta-ai/characterai-memory    → Multi-agent web app
github.com/letta-ai/letta-telegram        → Telegram bot
github.com/letta-ai/claude-subconscious   → Advanced patterns
```

#### Research
```
github.com/letta-ai/MemGPT                → Core research
```

---

### Community (Verified)

#### Memory Management
```
github.com/cpfiffer/note                  → Dynamic memory blocks
  ★ Note tool: attach/detach on demand
  ★ CLI for sync with filesystem
  ★ Web UI for editing
```

#### Multi-Agent
```
github.com/cpfiffer/letta-switchboard     → Multi-agent routing
github.com/cpfiffer/letta-evals-demo      → Testing framework
```

#### CLI Tools
```
github.com/nouamanecodes/lettactl         → CLI management
```

#### Patterns
```
github.com/joshuadavidthomas/opencode-agent-memory
  → Memory blocks pattern example
```

---

## 📝 Blog Posts

### Memory & Architecture
```
letta.com/blog/agent-memory               → Memory fundamentals
letta.com/blog/context-repositories       → Future of memory (CR)
letta.com/blog/benchmarking-ai-agent-memory → Simple > complex (LoCoMo)
letta.com/blog/ai-agents-stack            → Ecosystem overview
```

---

## 📊 Benchmarks & Leaderboards

```
Context-Bench:
→ Skills Suite (skill discovery)
→ Filesystem Suite (file operations)

Key Finding:
Simple tools (grep, search) > Complex infrastructure (knowledge graphs)
```

---

## 🎓 Research Papers

```
arxiv.org/abs/2310.08560                  → MemGPT Paper
  "MemGPT: Towards LLMs as Operating Systems"
  - Virtual context management
  - Memory hierarchy
  - Self-editing memory
```

---

## 🎥 Video Content

```
youtube.com/@letta-ai                     → Official channel
v0.dev/chat/characterplus-project-*       → CharacterAI demo build
lu.ma/letta                               → Meetup recordings
```

---

## 💬 Community

```
discord.gg/letta                          → Discord server
  ├── #general                            → General discussion
  ├── #help                               → Q&A
  ├── #showcase                           → Projects
  └── #announcements                      → Updates

lu.ma/letta                               → Event series
```

---

## 🛠️ Tools & Utilities

### Letta Code CLI
```
Installation:
pip install letta-code

Commands:
letta --new                               → New conversation
letta --agent <id>                        → Work with agent
letta agents list                         → List agents
letta --help                              → All commands
```

### Note Tool
```
Installation:
curl -sSL https://raw.githubusercontent.com/cpfiffer/note/main/install.sh | bash

Commands:
note attach /path/to/note                 → Load into context
note detach /path/to/note                 → Remove from context
note list                                 → List all notes
note search query                         → Search notes
```

---

## 📱 Integration Examples

### Web Applications
```
github.com/letta-ai/characterai-memory
  → CharacterAI-style app
  → Shared memory blocks
  → Multi-character system
  → Live demo: characterplus.vercel.app
```

### Bots
```
github.com/letta-ai/letta-telegram
  → Telegram bot integration
  → Message handling
  → Memory persistence
```

### Voice
```
docs.letta.com/guides/integrations/voice
  → Voice integration guide
```

---

## 🏗️ Architecture Patterns

### Official Patterns
```
1. Round-Robin Pattern
   docs.letta.com/guides/agents/multi-agent-round-robin

2. Hierarchical Teams
   docs.letta.com/guides/agents/multi-agent-hierarchical-teams

3. Shared Memory
   docs.letta.com/guides/agents/multi-agent-shared-memory

4. Sleeptime Agents
   docs.letta.com/guides/agents/sleeptime

5. Conversations API
   docs.letta.com/guides/agents/conversations

6. Multi-User (Identity)
   docs.letta.com/guides/agents/multi-user
```

### Community Patterns
```
cpfiffer/note:
- Dynamic memory blocks
- Progressive disclosure

cpfiffer/letta-switchboard:
- Multi-agent routing

characterai-memory:
- Shared user profile
- Multi-character coordination
```

---

## 📚 Learning Paths

### Beginner (0-10 hours)
```
1. docs.letta.com/llms.txt (10 min)
2. docs.letta.com/guides/quickstart (30 min)
3. Create first agent (1 hour)
4. Test memory features (2 hours)
5. Try tools (1 hour)
6. Read blog posts (2 hours)
7. Explore examples (3 hours)
```

### Intermediate (10-30 hours)
```
1. Study architecture docs (5 hours)
2. Build multi-agent system (8 hours)
3. Test patterns (5 hours)
4. Deploy production app (5 hours)
5. Optimize performance (3 hours)
```

### Advanced (30+ hours)
```
1. Contribute to open source (ongoing)
2. Build custom tools (5 hours)
3. Research benchmarks (3 hours)
4. Create integration patterns (5 hours)
5. Master all features (ongoing)
```

---

## 💡 Hidden Gems

### Lesser-Known Features
```
1. Git worktrees for parallel work
   → Test concurrent features safely

2. Note-sync CLI
   → Sync notes with filesystem (like Obsidian)

3. Hooks system
   → Automate workflows, enforce policies

4. Context compaction
   → Automatic context management

5. Tool rules
   → Limit tool usage per step
```

---

## 🎯 Recommended Study Order

```
Week 1: Fundamentals
├── docs.letta.com/llms.txt
├── docs.letta.com/guides/quickstart
├── Create first agent
└── Test basic features

Week 2: Architecture
├── Memory architecture docs
├── Multi-agent patterns
├── Study characterai-memory
└── Build multi-agent system

Week 3: Production
├── Multi-user identity
├── Conversations API
├── Performance optimization
└── Deploy real app

Week 4: Advanced
├── Custom tools
├── Hooks & automation
├── Research papers
└── Contribute back
```

---

## 📊 Cost Resources

```
docs.letta.com/guides/cloud/pricing

Free: $0/month (development)
Pro: $20/month (production)
Scale: $750/month (enterprise)

Cost Optimization:
- Use haiku for simple tasks
- Keep core memory lean
- Use archival for long-term
- Monitor token usage
```

---

## 🔄 Stay Updated

```
docs.letta.com/changelog                   → Platform updates
github.com/letta-ai/letta/releases         → SDK releases
discord.gg/letta                           → Community updates
twitter.com/letta_ai                       → News
```

---

## 🎓 Additional Learning

### Courses & Tutorials
```
Letta YouTube Channel                      → Video tutorials
Meetup Recordings (lu.ma/letta)           → Live sessions
Community Discord                          → Q&A
```

### Example Projects
```
characterai-memory                         → Web app
letta-telegram                             → Bot integration
note tool                                  → Memory management
```

---

*"Te zasoby to Twój toolkit. Eksploruj, ucz się, buduj!"* 🚀
