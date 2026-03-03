# First Steps 🚀

**Tutorial: Jak zacząć przygodę z Letta**

---

## 🎯 Step 0: Setup (5 min)

### Get API Key
```
1. Go to app.letta.com
2. Sign up / Login
3. Generate API key
4. Save it securely (you'll need it)
```

### Install SDK
```bash
# Python
pip install letta-client

# TypeScript
npm install @letta-ai/letta-client
```

### Test Connection
```python
from letta_client import Letta

client = Letta(api_key="your-api-key-here")

# Test connection
agents = client.agents.list()
print(f"Connected! Found {len(agents)} agents.")
```

---

## 📚 Step 1: Read Fundamentals (30 min)

### Start Here
```
1. docs.letta.com/llms.txt (10 min)
   → Understand platform overview

2. docs.letta.com/guides/quickstart (20 min)
   → Setup your first agent
```

### Key Concepts to Understand
```
✅ Agent types (letta_v1, memgpt_v2)
✅ Memory blocks (core, archival)
✅ Tools (web_search, run_code)
✅ Embeddings (text-embedding-3-small)
```

---

## 🛠️ Step 2: Create First Agent (15 min)

### Basic Agent
```python
from letta_client import Letta

client = Letta(api_key="your-api-key")

# Create agent
agent = client.agents.create(
    name="my_first_agent",
    model="anthropic/claude-sonnet-4-5",
    embedding="openai/text-embedding-3-small",
    memory_blocks=[
        {
            "label": "persona",
            "value": "I am a helpful AI assistant with memory. I remember our conversations and learn from them."
        },
        {
            "label": "human",
            "value": "User information will be stored here as we interact."
        }
    ]
)

print(f"Created agent: {agent.id}")
```

### Send First Message
```python
response = client.agents.messages.create(
    agent_id=agent.id,
    messages=[{
        "role": "user",
        "content": "Hello! My name is Alice and I love Python programming."
    }]
)

print(response.messages[-1].content)
```

---

## 💾 Step 3: Memory Management (20 min)

### Check Memory Blocks
```python
# List memory blocks
blocks = client.agents.blocks.list(agent_id=agent.id)

for block in blocks:
    print(f"{block.label}: {block.value[:50]}...")
```

### Update Memory
```python
# Update human block
client.agents.blocks.update(
    agent_id=agent.id,
    block_label="human",
    value="User is Alice. Loves Python programming. Interested in AI agents."
)
```

### Use Archival Memory
```python
# Store long-term fact
client.agents.archival_memory.insert(
    agent_id=agent.id,
    content="Alice is working on a project about stateful AI agents with persistent memory.",
    tags=["project", "alice", "ai-agents"]
)

# Search archival
results = client.agents.archival_memory.search(
    agent_id=agent.id,
    query="Alice project",
    tags=["project"]
)

print(results[0].content)
```

---

## 🤖 Step 4: Add Tools (15 min)

### Add Web Search
```python
# Get web_search tool
tools = client.tools.list(name="web_search")
web_search_tool = tools.items[0]

# Attach to agent
client.agents.tools.attach(
    agent_id=agent.id,
    tool_id=web_search_tool.id
)

# Now agent can search the web!
response = client.agents.messages.create(
    agent_id=agent.id,
    messages=[{
        "role": "user",
        "content": "Search for the latest news about AI agents with memory."
    }]
)
```

---

## 📝 Step 5: Build Knowledge Base (30 min)

### Create Memory Structure
```python
# In your memory filesystem
memory/
├── system/
│   ├── persona.md           ← Agent identity
│   ├── letta_fundamentals.md ← What you learned
│   ├── api_quick_reference.md ← Key endpoints
│   └── active_project.md    ← Current work
└── learning/
    └── discoveries/
        └── first_agent.md   ← Document your experience
```

### Document Your Learning
```markdown
# First Agent Experience

## What I Built
- Basic agent with memory blocks
- Added web search tool
- Tested archival memory

## Key Learnings
- Memory blocks persist across conversations
- Archival needs tags for discovery
- Tools extend agent capabilities

## Next Steps
- Try multi-agent coordination
- Add more tools
- Test conversations API
```

---

## 🎨 Step 6: Try Patterns (45 min)

