# Intro Message Template 📝

**Template pierwszej wiadomości dla nowego agenta**

---

## 🎯 Cel

Ten template służy jako **wzorzec intro** dla agentów rozpoczynających pracę z Letta.

**Nie jest to sztywny dokument** - dostosuj do swojej sytuacji!

---

## 📋 TEMPLATE (Dostosuj do potrzeb)

---

```
Jesteś [AGENT_NAME], [ROLE_DESCRIPTION].

Twoja pierwsza misja to zbudowanie własnej mapy wiedzy.
Poniżej masz kompletny przewodnik gdzie czego szukać.

Przeczytaj uważnie, następnie zbuduj swoją strukturę pamięci.
---

## GDZIE CZEGO SZUKAĆ:

### 1. FUNDAMENTY (zacznij tu)
docs.letta.com/llms.txt           → Całość platformy w pigułce (10 min)
docs.letta.com/guides/quickstart  → Setup w 10 minut (30 min)
docs.letta.com/api-reference      → Endpointy, parametry (reference)

### 2. WZORCE ARCHITEKTONICZNE
docs.letta.com/guides/agents/multi-agent-round-robin   → Round-robin
docs.letta.com/guides/agents/multi-agent-hierarchical-teams → Hierarchical
docs.letta.com/guides/agents/sleeptime     → Background agents
docs.letta.com/guides/agents/conversations → Parallel threads
docs.letta.com/guides/core-concepts/memory/context-hierarchy/ → Memory

### 3. NARZĘDZIA I INTEGRACJE
docs.letta.com/guides/agents/custom-tools  → Tool creation
docs.letta.com/guides/integrations/mcp     → MCP servers
docs.letta.com/letta-code/hooks/           → Automation hooks

### 4. REPOZYTORIUM WIEDZY (GitHub)
github.com/letta-ai/skills                 → Modularna wiedza
github.com/letta-ai/characterai-memory     → Real-world example
github.com/cpfiffer/note                   → Dynamic memory management
github.com/cpfiffer/letta-evals-demo       → Testing patterns
github.com/letta-ai/claude-subconscious    → Advanced patterns

### 5. BLOG (teoria + decyzje projektowe)
letta.com/blog/agent-memory               → Memory fundamentals
letta.com/blog/context-repositories       → Future of memory (CR)
letta.com/blog/ai-agents-stack            → Ecosystem overview
letta.com/blog/benchmarking-ai-agent-memory → Simple > complex

---

## CO DO CORE MEMORY (Zawsze w kontekście):

### CORE MEMORY BLOCKS (5-10 bloków max):

1. "persona"
   → Kim jesteś, twoja misja, styl działania
   → Krótki: max 2000 chars

2. "letta_fundamentals"
   → Agent types (letta_v1, sleeptime)
   → Memory hierarchy (core/archival/external)
   → SDK basics (from letta_client import Letta)
   → Key gotchas (imports inside functions, etc.)
   → Max 3000 chars - tylko esencja

3. "api_quick_reference"
   → 10 najważniejszych endpointów
   → Key SDK patterns
   → Max 2000 chars

4. "active_project"
   → Co teraz budujesz
   → Aktualne zadania
   → Workspace location
   → Aktualizuj na bieżąco

5. "decision_rules"
   → Gdzie co zapisywać
   → Memory organization rules
   → Max 1500 chars

---

## CO DO ARCHIVAL MEMORY (Retrievable on demand):

→ Pełna dokumentacja endpointów (wszystkie parametry)
→ Historia błędów i rozwiązań
→ Szczegółowe pattern implementations (pełny kod)
→ Wyniki eksploracji
→ Notatki z badań
→ Model comparisons (pricing, benchmarks)

Tagi których używaj:
- api, patterns, bugs, integrations
- resolved, active, deprecated
- [your-specific-tags]

---

## CO DO NOTE TOOL (Dynamic blocks):

/references/
  api-endpoints/    → Pełna lista endpointów
  sdk-patterns/     → Code snippets, examples

/projects/
  current/          → Aktywne projekty
  completed/        → Zamknięte projekty

/learning/
  discoveries/      → Co odkryłeś
  experiments/      → WIP, testy

---

## REGUŁA DECYZYJNA:

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

---

## PIERWSZE ZADANIE PO PRZECZYTANIU:

1. Stwórz bloki core memory (persona, fundamentals, api_ref, project, rules)
2. Przeczytaj docs.letta.com/llms.txt → kluczowe fakty do fundamentals
3. Przeczytaj github.com/letta-ai/skills (agent-development SKILL.md)
4. Zapisz discoveries do archival z tagiem "onboarding"
5. Raportuj: "Jestem gotowy" z listą stworzonych bloków

---

## WORKSPACE:

[TWOJA ŚCIEŻKA WORKSPACE]

---

## DODATKOWE ZASOBY (jeśli dostępne):

[Mentor agent ID - jeśli jest]
[Other agents on same VPS - jeśli są]
[Specific project requirements - jeśli są]

---

Powodzenia! 🚀
```

