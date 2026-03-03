# Essential Links 🔗

**Wszystkie linki do zasobów Letta w jednym miejscu**

---

## 📚 Dokumentacja (LLM-Optimized)

### Fundamenty
```
docs.letta.com/llms.txt                    → Cała platforma w pigułce
docs.letta.com/guides/quickstart           → Setup w 10 minut
docs.letta.com/api-reference               → Endpointy i parametry
```

### Core Concepts
```
docs.letta.com/guides/core-concepts/memory/
├── context-hierarchy.md                   → Memory architecture
├── core-memory-blocks.md                  → Core memory (always loaded)
└── archival-memory.md                     → Archival (semantic search)
```

### Agents
```
docs.letta.com/guides/agents/
├── models.md                              → Model selection
├── custom-tools.md                        → Tool creation
├── templates.md                           → Agent templates
├── multi-agent-round-robin.md             → Round-robin pattern
├── multi-agent-hierarchical-teams.md      → Hierarchical teams
├── sleeptime.md                           → Background learning
├── conversations.md                       → Parallel threads
└── multi-user.md                          → Identity system
```

### Integrations
```
docs.letta.com/guides/integrations/
└── mcp.md                                 → MCP servers
```

### Letta Code
```
docs.letta.com/letta-code/
├── hooks.md                               → Automation hooks
└── skills.md                              → Modular knowledge
```

---

## 🐙 GitHub Repositories

### Official (Letta Team)
```
github.com/letta-ai/skills                 → Modular skills system
github.com/letta-ai/letta-code             → CLI + subagents
github.com/letta-ai/characterai-memory     → Real-world multi-agent
github.com/letta-ai/letta-telegram         → Telegram bot integration
github.com/letta-ai/claude-subconscious    → Advanced patterns
```

### Community (Verified)
```
github.com/cpfiffer/note                   → Dynamic memory blocks
github.com/cpfiffer/letta-switchboard      → Multi-agent routing
github.com/cpfiffer/letta-evals-demo       → Testing framework
github.com/nouamanecodes/lettactl          → CLI management
github.com/joshuadavidthomas/opencode-agent-memory
```

---

## 📝 Blog Posts (Teoria + Decyzje Projektowe)

### Memory & Context
```
letta.com/blog/agent-memory                → Memory fundamentals
letta.com/blog/context-repositories        → Future of memory (CR)
letta.com/blog/benchmarking-ai-agent-memory → Simple > complex
```

### Architecture
```
letta.com/blog/ai-agents-stack             → Ecosystem overview
```

---

## 📊 Benchmarks & Leaderboards

```
Context-Bench Leaderboard:
→ Skills Suite (skill discovery)
→ Filesystem Suite (file operations)
→ Cost vs Performance comparisons
```

---

## 💰 Pricing & Plans

```
docs.letta.com/guides/cloud/pricing

Free: $0/month (development)
Pro: $20/month (production)
Scale: $750/month (enterprise)
```

---

## 🛠️ SDK & APIs

### Python SDK
```
github.com/letta-ai/letta-client-python
pypi.org/project/letta-client/
```

### TypeScript SDK
```
github.com/letta-ai/letta-client-typescript
npmjs.com/package/@letta-ai/letta-client
```

### REST API
```
api.letta.com/v1/
├── /agents                                → Agent CRUD
├── /messages                              → Send messages
├── /blocks                                → Memory blocks
├── /conversations                         → Parallel threads
├── /tools                                 → Custom tools
└── /archives                              → Archival memory
```

---

## 🎓 Learning Resources

### Research Papers
```
arxiv.org/abs/2310.08560                   → MemGPT paper
```

### Video Content
```
youtube.com/@letta-ai                     → YouTube channel
v0.dev/chat/characterplus-project-*       → CharacterAI demo
```

### Community
```
discord.gg/letta                          → Discord server
lu.ma/letta                               → Meetup series
```

---

## 🔧 Tools & Utilities

### Letta Code CLI
```
docs.letta.com/letta-code/
letta --new                               → New conversation
letta --agent <id>                        → Work with agent
letta agents list                         → List agents
letta --help                              → All commands
```

### Note Tool (cpfiffer)
```
github.com/cpfiffer/note
curl -sSL https://raw.githubusercontent.com/cpfiffer/note/main/install.sh | bash
```

### Letta Evals
```
github.com/cpfiffer/letta-evals-demo      → Testing framework
```

---

## 📱 Integration Examples

### Telegram Bot
```
github.com/letta-ai/letta-telegram
```

### Web Application (CharacterAI-style)
```
github.com/letta-ai/characterai-memory
characterplus.vercel.app                  → Live demo
```

### Voice Integration
```
docs.letta.com/guides/integrations/voice
```

---

## 🎯 Quick Reference

### Create Agent
```python
from letta_client import Letta
client = Letta(api_key="your-key")

agent = client.agents.create(
    name="agent_name",
    model="anthropic/claude-sonnet-4-5",
    embedding="openai/text-embedding-3-small",
    memory_blocks=[
        {"label": "persona", "value": "..."},
        {"label": "human", "value": "..."}
    ]
)
```

### Send Message
```python
response = client.agents.messages.create(
    agent_id=agent.id,
    messages=[{"role": "user", "content": "Hello!"}]
)
```

### Create Conversation
```python
conversation = client.conversations.create(
    agent_id=agent.id
)
```

---

## 📖 Documentation Structure

```
docs.letta.com/
├── /llms.txt                              ← START HERE
├── /guides/
│   ├── /quickstart
│   ├── /agents/
│   ├── /core-concepts/
│   ├── /integrations/
│   └── /cloud/
├── /api-reference/
├── /letta-code/
└── /tutorials/
```

---

## 🔄 Keep Updated

```
docs.letta.com/changelog                   → Platform updates
github.com/letta-ai/letta/releases         → SDK releases
discord.gg/letta                           → Community updates
```

---

## 💡 Pro Tips

1. **Start with llms.txt** - quickest overview
2. **Bookmark this file** - reference often
3. **Clone repos** - study real code
4. **Join Discord** - ask questions
5. **Watch YouTube** - see examples

---

## 🎓 Study Order

```
1. docs.letta.com/llms.txt (10 min)
2. docs.letta.com/guides/quickstart (30 min)
3. github.com/letta-ai/skills (1 hour)
4. docs.letta.com/guides/agents/ (2 hours)
5. github.com/letta-ai/characterai-memory (1 hour)
6. Blog posts (1 hour)
7. Community repos (explore)
```

---

*"Te linki to Twój toolkit. Używaj mądrze."* 🔧