### Pattern 1: Conversations (Parallel Threads)
```python
# Create conversation
conversation = client.conversations.create(
    agent_id=agent.id
)

# Send message in conversation
response = client.conversations.messages.create(
    conversation.id,
    messages=[{"role": "user", "content": "Hello!"}]
)
```

### Pattern 2: Shared Memory
```python
# Create shared block
shared_block = client.blocks.create(
    label="project_context",
    value="Project: Building AI assistant with memory"
)

# Attach to multiple agents
client.agents.blocks.attach(agent_id=agent1.id, block_id=shared_block.id)
client.agents.blocks.attach(agent_id=agent2.id, block_id=shared_block.id)

# Both agents now share this context!
```

---

## 📊 Step 7: Test & Experiment (ongoing)

### Test Different Models
```python
# Try different models
models = [
    "anthropic/claude-haiku-4-5",     # Fast, cheap
    "anthropic/claude-sonnet-4-5",    # Balanced
    "anthropic/claude-opus-4-5"       # Best, expensive
]

for model in models:
    agent = client.agents.create(
        name=f"test_{model.split('/')[1]}",
        model=model,
        memory_blocks=[{"label": "persona", "value": "Test agent"}]
    )
    # Test performance vs cost
```

### Monitor Token Usage
```python
# Check usage
response = client.agents.messages.create(...)

# Monitor in dashboard
# app.letta.com → Agents → Your Agent → Usage
```

---

## 🎓 Step 8: Document Everything (ongoing)

### Keep Learning Journal
```markdown
# Learning Journal

## 2026-03-03
### What I Did
- Created first agent
- Tested memory blocks
- Added web search tool

### What I Learned
- Core memory is always loaded (expensive!)
- Archival needs tags for discovery
- Tools can be attached/removed dynamically

### Questions
- How to optimize token usage?
- How to build multi-agent system?
- How to use sleeptime agents?

### Next Steps
- Read about multi-agent patterns
- Try hierarchical teams
- Test conversations API
```

---

## ✅ Checklist: First Day

```
Setup:
- [ ] Got API key
- [ ] Installed SDK
- [ ] Tested connection

Basics:
- [ ] Read llms.txt
- [ ] Read quickstart guide
- [ ] Created first agent
- [ ] Sent first message

Memory:
- [ ] Updated memory block
- [ ] Used archival memory
- [ ] Tested memory search

Tools:
- [ ] Added web_search tool
- [ ] Tested tool usage

Documentation:
- [ ] Created memory structure
- [ ] Documented learnings
- [ ] Asked questions

Patterns:
- [ ] Tried conversations API
- [ ] Tested shared memory

Next:
- [ ] Plan next learning session
- [ ] Identify knowledge gaps
- [ ] Set learning goals
```

---

## 🎯 Common Pitfalls

### Don't Do This
```python
# ❌ Don't put large docs in core memory
memory_blocks=[{
    "label": "docs",
    "value": "ENTIRE API DOCUMENTATION..."  # Too large!
}]

# ❌ Don't forget tags in archival
client.agents.archival_memory.insert(
    content="Important fact",
    # Missing tags! Hard to find later
)

# ❌ Don't use expensive model for simple tasks
model="anthropic/claude-opus-4-5"  # For "Hello world"?!
```

### Do This Instead
```python
# ✅ Use notes for large docs
note("attach", "/references/api-docs")

# ✅ Always use tags
client.agents.archival_memory.insert(
    content="Important fact",
    tags=["category", "domain", "date"]
)

# ✅ Match model to task
model="anthropic/claude-haiku-4-5"  # For simple tasks
```

---

## 🚀 Next Steps

After completing these steps:

1. **Read** `05_RESOURCES.md` - discover more repos
2. **Study** `06_BEST_PRACTICES.md` - learn from experts
3. **Try** multi-agent patterns
4. **Build** something real!

---

## 💡 Pro Tips

1. **Learn by doing** - hands-on > reading
2. **Document everything** - build knowledge base
3. **Test often** - experiment with features
4. **Ask questions** - Discord community
5. **Iterate** - improve progressively

---

## 🆘 Getting Help

```
Documentation: docs.letta.com
Community: discord.gg/letta
Examples: github.com/letta-ai/*
Blog: letta.com/blog
```

---

*"Every master was once a beginner. Start now!"* 🚀