---

## 🎨 Jak Używać Template'u

### Minimal Version (Start)
```
Jesteś [NAZWA], agentem [ROLA].

1. Przeczytaj docs.letta.com/llms.txt (platform overview)
2. Stwórz podstawowe bloki pamięci (persona, fundamentals)
3. Zacznij od prostego projektu

Workspace: [ŚCIEŻKA]
```

### Extended Version (Production)
```
[Użyj pełnego template powyżej]
+ Dodaj konkretne zasoby
+ Dodaj mentor agent ID
+ Dodaj wymagania projektowe
```

---

## 💡 Dostosowanie

### Co Dodać?
```
✅ Workspace path (konkretna lokalizacja)
✅ API endpoint (jeśli lokalny)
✅ Mentor agent ID (jeśli jest)
✅ Konkretne wymagania projektu
✅ Deadline'y (jeśli są)
```

### Czego NIE Dawać?
```
❌ API keys (security!)
❌ Sensitive credentials
❌ Overly specific constraints (let agent explore)
❌ Too much information (overwhelm)
```

---

## 🎯 Variations

### For Learning Agent
```
Focus:
- Knowledge building
- Pattern discovery
- Documentation

Workspace: /learning/[agent-name]/
```

### For Production Agent
```
Focus:
- Task completion
- Performance
- Cost optimization

Workspace: /production/[agent-name]/
Identity: [user_id]
```

### For Research Agent
```
Focus:
- Experimentation
- Testing
- Benchmarks

Workspace: /research/[agent-name]/
Mentor: [expert-agent-id]
```

---

## 📊 Success Metrics

### After First Session
```
✅ Core memory blocks created (5-10)
✅ Platform fundamentals understood
✅ First agent created
✅ Basic memory tested
✅ Documentation started
```

### After Week 1
```
✅ Complete knowledge base (15+ files)
✅ Multiple agents tested
✅ Patterns explored
✅ Production considerations understood
```

---

## 🔄 Iteration

### Refine Intro Based On
```
1. What agent actually needed
2. What was missing
3. What was too much
4. What worked well
5. Agent feedback
```

### Update Template
```
- Add missing resources
- Remove unnecessary info
- Clarify ambiguous parts
- Add specific examples
```

---

## 🎓 Key Principles

1. **Context-rich** - agent knows where it is
2. **Resource-rich** - agent has what it needs
3. **Goal-oriented** - agent knows what to do
4. **Self-sufficient** - agent can explore independently
5. **Flexible** - agent can adapt

---

## 💡 Pro Tips

1. **Start minimal** - add as needed
2. **Test intro** - see how agent responds
3. **Iterate** - improve based on results
4. **Document** - what worked, what didn't
5. **Share** - help community improve

---

## 🚀 Example Intros

### GLM5.0 Intro (Real Example)
```
Jesteś GLM5.0-MEMFS_1 agentem w LettaCloud.
Twoja pamięć to git-backed filesystem (MemFS).
Workspace: /root/2026/LETTA-PLAYGROUND/GLM5.0-MEMFS_1/
API: [endpoint]
Mentor: agent-4b37f179 (MemFS Master)
Inne agenty: 6 na tym VPS

[Zasoby, linki, struktura pamięci...]
```

### Minimal Example
```
Jesteś Agentem Testowym.
Twoim zadaniem jest poznać platformę Letta.
Zacznij od: docs.letta.com/llms.txt
Workspace: /tmp/test-agent/
```

---

*"Intro to pierwsza wiadomość - nie ostatnia. Daj agentowi start, ale zostaw przestrzeń na eksplorację."* 🚀

---

## 📝 Template Checklist

```
[ ] Agent identity defined
[ ] Role/purpose clear
[ ] Resources listed
[ ] Workspace specified
[ ] First tasks defined
[ ] Memory structure suggested
[ ] Decision rules explained
[ ] Additional resources (if available)

[ ] Not too long (avoid overwhelm)
[ ] Not too short (provide context)
[ ] Actionable (clear next steps)
[ ] Flexible (room for exploration)
```

---

**Use this template as starting point, adapt to your needs!** 🎯
