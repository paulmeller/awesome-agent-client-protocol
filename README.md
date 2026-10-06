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

## SDKs

- [Rust SDK](https://github.com/agentclientprotocol/rust-sdk) - Official crates for building ACP clients, agents, and proxies.
- [Python SDK](https://github.com/agentclientprotocol/python-sdk) - Official Python implementation with Pydantic models and async transports.
- [TypeScript SDK](https://github.com/agentclientprotocol/typescript-sdk) - Official TypeScript implementation, published to npm as @agentclientprotocol/sdk.
- [Kotlin SDK](https://agentclientprotocol.com/libraries/kotlin) - Official JVM-targeted Kotlin implementation.
- [Java SDK](https://github.com/agentclientprotocol/java-sdk) - Official pure-Java implementation for building clients and agents.

## Editor and Client Implementations

- [Zed](https://zed.dev/acp) - High-performance, multiplayer editor with native ACP support built in.
- [JetBrains IDEs](https://blog.jetbrains.com/ai/2025/10/jetbrains-zed-open-interoperability-for-ai-coding-agents-in-your-ide/) - Native ACP support across IntelliJ-based IDEs.
- [agentic.nvim](https://github.com/carlos-algms/agentic.nvim) - Neovim chat interface implementing ACP, works with any ACP-compatible agent.
- [CodeCompanion.nvim](https://codecompanion.olimorris.dev/agent-client-protocol) - Neovim plugin with ACP support, including session management and permission handling.
- [agent-shell](https://github.com/xenodium/agent-shell) - Native Emacs buffer for interacting with ACP-powered agents.
- [ACP Clients Directory](https://agentclientprotocol.com/get-started/clients) - Official listing of every known editor and IDE implementing ACP, including community extensions for VS Code, Obsidian, Qt Creator, and Unity.
- [ACP for Sublime Text](https://packages.sublimetext.io/packages/ACP) - Sublime Text 4 plugin for running ACP agents such as Claude Code, OpenCode, and Copilot, with persistent sessions and model, mode, and thought-level switching.

## Agent Implementations

- [Claude Agent ACP Adapter](https://github.com/zed-industries/claude-agent-acp) - Lets the Claude Agent SDK be driven from any ACP client.
- [GitHub Copilot CLI ACP Support](https://docs.github.com/en/copilot/reference/acp-server) - Documentation for running Copilot CLI as an ACP agent.
- [Cursor CLI ACP Support](https://cursor.com/docs/cli/acp) - Documentation for Cursor CLI's ACP integration.
- [Goose](https://goose-docs.ai/docs/guides/cli-providers/) - Open-source AI agent that ships native claude-acp and codex-acp providers.
- [ACP Agents Directory](https://agentclientprotocol.com/get-started/agents) - Official listing of agents implementing ACP, including Gemini CLI, Cline, and OpenHands.

## Documentation

- [Rust SDK Book](https://agentclientprotocol.github.io/rust-sdk/) - Design and architecture documentation for the Rust SDK.
- [Python SDK Docs](https://agentclientprotocol.github.io/python-sdk/) - API reference and usage guide for the Python SDK.
- [TypeScript SDK Docs](https://agentclientprotocol.github.io/typescript-sdk/) - API reference and usage guide for the TypeScript SDK.
- [Rust SDK v2 Quickstart](https://agentclientprotocol.github.io/rust-sdk/protocol-v2-quickstart.html) - Runnable ACP v2 agent and client examples behind the `unstable_protocol_v2` feature flag.

## Articles and Guides

- [The Agent Client Protocol Overview](https://www.philschmid.de/acp-overview) - Philipp Schmid's technical overview of ACP's architecture and JSON-RPC design.
- [Introducing Emacs agent-shell](https://xenodium.com/introducing-agent-shell) - Walkthrough of building an ACP-powered agent shell for Emacs.
- [Which Coding Agents Support ACP?](https://agentrq.com/blog/which-coding-agents-support-acp-agent-client-protocol) - AgentRQ table of 33 agents showing native or adapter ACP support, the command that starts each one, and its registry id, as of October 2026.
- [JetBrains Air in IDEs EAP](https://blog.jetbrains.com/ai/2026/10/air-in-ides-eap/) - JetBrains announcement of Air in its IDEs, which runs Codex, Gemini, GitHub Copilot, Claude Agent, and Junie out of the box and connects other agents through ACP.

## Related Protocols

- [Model Context Protocol](https://modelcontextprotocol.io) - Anthropic's open standard for connecting agents to external tools and data sources, frequently paired with ACP-based clients.
- [Language Server Protocol](https://microsoft.github.io/language-server-protocol/) - The protocol ACP is explicitly modeled after, decoupling language intelligence from editors the way ACP decouples agents from editors.

## Automated Updates

The weekly GitHub Action is removed. New items still arrive as a pull request, and nothing merges on its own.

## Contributing

Contributions welcome! Read the [contribution guidelines](CONTRIBUTING.md) first.
