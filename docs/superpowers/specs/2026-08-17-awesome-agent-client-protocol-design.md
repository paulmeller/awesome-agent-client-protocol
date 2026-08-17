# Design: awesome-agent-client-protocol

Date: 2026-08-17

## Purpose

Create a new, independent GitHub repository, `paulmeller/awesome-agent-client-protocol`, as a peer to the existing `paulmeller/awesome-managed-agents` repo. It curates resources for the Agent Client Protocol (ACP) — the open, editor-agnostic JSON-RPC standard originated by Zed Industries (co-developed with JetBrains) for connecting AI coding agents to any editor or IDE, analogous to how the Language Server Protocol decoupled language intelligence from editors.

A separate, unrelated list already exists at `github.com/nMaroulis/awesome-agent-client-protocol`. The user chose to build an independent list anyway rather than contribute there — same relationship as any other pair of unaffiliated awesome-lists on the same topic. No action is needed regarding that repo.

## Structure

Mirror `awesome-managed-agents` file-for-file, adapting only the content:

```
awesome-agent-client-protocol/
├── .github/workflows/update-list.yml
├── .gitignore
├── CONTRIBUTING.md
├── LICENSE
├── README.md
├── scripts/
│   ├── setup_skill.py
│   └── update_list.py
└── skills/
    └── awesome-list-curator/
        └── SKILL.md
```

- `LICENSE`: identical CC0 1.0 Universal text as the peer repo.
- `.gitignore`: identical (`__pycache__/`, `.skill-id`) — no `.skill-id` file is committed; it's generated locally by `setup_skill.py` and stays gitignored, exactly as in the peer repo.
- `CONTRIBUTING.md`: same guidelines/quality-standards structure as the peer repo, wording adjusted from "Claude Managed Agents" to "Agent Client Protocol" / "ACP".

## README.md

### Header

```
# Awesome Agent Client Protocol [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> An open, editor-agnostic JSON-RPC protocol for connecting AI coding agents to any editor or IDE — created by Zed, co-developed with JetBrains. Build your agent once and any ACP-compatible client can drive it.
```

### Contents (sections, in order)

1. Official Resources
2. SDKs
3. Editor and Client Implementations
4. Agent Implementations
5. Documentation
6. Articles and Guides
7. Related Protocols

No "Specification" section (its only real content — the schema repo — already lives under Official Resources; a separate section would be a one-entry duplicate). No "Community Projects", "Videos and Talks", "Press", or "Related Products" sections — no genuinely distinct, verified content exists for them yet, and the curator quality bar (below) says not to pad sections. These can appear later if the automated curator or a contributor finds real material — `CONTRIBUTING.md` says new categories are welcome.

### Seed entries

Every URL below was fetched and verified during design (not guessed). Format follows the existing repo's convention exactly: `- [Name](URL) - Description.` (capital start, period end, description doesn't repeat the link text).

**Official Resources**
- `[Agent Client Protocol](https://agentclientprotocol.com) - Official documentation and specification site for the protocol.`
- `[Agent Client Protocol Repository](https://github.com/agentclientprotocol/agent-client-protocol) - Canonical spec and schema repository, maintained jointly by Zed and JetBrains.`
- `[Zed's Agent Client Protocol Page](https://zed.dev/acp) - Zed's official overview of ACP and how it works inside the editor.`
- `[The ACP Registry](https://zed.dev/blog/acp-registry) - Announcement of the public registry that lets agent developers register once and appear across every compatible editor.`
- `[JetBrains x Zed: Open Interoperability for AI Coding Agents](https://blog.jetbrains.com/ai/2025/10/jetbrains-zed-open-interoperability-for-ai-coding-agents-in-your-ide/) - JetBrains' announcement of native ACP support across its IDEs.`

**SDKs**
- `[Rust SDK](https://github.com/agentclientprotocol/rust-sdk) - Official crates for building ACP clients, agents, and proxies.`
- `[Python SDK](https://github.com/agentclientprotocol/python-sdk) - Official Python implementation with Pydantic models and async transports.`
- `[TypeScript SDK](https://github.com/agentclientprotocol/typescript-sdk) - Official TypeScript implementation, published to npm as @agentclientprotocol/sdk.`
- `[Kotlin SDK](https://agentclientprotocol.com/libraries/kotlin) - Official JVM-targeted Kotlin implementation.`
- `[Java SDK](https://github.com/agentclientprotocol/java-sdk) - Official pure-Java implementation for building clients and agents.`

**Editor and Client Implementations**
- `[Zed](https://zed.dev/acp) - High-performance, multiplayer editor with native ACP support built in.`
- `[JetBrains IDEs](https://blog.jetbrains.com/ai/2025/10/jetbrains-zed-open-interoperability-for-ai-coding-agents-in-your-ide/) - Native ACP support across IntelliJ-based IDEs.`
- `[agentic.nvim](https://github.com/carlos-algms/agentic.nvim) - Neovim chat interface implementing ACP, works with any ACP-compatible agent.`
- `[CodeCompanion.nvim](https://codecompanion.olimorris.dev/agent-client-protocol) - Neovim plugin with ACP support, including session management and permission handling.`
- `[agent-shell](https://github.com/xenodium/agent-shell) - Native Emacs buffer for interacting with ACP-powered agents.`
- `[ACP Clients Directory](https://agentclientprotocol.com/get-started/clients) - Official listing of every known editor and IDE implementing ACP, including community extensions for VS Code, Obsidian, Qt Creator, and Unity.`

