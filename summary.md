# Summary

## requirements.txt

The project requires three Python dependencies:

| Package | Minimum Version |
|---|---|
| `anthropic` | >= 0.25.0 |
| `python-dotenv` | >= 1.0.0 |
| `pyyaml` | >= 6.0 |

---

## README.md Overview

### Core Philosophy

**"Agency comes from model training, not from external code orchestration."** The model is the intelligence (driver), the harness is the operational environment (vehicle). This repository teaches how to build the harness.

### What is an Agent?

- **An agent = Model (LLM) + Harness (Tools, Knowledge, Observation, Actions, Permissions)**
- Agency (the ability to perceive, reason, and act) is **learned through training**, not coded via procedural logic.
- The repository warns against "prompt-plumbing" tools (drag-and-drop workflows, no-code AI agent platforms, prompt-chain orchestration libraries), which it describes as "Rube Goldberg machines" 〞 brittle procedural pipelines with an LLM wedged in.

### Historical Context

The README cites milestones demonstrating trained agency:
- **2013** 〞 DeepMind DQN playing Atari
- **2019** 〞 OpenAI Five defeating Dota 2 world champions
- **2019** 〞 DeepMind AlphaStar reaching Grandmaster in StarCraft II
- **2019** 〞 Tencent Jueyu defeating Honor of Kings professionals
- **2024-2025** 〞 LLM agents (Claude, GPT, Gemini) reshaping software engineering

### Core Pattern (Agent Loop)

```python
def agent_loop(messages):
    while True:
        response = client.messages.create(...)
        messages.append(response)
        if response.stop_reason != "tool_use":
            return
        for tool_use in response.content:
            output = execute_tool(tool_use)
            messages.append(tool_result)
```

### What Harness Engineers Do

1. **Implement tools** 〞 File I/O, shell, API calls, browser control
2. **Curate knowledge** 〞 Product docs, style guides, domain references
3. **Manage context** 〞 Subagent isolation, compaction, task persistence
4. **Control permissions** 〞 Sandboxing, approval workflows, trust boundaries
5. **Collect trajectory data** 〞 Real deployment sequences for future fine-tuning

### Project Structure

Two tutorial tracks exist:
- **Current (s01每s20)** 〞 Root-level folders with full README, translations, `code.py`
- **Legacy (docs/, agents/)** 〞 Older 12-lesson track kept temporarily

Key directories:
- `s01_agent_loop/` .. `s20_comprehensive/` 〞 20 progressive lessons
- `agents/` 〞 Legacy runnable copies
- `skills/` 〞 Skill files for lesson s07
- `docs/` 〞 Legacy documentation
- `web/` 〞 Web app rendering legacy docs
- `tests/` 〞 Test files

### The 20 Lessons (6 Stages)

| Stage | Lessons | Focus |
|---|---|---|
| **1. Core Capabilities** | s01每s04 | Agent loop, tool use, permissions, hooks |
| **2. Complex Work** | s05, s06, s08 | Planning (TodoWrite), subagents, context compaction |
| **3. Memory & Recovery** | s09每s11 | Memory, system prompts, error recovery |
| **4. Long-Running Tasks** | s12每s14 | Task system, background tasks, cron scheduler |
| **5. Multi-Agent Coordination** | s15每s18 | Teams, protocols, autonomous agents, worktree isolation |
| **6. Extension & Assembly** | s07, s19, s20 | Skill loading, MCP plugin, comprehensive agent |

### Quick Start

```sh
git clone https://github.com/shareAI-lab/learn-claude-code
cd learn-claude-code
pip install -r requirements.txt
cp .env.example .env   # configure ANTHROPIC_API_KEY
python s01_agent_loop/code.py
```

### What's Next After the 20 Lessons

- **[Kode Agent CLI](https://github.com/shareAI-lab/Kode-CLI)** 〞 Open-source coding agent CLI
- **[Kode Agent SDK](https://github.com/shareAI-lab/kode-agent-sdk)** 〞 Embed agent capabilities in applications
- **[claw0](https://github.com/shareAI-lab/claw0)** 〞 Sister repository on always-on assistants (heartbeat, cron, IM, memory, soul)

### License

**MIT**
