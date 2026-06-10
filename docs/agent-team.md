# Agent team

This project uses a four-agent custom team to build Mona's Project Pulse dashboard. Each agent is defined under .github/agents/.

- Orchestrator — model: Claude Opus 4.7. Responsibility: coordinate Planner, Coder, and Designer; break plans into phases, assign file scopes, run tasks in parallel or sequence, and verify integration. Definition: .github/agents/orchestrator.agent.md

- Planner — model: Claude Opus 4.7. Responsibility: research the codebase, produce an ordered implementation plan with file assignments, dependencies, edge cases, and validation expectations. Definition: .github/agents/planner.agent.md

- Coder — model: GPT-5.5 (copilot). Responsibility: implement code, fix bugs, produce testable behavior, and provide runnable-app support (e.g., create .vscode/launch.json for Project Pulse). Definition: .github/agents/coder.agent.md

- Designer — model: Gemini 3.1 Pro (copilot). Responsibility: UI/UX, accessibility, information architecture, and visual styling to produce a polished, responsive dashboard. Definition: .github/agents/designer.agent.md

Work will be orchestrated from a GitHub Codespace using the GitHub Copilot CLI to run and coordinate these agents.