**Agent Implementations**
- `[Claude Agent ACP Adapter](https://github.com/zed-industries/claude-agent-acp) - Lets the Claude Agent SDK be driven from any ACP client.`
- `[GitHub Copilot CLI ACP Support](https://docs.github.com/en/copilot/reference/acp-server) - Documentation for running Copilot CLI as an ACP agent.`
- `[Cursor CLI ACP Support](https://cursor.com/docs/cli/acp) - Documentation for Cursor CLI's ACP integration.`
- `[Goose](https://goose-docs.ai/docs/guides/cli-providers/) - Open-source AI agent that ships native claude-acp and codex-acp providers.`
- `[ACP Agents Directory](https://agentclientprotocol.com/get-started/agents) - Official listing of agents implementing ACP, including Gemini CLI, Cline, and OpenHands.`

**Documentation**
- `[Get Started: Clients](https://agentclientprotocol.com/get-started/clients) - Guide for editor authors building an ACP client.`
- `[Get Started: Agents](https://agentclientprotocol.com/get-started/agents) - Guide for agent authors implementing the ACP agent side.`
- `[Rust SDK Book](https://agentclientprotocol.github.io/rust-sdk/) - Design and architecture documentation for the Rust SDK.`
- `[Python SDK Docs](https://agentclientprotocol.github.io/python-sdk/) - API reference and usage guide for the Python SDK.`
- `[TypeScript SDK Docs](https://agentclientprotocol.github.io/typescript-sdk/) - API reference and usage guide for the TypeScript SDK.`

**Articles and Guides**
- `[The Agent Client Protocol Overview](https://www.philschmid.de/acp-overview) - Philipp Schmid's technical overview of ACP's architecture and JSON-RPC design.`
- `[Introducing Emacs agent-shell](https://xenodium.com/introducing-agent-shell) - Walkthrough of building an ACP-powered agent shell for Emacs.`

**Related Protocols**
- `[Model Context Protocol](https://modelcontextprotocol.io) - Anthropic's open standard for connecting agents to external tools and data sources, frequently paired with ACP-based clients.`
- `[Language Server Protocol](https://microsoft.github.io/language-server-protocol/) - The protocol ACP is explicitly modeled after, decoupling language intelligence from editors the way ACP decouples agents from editors.`

Note: `agentic.nvim` and `CodeCompanion.nvim` each appear once, under Editor and Client Implementations only (not duplicated into a separate "Community Projects" section).

## CONTRIBUTING.md

Same structure and rules as the peer repo, with wording changed from "Claude Managed Agents" to "Agent Client Protocol" throughout. Same quality standards: directly related to ACP, actively maintained, clear purpose, not a duplicate.

## skills/awesome-list-curator/SKILL.md

Same shape as the peer repo's curator skill, rewritten for ACP:

- `name: awesome-list-curator`, `description`: rewritten to reference ACP instead of Managed Agents.
- **Search Strategy**: same five categories (blog posts/tutorials, GitHub repos, press/news, videos/talks, integrations), queries rewritten, e.g.:
  - `"Agent Client Protocol" tutorial`, `"Agent Client Protocol" guide`, `ACP editor integration site:github.com`, `"agent-client-protocol" site:github.com`, `"Agent Client Protocol" news`, `"Agent Client Protocol" site:youtube.com`, `ACP client OR agent integration`.
- **Assessment Criteria**: identical required checks (exists via `web_fetch`, relevant, not a duplicate, not spam) and identical quality signals / A–D scoring rubric. Only A/B added.
- **Output Format**: identical JSON assessment + full README write-out to `/mnt/session/outputs/`, same as peer repo.
- **Awesome List Formatting Rules**: identical (items added at bottom of section, never remove existing items, no License section, "Contents" heading, etc.), plus the repo's actual current section list so the curator knows what exists.

## .github/workflows/update-list.yml

Identical mechanics to the peer repo: Monday 9am UTC cron + `workflow_dispatch`, checkout, Python 3.12, `pip install anthropic`, run `scripts/update_list.py` with `ANTHROPIC_API_KEY` / `CURATOR_SKILL_ID` secrets, diff-check README, open a PR on change. Only text that changes: PR branch prefix, commit message, and PR body description reference "Agent Client Protocol" instead of "Managed Agents".

## scripts/setup_skill.py and scripts/update_list.py

Identical logic to the peer repo. String changes only:
- `setup_skill.py`: `display_title="Awesome List Curator"` → `display_title="ACP Awesome List Curator"` (avoids confusion if both skills ever appear in the same Anthropic account).
- `update_list.py`: system prompt and user-message text reference "Agent Client Protocol" / "ACP" instead of "Claude Managed Agents" / "awesome-managed-agents"; PR title/session title text updated to match.

Out of scope for this build: actually running `setup_skill.py` (requires the user's `ANTHROPIC_API_KEY` and a deliberate decision to create a live skill) and adding the `ANTHROPIC_API_KEY` / `CURATOR_SKILL_ID` repo secrets. The workflow will be committed ready-to-run; enabling it is a follow-up the user does deliberately, same as presumably happened for the peer repo.

## Repo creation

1. `git init` locally (done), write all files above, commit.
2. `gh repo create paulmeller/awesome-agent-client-protocol --public --source=. --remote=origin` (or equivalent) to create the GitHub repo and wire the remote.
3. Push `main`.

## Testing / Verification

- No code logic changes from the peer repo (scripts are copied with string substitutions only), so no new automated tests are needed beyond a manual read-through diff against the peer repo's `scripts/*.py` to confirm only strings changed, not behavior.
- Verify `README.md` renders correctly (valid Markdown, all TOC anchors match actual headings) before committing.
- Verify every URL in the seed content resolves (already done during design research; re-check is optional but not required since URLs don't change between design and implementation on this short timescale).
