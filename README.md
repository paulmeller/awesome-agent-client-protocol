# Awesome Agent Client Protocol [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> An open, editor-agnostic JSON-RPC protocol for connecting AI coding agents to any editor or IDE — created by Zed, co-developed with JetBrains. Build your agent once and any ACP-compatible client can drive it.

## Contents

- [Official Resources](#official-resources)
- [SDKs](#sdks)
- [Editor and Client Implementations](#editor-and-client-implementations)
- [Agent Implementations](#agent-implementations)
- [Documentation](#documentation)
- [Articles and Guides](#articles-and-guides)
- [Related Protocols](#related-protocols)

## Official Resources

- [Agent Client Protocol](https://agentclientprotocol.com) - Official documentation and specification site for the protocol.
- [Agent Client Protocol Repository](https://github.com/agentclientprotocol/agent-client-protocol) - Canonical spec and schema repository, maintained jointly by Zed and JetBrains.
- [Zed's Agent Client Protocol Page](https://zed.dev/acp) - Zed's official overview of ACP and how it works inside the editor.
- [The ACP Registry](https://zed.dev/blog/acp-registry) - Announcement of the public registry that lets agent developers register once and appear across every compatible editor.
- [JetBrains x Zed: Open Interoperability for AI Coding Agents](https://blog.jetbrains.com/ai/2025/10/jetbrains-zed-open-interoperability-for-ai-coding-agents-in-your-ide/) - JetBrains' announcement of native ACP support across its IDEs.
- [ACP v2 Draft Announcement](https://agentclientprotocol.com/announcements/acp-v2-draft) - Announcement of the first draft of protocol version 2, published for review and testing alongside the stable v1.
- [Rust and TypeScript SDKs Reach 1.0](https://agentclientprotocol.com/announcements/sdk-1-0-releases) - Announcement of `agent-client-protocol` v1.0.0 and `@agentclientprotocol/sdk` v1.0.0, published June 2026.
- [ACP Registry Repository](https://github.com/agentclientprotocol/registry) - Apache-2.0 registry of agents that support user authentication, checked in CI for valid `authMethods`, with a public JSON index and hourly automatic version updates.
- [Python SDK 1.0.0](https://github.com/agentclientprotocol/python-sdk/releases/tag/1.0.0) - First stable 1.x release of the Python SDK, with v1 bindings tracking `schema-v1.23.0` and experimental v2 bindings, published November 2026.
- [Client-Provided System Prompts Are Stabilized](https://agentclientprotocol.com/announcements/client-system-prompt-stabilized) - Announcement that the `systemPrompt` field on session setup and the `systemPrompt` session capability are stabilized in ACP v1 and v2, published November 6, 2026.

## SDKs

- [Rust SDK](https://github.com/agentclientprotocol/rust-sdk) - Official crates for building ACP clients, agents, and proxies.
- [Python SDK](https://github.com/agentclientprotocol/python-sdk) - Official Python implementation with Pydantic models and async transports.
- [TypeScript SDK](https://github.com/agentclientprotocol/typescript-sdk) - Official TypeScript implementation, published to npm as @agentclientprotocol/sdk.
- [Kotlin SDK](https://agentclientprotocol.com/libraries/kotlin) - Official JVM-targeted Kotlin implementation.
- [Java SDK](https://github.com/agentclientprotocol/java-sdk) - Official pure-Java implementation for building clients and agents.
- [Community Libraries](https://agentclientprotocol.com/libraries/community) - Official index of community-maintained ACP libraries for Go, Swift, Crystal, .NET, Dart, and other languages.

## Editor and Client Implementations

- [Zed](https://zed.dev/acp) - High-performance, multiplayer editor with native ACP support built in.
- [JetBrains IDEs](https://blog.jetbrains.com/ai/2025/10/jetbrains-zed-open-interoperability-for-ai-coding-agents-in-your-ide/) - Native ACP support across IntelliJ-based IDEs.
- [agentic.nvim](https://github.com/carlos-algms/agentic.nvim) - Neovim chat interface implementing ACP, works with any ACP-compatible agent.
- [CodeCompanion.nvim](https://codecompanion.olimorris.dev/agent-client-protocol) - Neovim plugin with ACP support, including session management and permission handling.
- [agent-shell](https://github.com/xenodium/agent-shell) - Native Emacs buffer for interacting with ACP-powered agents.
- [ACP Clients Directory](https://agentclientprotocol.com/get-started/clients) - Official listing of every known editor and IDE implementing ACP, including community extensions for VS Code, Obsidian, Qt Creator, and Unity.
- [ACP for Sublime Text](https://packages.sublimetext.io/packages/ACP) - Sublime Text 4 plugin for running ACP agents such as Claude Code, OpenCode, and Copilot, with persistent sessions and model, mode, and thought-level switching.
- [Xcode](https://developer.apple.com/documentation/xcode/setting-up-coding-intelligence) - Apple's coding intelligence setup guide, where any agent that supports ACP can be added to Xcode with Add an Agent in Intelligence settings.
- [devin-tui](https://github.com/fenner888/devin-tui) - Unofficial full-screen terminal UI for Devin driven by `devin acp`, with inline diffs, plans, per-session spend, and a flag to spawn any other ACP agent.
- [Eclipse ACP Connector](https://marketplace.eclipse.org/content/eclipse-acp-connector) - Beta Apache-2.0 plugin for Eclipse IDE that opens a project chat and runs a configurable local ACP agent over stdio, with session history, permission dialogs, and mode, model, and reasoning-level selectors.
- [acp-tui](https://github.com/FasterPHP/acp-tui) - Preview full-screen terminal client for ACP, built for the integrated terminals of PhpStorm, IntelliJ IDEA, and Zed, with Auggie out of the box and Claude Code, OpenCode, or Codex by configuration.
- [Volt](https://github.com/LeulAria/volt) - Open-source editor on the VS Code core that runs ACP agents such as Claude Code, Codex and OpenCode, with pending hunk-level edits and a Git checkpoint every turn.
- [Eleven](https://github.com/Zfinix/eleven) - Agent-first reverse-engineering app for macOS where any ACP agent can read code, rename functions, leave notes, and suggest patches on Ghidra analysis while you watch and approve.
- [littleguys](https://github.com/herval/littleguys) - Free, open-source Mac app that puts Claude Code, Codex, OpenClaw, Hermes, and any ACP agent in WhatsApp-style chats, with a menu-bar status sprite and one-click agents from the ACP registry.
- [acpx](https://github.com/openclaw/acpx) - Headless CLI client for stateful ACP sessions across agents such as Codex, Claude Code, Pi, and OpenClaw, with machine-readable output for automation.
- [AgentConnect](https://github.com/agentconnect-md/agentconnect) - Open-source (Apache-2.0) platform that brings Claude Code, Codex, Pi, or any ACP-compatible agent into team workflows across Slack, Telegram, Discord, Lark, Google Chat, GitHub, GitLab, Gitea, and Linear.
- [Octop](https://github.com/TencentCloud/Octop) - Tencent Cloud's self-hosted, multi-user AI assistant (MIT) that serves its agents over ACP with `octop acp` and delegates coding tasks to external ACP agents such as OpenCode and Claude Code.
- [acpantenna](https://github.com/fboldo/acpantenna) - CLI channel that hands a running ACP agent a link and QR code, so the session carries on in a browser or on a phone over an end-to-end encrypted relay, with permission prompts on the device you moved to.
- [ACP Bridge](https://github.com/aws-samples/sample-acp-bridge) - AWS sample (MIT-0) that exposes local CLI agents such as Kiro CLI, Claude Code, and Codex through ACP over HTTP, with SSE streaming, async jobs, and Discord push notifications.
- [ACP VS Code Extension and Web UI](https://github.com/strato-space/acp-plugin) - VS Code extension with an optional browser UI for running ACP agents, using Zed-compatible `agent_servers` configuration.
- [ACP Client for VS Code](https://github.com/formulahendry/vscode-acp) - VS Code extension that connects to any ACP agent, with per-agent session lists, session config options, slash commands, permission policies, and protocol traffic logging.
- [VSCode ACP](https://github.com/omercnet/vscode-acp) - VS Code extension for chatting with Claude Code, OpenCode, and other ACP agents in the editor, published on the VS Code Marketplace and Open VSX.
- [ACP Patchbay](https://github.com/solutionsunity/acp-patchbay) - Unified VS Code client for any agent in the ACP registry, with one permission model, a declared-versus-used capability matrix, parallel sessions, and editor context over a local MCP server.
- [Pulsar ACP Agent](https://github.com/hovancik/pulsar-acp-agent) - Pulsar package that runs ACP coding agents from a dock panel, with file, selection, and image attachments and inline permission prompts, diffs, and plans.
- [acp.nvim](https://github.com/brianhuster/acp.nvim) - Early-development ACP client for Neovim 0.12 and later that works with any ACP-compatible agent.

## Agent Implementations

- [Claude Agent ACP Adapter](https://github.com/zed-industries/claude-agent-acp) - Lets the Claude Agent SDK be driven from any ACP client.
- [GitHub Copilot CLI ACP Support](https://docs.github.com/en/copilot/reference/acp-server) - Documentation for running Copilot CLI as an ACP agent.
- [Cursor CLI ACP Support](https://cursor.com/docs/cli/acp) - Documentation for Cursor CLI's ACP integration.
- [Goose](https://goose-docs.ai/docs/guides/cli-providers/) - Open-source AI agent that ships native claude-acp and codex-acp providers.
- [ACP Agents Directory](https://agentclientprotocol.com/get-started/agents) - Official listing of agents implementing ACP, including Gemini CLI, Cline, and OpenHands.
- [Devin CLI ACP Support](https://docs.devin.ai/cli/acp/zed) - Cognition guide to running Devin CLI as an ACP agent in Zed's Agent Panel, installed from the ACP registry, with companion pages for JetBrains IDEs and Xcode.
- [Poolside ACP Support](https://docs.poolside.ai/tools/zed) - Guide to running Poolside in Zed through ACP, installed from the ACP Registry, set up with `pool acp setup --editor zed`, or configured manually as a custom agent.
- [acplause](https://github.com/anesthetised/acplause) - Experimental ACP v2 agent that talks to editors over stdio and works through any OpenAI-compatible Chat Completions API, OpenRouter first, with streaming reasoning, tool calls, and usage and cost reporting.
- [Cursor Agent ACP Adapter](https://github.com/blowmage/cursor-agent-acp-npm) - Unofficial MIT TypeScript adapter that bridges Cursor CLI to ACP editors such as Zed over stdio, built on `@agentclientprotocol/sdk`.
- [Kiro CLI ACP Support](https://kiro.dev/docs/cli/acp/) - Documentation for running `kiro-cli acp` as an ACP agent in JetBrains IDEs, Zed, and other compatible editors, including its supported methods and `_kiro.dev/` extensions.
- [OpenCode ACP Support](https://opencode.ai/docs/acp/) - Documentation for running `opencode acp` as an ACP subprocess in Zed, JetBrains IDEs, Avante.nvim, and CodeCompanion.nvim.
- [Codex ACP Adapter](https://github.com/agentclientprotocol/codex-acp) - Official ACP server that exposes Codex CLI to any ACP client, published as `@agentclientprotocol/codex-acp`.
- [Command Code ACP Support](https://commandcode.ai/docs/acp) - Documentation for running `cmd acp` as an ACP server in Zed and other ACP-compatible editors, with the same tools, skills, permissions, and sessions.
- [Octomind](https://github.com/muvon/octomind/blob/master/doc/integration/02-acp-protocol.md) - Open-source Rust coding agent runtime for any model provider, MCP-native, that runs as an ACP agent over stdio via `octomind acp`.
- [Grok Build ACP Agent Mode](https://github.com/xai-org/grok-build/blob/main/crates/codegen/xai-grok-pager/docs/user-guide/15-agent-mode.md) - Runs xAI's Grok Build as a long-lived ACP server with `grok agent stdio` or a WebSocket server, for IDEs, SDKs, eval harnesses, and custom apps.
- [DeepSeek Harness ACP Server](https://github.com/deepseek-ai/deepseek-harness/blob/master/packages/acp/acp/README.md) - Automation-only ACP v1 server (`@deepseek-ai/dsh-acp`) that lets scripts and test runners drive persistent DeepSeek Harness sessions over stdio, started with `dsh --profile acp`.
- [acp-bridge](https://github.com/BlakeHung/acp-bridge) - Rust single-binary adapter that bridges any OpenAI-compatible API to ACP for offline, air-gapped coding agents, supporting ACP v1 and v2. MIT.
- [CodeWork](https://codework.sh/posts/codework-supports-acp/) - Open-source coding agent CLI whose `codework acp` subcommand runs an ACP v1 server on stdio, sharing session history with the terminal and exposing model and thinking-effort pickers.
- [acp-llm-adapter](https://github.com/euri10/acp-llm-adapter) - Rust ACP coding-agent harness for DeepSeek, GLM, and Groq, with permission-gated tools and persistent sessions.
- [Antigravity CLI ACP Support](https://antigravity.google/docs/cli/acp/) - Google Antigravity docs for `agy acp`, which runs Antigravity CLI as an ACP server over stdio for Zed, JetBrains IDEs, Android Studio, Xcode, and other ACP clients.
- [Kimi Code CLI ACP Support](https://www.kimi.com/code/docs/en/kimi-code-cli/guides/ides) - Kimi Code docs guide to running Kimi Code CLI as an ACP agent with `kimi acp` in Zed and JetBrains IDEs.

## Documentation

- [Rust SDK Book](https://agentclientprotocol.github.io/rust-sdk/) - Design and architecture documentation for the Rust SDK.
- [Python SDK Docs](https://agentclientprotocol.github.io/python-sdk/) - API reference and usage guide for the Python SDK.
- [TypeScript SDK Docs](https://agentclientprotocol.github.io/typescript-sdk/) - API reference and usage guide for the TypeScript SDK.
- [Rust SDK v2 Quickstart](https://agentclientprotocol.github.io/rust-sdk/protocol-v2-quickstart.html) - Runnable ACP v2 agent and client examples behind the `unstable_protocol_v2` feature flag.
- [ACP v2 Migration Guide](https://agentclientprotocol.com/protocol/v2/migration) - Breaking changes, new features, and agent, client, and SDK checklists for moving from v1 to the draft v2 protocol while keeping v1 support side by side.
- [Zed External Agents](https://zed.dev/docs/ai/external-agents) - Zed's guide to installing ACP agents from the registry, adding custom agents, importing their threads, forwarding MCP servers, and reading ACP logs with `dev: open acp logs`.
- [JetBrains AI Assistant ACP Guide](https://www.jetbrains.com/help/ai-assistant/acp.html) - JetBrains documentation for adding ACP agents to AI Chat from the curated registry or as custom agents, with no JetBrains AI subscription required.
- [TypeScript SDK Stable-by-Default Migration Guide](https://github.com/agentclientprotocol/typescript-sdk/blob/main/MIGRATION_STABLE_UNSTABLE.md) - Upgrade guide for the SDK entrypoint split, where the default import uses stable ACP v1 and unstable or v2 draft features need explicit imports.
- [RFD Updates](https://agentclientprotocol.com/rfds/updates) - Lifecycle log of ACP Requests for Dialog, such as the client-set session titles and session status RFDs that moved to Draft in October 2026.
- [Agent Extensions via ACP Proxies](https://agentclientprotocol.com/rfds/proxy-chains) - RFD for proxies that sit between a client and an agent, with the `proxy/initialize` and `proxy/successor` messages and a reference conductor implemented in the Rust SDK.

## Articles and Guides

- [The Agent Client Protocol Overview](https://www.philschmid.de/acp-overview) - Philipp Schmid's technical overview of ACP's architecture and JSON-RPC design.
- [Introducing Emacs agent-shell](https://xenodium.com/introducing-agent-shell) - Walkthrough of building an ACP-powered agent shell for Emacs.
- [Which Coding Agents Support ACP?](https://agentrq.com/blog/which-coding-agents-support-acp-agent-client-protocol) - AgentRQ table of 33 agents showing native or adapter ACP support, the command that starts each one, and its registry id, as of October 2026.
- [JetBrains Air in IDEs EAP](https://blog.jetbrains.com/ai/2026/10/air-in-ides-eap/) - JetBrains announcement of Air in its IDEs, which runs Codex, Gemini, GitHub Copilot, Claude Agent, and Junie out of the box and connects other agents through ACP.
- [Add a Coding Agent to Zed and JetBrains IDEs With ACP](https://dev.to/abishaiama/add-a-coding-agent-to-zed-and-jetbrains-ides-with-the-agent-client-protocol-4o08) - Atlarix walkthrough of adding its `atlarix acp` agent to Zed and JetBrains IDEs, with its modes, models, and permission prompts in the editor's own UI.
- [A new agent, and nothing else moved](https://openspec-ui.dev/articles/a-new-agent-and-nothing-else-moved/) - OpenSpec Workbench post on adding DeepSeek as an ACP agent via `dsh --profile acp` with one adapter shared by its VS Code extension and web app.
- [ACP from Scratch](https://k33g.org/p/20261031-acp-from-scratch) - k33g walkthrough of ACP v1 basics, covering the stdio subprocess model, JSON-RPC 2.0 messages, and requests flowing in both directions between editor and agent.
- [ACP Agent Registry Is Live](https://blog.jetbrains.com/ai/2026/01/acp-agent-registry/) - JetBrains announcement of the official ACP Agent Registry, launched with Zed, for browsing and installing coding agents from JetBrains IDEs 2025.3 and later.
- [Use Your GitHub Copilot Plan in JetBrains Air](https://blog.jetbrains.com/air/2026/11/github-copilot-in-air/) - JetBrains walkthrough of running the official GitHub Copilot CLI in Air over ACP, locally in the IDE or as Air Teams cloud tasks billed to the Copilot plan, published November 2026.
- [Your IDE Stopped Choosing Your Coding Agent](https://stepto.net/blog/agent-client-protocol-bring-your-own-agent-ide-2026) - StepTo piece for engineering leaders on what ACP changes, comparing it with MCP and A2A and proposing an approved-agent policy and a 90-day rollout plan.
- [Android Studio Rabbit 2: Run Any AI Agent in Your IDE](https://byteiota.com/android-studio-rabbit-2-bring-your-own-agent/) - Walkthrough from byteiota of Android Studio's ACP-based Bring Your Own Agent feature, covering what connected agents can access, setup, and early stability caveats.
- [Agent Client Protocol (ACP) on tomrochette.com](https://tomrochette.com/agents/protocols/acp/) - Running assessment of ACP with SDK versions, agent-list counts, strengths, criticisms, and a dated change log.
- [GitHub Copilot Reaches JetBrains Air Through ACP](https://pondero.ai/news/2026-11-05-copilot-jetbrains-air/) - Pondero analysis of GitHub adding Copilot to the JetBrains Air agent picker over ACP instead of a dedicated connector.
- [Your Editor Can Now Use agy as Its Agent over ACP](https://www.vibecoding.cz/en/antigravity-weekly-2026-w45/) - Vibecoding.cz weekly on Antigravity CLI 1.5.0 to 1.5.3, covering `agy acp` session modes, `session/resume`, terminal sign-in with `agy acp --login`, and per-session model selection.
- [Nanocoder v1.32.0: ACP Matures](https://nanocollective.org/blog/nanocoder-v1320-acp-matures-a-ci-gate-browser-and-voice-134) - Nano Collective release post on Nanocoder's ACP agent gaining editor-supplied MCP servers per session, `_`-prefixed extension methods, and per-session provider and model.
- [Mini Me v1.0.6: Custom ACP Extensions](https://mini-me.org/p/20261111-mm-v1-0-6) - k33g release post on letting the ACP client lend its own functions to the Mini Me agent as tools, alongside a native Kronk provider.
- [Lessons from Putting 14 Coding-Agent CLIs Behind One Interface](https://dev.to/tesseract_app/lessons-from-putting-14-coding-agent-clis-behind-one-interface-gch) - Tesseract write-up on a desktop app where twelve of fourteen agent CLIs share one ACP backend, and where it hosts its own MCP tools to cover what ACP lacks.

## Related Protocols

- [Model Context Protocol](https://modelcontextprotocol.io) - Anthropic's open standard for connecting agents to external tools and data sources, frequently paired with ACP-based clients.
- [Language Server Protocol](https://microsoft.github.io/language-server-protocol/) - The protocol ACP is explicitly modeled after, decoupling language intelligence from editors the way ACP decouples agents from editors.

## Automated Updates

The weekly GitHub Action is removed. New items still arrive as a pull request, and nothing merges on its own.

## Contributing

Contributions welcome! Read the [contribution guidelines](CONTRIBUTING.md) first.
