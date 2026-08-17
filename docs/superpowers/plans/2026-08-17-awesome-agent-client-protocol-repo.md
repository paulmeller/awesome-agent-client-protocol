# Awesome Agent Client Protocol Repo Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build and publish `paulmeller/awesome-agent-client-protocol`, a new public awesome-list repo for the Agent Client Protocol (ACP), mirroring the structure and automation of the peer repo `paulmeller/awesome-managed-agents`.

**Architecture:** A static curated `README.md` plus a GitHub Actions workflow that runs a Claude Managed Agents session (guided by a custom curator skill) weekly to find and PR new resources — the same mechanism as the peer repo, with content adapted to the ACP topic.

**Tech Stack:** Markdown, GitHub Actions (YAML), Python 3.12 (`anthropic` SDK), `gh` CLI.

## Global Constraints

- License: CC0 1.0 Universal, verbatim text copied from the peer repo's `LICENSE`.
- List item format: `- [Name](URL) - Description.` — description starts with a capital letter, ends with a period, and does not repeat the link text.
- Every seeded URL must be one already verified during design (see `docs/superpowers/specs/2026-08-17-awesome-agent-client-protocol-design.md`) — do not add any new unverified URL while implementing this plan.
- `.skill-id` is gitignored and never committed.
- Repo visibility: public.
- No "License" section in the README (CC0 lives only in `LICENSE`).
- The "Contents" TOC lists only the 7 content sections — never "Automated Updates" or "Contributing".
- Working directory for all tasks: `/Users/paulmeller/Projects/awesome-agent-client-protocol` (already `git init`'d, with one commit containing the design spec).

---

### Task 1: Repo scaffolding (LICENSE, .gitignore, CONTRIBUTING.md)

**Files:**
- Create: `LICENSE`
- Create: `.gitignore`
- Create: `CONTRIBUTING.md`

**Interfaces:**
- Consumes: none.
- Produces: none consumed by later tasks' code, but `CONTRIBUTING.md` is linked from `README.md` in Task 2 (must exist at the exact relative path `CONTRIBUTING.md`).

- [ ] **Step 1: Create `LICENSE`**

```
CC0 1.0 Universal (CC0 1.0)
Public Domain Dedication

The person who associated a work with this deed has dedicated the work to
the public domain by waiving all of his or her rights to the work worldwide
under copyright law, including all related and neighboring rights, to the
extent allowed by law.

You can copy, modify, distribute and perform the work, even for commercial
purposes, all without asking permission.

https://creativecommons.org/publicdomain/zero/1.0/
```

- [ ] **Step 2: Create `.gitignore`**

```
__pycache__/
.skill-id
```

- [ ] **Step 3: Create `CONTRIBUTING.md`**

```markdown
# Contributing

Thank you for your interest in contributing to Awesome Agent Client Protocol!

## Guidelines

- Search previous suggestions before making a new one to avoid duplicates.
- Make an individual pull request for each suggestion.
- Use the following format: `[Resource Name](link) - Description.`
- Keep descriptions short and simple, but descriptive.
- Start the description with a capital and end with a period.
- New categories or improvements to the existing categorization are welcome.
- Check your spelling and grammar.
- Make sure your text editor is set to remove trailing whitespace.
- The pull request and commit should have a useful title.

## Quality Standards

To be included, a resource should:

- Be directly related to the Agent Client Protocol.
- Be actively maintained (for tools and libraries).
- Have a clear purpose and value to the community.
- Not be a duplicate of an existing entry.

## Updating Your PR

If the maintainers notice anything that we'd like changed, we'll ask you to edit your PR before we merge it. If you're not sure how to do that, [here is a guide](https://github.com/RichardLitt/knowledge/blob/master/github/amending-a-commit-guide.md) on the different ways you can update your PR.
```

- [ ] **Step 4: Verify files exist and LICENSE matches the peer repo exactly**

Run: `diff /Users/paulmeller/Projects/awesome-managed-agents/LICENSE LICENSE && test -f .gitignore && test -f CONTRIBUTING.md && echo "Task 1 files OK"`
Expected: `Task 1 files OK` (the `diff` prints nothing and exits 0 since the license text is identical).

- [ ] **Step 5: Commit**

```bash
git add LICENSE .gitignore CONTRIBUTING.md
git commit -m "Add license, gitignore, and contributing guidelines"
```

---

### Task 2: README.md

**Files:**
- Create: `README.md`

**Interfaces:**
- Consumes: none.
- Produces: none consumed by later tasks' code. Task 5's workflow and Task 4's `update_list.py` both reference `README.md` by path, and Task 3's curator skill references the same 7 section names — the section names here are the canonical list every later task must match exactly: `Official Resources`, `SDKs`, `Editor and Client Implementations`, `Agent Implementations`, `Documentation`, `Articles and Guides`, `Related Protocols`.

- [ ] **Step 1: Create `README.md`**

```markdown
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

## Agent Implementations

- [Claude Agent ACP Adapter](https://github.com/zed-industries/claude-agent-acp) - Lets the Claude Agent SDK be driven from any ACP client.
- [GitHub Copilot CLI ACP Support](https://docs.github.com/en/copilot/reference/acp-server) - Documentation for running Copilot CLI as an ACP agent.
- [Cursor CLI ACP Support](https://cursor.com/docs/cli/acp) - Documentation for Cursor CLI's ACP integration.
- [Goose](https://goose-docs.ai/docs/guides/cli-providers/) - Open-source AI agent that ships native claude-acp and codex-acp providers.
- [ACP Agents Directory](https://agentclientprotocol.com/get-started/agents) - Official listing of agents implementing ACP, including Gemini CLI, Cline, and OpenHands.

## Documentation

- [Get Started: Clients](https://agentclientprotocol.com/get-started/clients) - Guide for editor authors building an ACP client.
- [Get Started: Agents](https://agentclientprotocol.com/get-started/agents) - Guide for agent authors implementing the ACP agent side.
- [Rust SDK Book](https://agentclientprotocol.github.io/rust-sdk/) - Design and architecture documentation for the Rust SDK.
- [Python SDK Docs](https://agentclientprotocol.github.io/python-sdk/) - API reference and usage guide for the Python SDK.
- [TypeScript SDK Docs](https://agentclientprotocol.github.io/typescript-sdk/) - API reference and usage guide for the TypeScript SDK.

## Articles and Guides

- [The Agent Client Protocol Overview](https://www.philschmid.de/acp-overview) - Philipp Schmid's technical overview of ACP's architecture and JSON-RPC design.
- [Introducing Emacs agent-shell](https://xenodium.com/introducing-agent-shell) - Walkthrough of building an ACP-powered agent shell for Emacs.

## Related Protocols

- [Model Context Protocol](https://modelcontextprotocol.io) - Anthropic's open standard for connecting agents to external tools and data sources, frequently paired with ACP-based clients.
- [Language Server Protocol](https://microsoft.github.io/language-server-protocol/) - The protocol ACP is explicitly modeled after, decoupling language intelligence from editors the way ACP decouples agents from editors.

## Automated Updates

This list is itself maintained using Claude Managed Agents. A [weekly workflow](.github/workflows/update-list.yml) spins up a Managed Agents session with a [custom curator skill](skills/awesome-list-curator/SKILL.md) that searches the web for new resources, scores each candidate against quality criteria, and opens a PR with any additions. See [`scripts/`](scripts/) for the implementation.

## Contributing

Contributions welcome! Read the [contribution guidelines](CONTRIBUTING.md) first.
```

- [ ] **Step 2: Verify TOC anchors match headings exactly**

Run:
```bash
python3 - <<'EOF'
import re
content = open("README.md").read()
headings = re.findall(r'^## (.+)$', content, re.MULTILINE)
content_headings = [h for h in headings if h not in ("Contents", "Automated Updates", "Contributing")]
def slug(h):
    return re.sub(r'[^a-z0-9\- ]', '', h.lower()).replace(' ', '-')
expected = {f"#{slug(h)}" for h in content_headings}
toc_block = content.split("## Contents")[1].split("## Official Resources")[0]
toc_links = {l.strip("()") for l in re.findall(r'\(#\S+?\)', toc_block)}
assert toc_links == expected, f"Mismatch: TOC={toc_links} vs headings={expected}"
assert content_headings == [
    "Official Resources", "SDKs", "Editor and Client Implementations",
    "Agent Implementations", "Documentation", "Articles and Guides", "Related Protocols",
], content_headings
print("TOC anchors match headings:", sorted(expected))
EOF
```
Expected: `TOC anchors match headings: [...]` printed, script exits 0.

- [ ] **Step 3: Verify every list item matches the awesome-list format**

Scoped to skip the Contents TOC block, whose anchor links intentionally don't match the resource-entry pattern.

Run:
```bash
python3 - <<'EOF'
import re
content = open("README.md").read()
body = content.split("## Official Resources", 1)[1].split("## Automated Updates", 1)[0]
body = "## Official Resources" + body
pattern = re.compile(r'^- \[.+?\]\(https?://\S+\) - [A-Z].*\.$')
bad = [line for line in body.splitlines() if line.startswith("- [") and not pattern.match(line)]
assert not bad, f"Malformed list lines: {bad}"
print("All list items match the required format.")
EOF
```
Expected: `All list items match the required format.`

- [ ] **Step 4: Commit**

```bash
git add README.md
git commit -m "Add README with seeded, verified ACP resources"
```

---

### Task 3: Curator skill (`skills/awesome-list-curator/SKILL.md`)

**Files:**
- Create: `skills/awesome-list-curator/SKILL.md`

**Interfaces:**
- Consumes: the 7 section names from Task 2's `README.md` (must list them identically in the "Awesome List Formatting Rules" section below).
- Produces: `skill_id`-referenced content later uploaded by `scripts/setup_skill.py` (Task 4) — no code interface, just the file's existence at this exact path (`setup_skill.py`'s `SKILL_DIR` points here).

- [ ] **Step 1: Create `skills/awesome-list-curator/SKILL.md`**

```markdown
---
name: awesome-list-curator
description: Finds, assesses, and curates new resources for an awesome-list about the Agent Client Protocol (ACP). Use when searching for and evaluating blog posts, GitHub repos, tutorials, videos, and press coverage to add to a curated list.
---

# Awesome List Curator

A skill for discovering and evaluating new resources to add to an awesome-list.

## Search Strategy

Run multiple searches to cover different resource types. Use `web_search` for each:

1. **Blog posts and tutorials** — Search for recent posts teaching people how to use the Agent Client Protocol. Try queries like:
   - `"Agent Client Protocol" tutorial`
   - `"Agent Client Protocol" guide`
   - `ACP editor integration guide`
   - `site:medium.com "Agent Client Protocol"`
   - `site:dev.to "Agent Client Protocol"`

2. **GitHub repositories** — Search for community projects and tools. Try:
   - `"agent-client-protocol" site:github.com`
   - `"Agent Client Protocol" client OR agent site:github.com`
   - `ACP editor plugin site:github.com`

3. **Press and news** — Search for coverage from tech publications:
   - `"Agent Client Protocol" news`
   - `Zed "Agent Client Protocol" launch`

4. **Videos and talks** — Search for demos and conference talks:
   - `"Agent Client Protocol" site:youtube.com`
   - `"Agent Client Protocol" talk OR demo OR walkthrough`

5. **Integrations** — Search for editor, IDE, and agent integrations:
   - `"Agent Client Protocol" integration`
   - `ACP client OR agent implementation`

## Assessment Criteria

For each candidate resource, evaluate against these criteria. A resource must pass ALL required criteria and score well on quality signals.

### Required (must pass all)

- **Exists** — The URL is accessible. Use `web_fetch` to verify.
- **Relevant** — Directly about the Agent Client Protocol, not just AI coding agents in general.
- **Not a duplicate** — Not already in the list (check URLs AND content — same article on different domains counts as duplicate).
- **Not spam** — Not a low-effort SEO article, affiliate link farm, or auto-generated content.

### Quality Signals (aim for 3+ out of 5)

- **Substantive** — Contains original insight, working code, or meaningful analysis (not just a product summary).
- **Accurate** — Technical claims are correct based on what you know about ACP.
- **Maintained** — For repos: has recent commits, a README, and isn't archived. For articles: published within the last 6 months.
- **Useful** — Would help a developer building with or against ACP.
- **Credible** — From a known publication, established developer, or official source.

### Scoring

Rate each resource:

- **A** — High quality, clearly belongs in the list. Add it.
- **B** — Decent quality, adds value. Add it.
- **C** — Borderline. Skip unless the section is sparse.
- **D** — Low quality or barely relevant. Skip.

Only add resources rated A or B.

## Output Format

Write your assessment to `/mnt/session/outputs/assessment.json` as:

```json
{
  "searched_at": "2026-04-11T12:00:00Z",
  "queries_run": ["query1", "query2"],
  "candidates_found": 12,
  "candidates_accepted": 3,
  "candidates": [
    {
      "title": "Resource Name",
      "url": "https://example.com/resource",
      "section": "Articles and Guides",
      "description": "Description starting uppercase, ending with period.",
      "rating": "A",
      "rationale": "Why this resource was accepted or rejected."
    }
  ]
}
```

Then write the complete updated README.md to `/mnt/session/outputs/README.md`.

## Awesome List Formatting Rules

Every list item must follow this exact format:

```
- [Name](URL) - Description starting with uppercase, ending with period.
```

Additional rules:
- Current sections, in order: Official Resources, SDKs, Editor and Client Implementations, Agent Implementations, Documentation, Articles and Guides, Related Protocols. New categories are welcome if a resource doesn't fit any existing one and there are enough real entries to justify a new section — don't create a section for a single item.
- Add new items at the BOTTOM of the appropriate section.
- Never remove existing items.
- No License section in the README.
- Top description describes the subject, not the list.
- Table of contents section must be named "Contents".
- Contributing and Automated Updates must not appear in Contents.
- Use ` - ` (space-dash-space) between link and description.
- Descriptions must not repeat the link text.
```

- [ ] **Step 2: Verify frontmatter is valid and section list matches README.md exactly**

Run:
```bash
python3 - <<'EOF'
import re, yaml
skill = open("skills/awesome-list-curator/SKILL.md").read()
m = re.match(r'^---\n(.*?)\n---\n', skill, re.DOTALL)
assert m, "No frontmatter found"
data = yaml.safe_load(m.group(1))
assert data["name"] == "awesome-list-curator"
assert "Agent Client Protocol" in data["description"]

readme = open("README.md").read()
readme_sections = re.findall(r'^## (.+)$', readme, re.MULTILINE)
readme_sections = [h for h in readme_sections if h not in ("Contents", "Automated Updates", "Contributing")]
sections_line = [l for l in skill.splitlines() if l.startswith("- Current sections, in order:")][0]
listed = sections_line.split(":", 1)[1].split(".")[0].strip().split(", ")
assert listed == readme_sections, f"{listed} != {readme_sections}"
print("Frontmatter and section list OK:", listed)
EOF
```
Expected: `Frontmatter and section list OK: [...]` printed, script exits 0.

- [ ] **Step 3: Commit**

```bash
git add skills/awesome-list-curator/SKILL.md
git commit -m "Add awesome-list-curator skill for ACP"
```

---

### Task 4: Scripts (`scripts/setup_skill.py`, `scripts/update_list.py`)

**Files:**
- Create: `scripts/setup_skill.py`
- Create: `scripts/update_list.py`

**Interfaces:**
- Consumes: `skills/awesome-list-curator` directory (Task 3), `.skill-id` file (generated at runtime, not committed), `README.md` (Task 2).
- Produces: no code consumed by later tasks — Task 5's workflow invokes `python scripts/update_list.py` by path and expects it to read/write `README.md` at the repo root, exactly as implemented here.

- [ ] **Step 1: Create `scripts/setup_skill.py`**

```python
"""Upload the awesome-list-curator skill to Anthropic. Run once, then store the skill ID."""

import json
import os

from anthropic import Anthropic
from anthropic.lib import files_from_dir

SKILL_DIR = os.path.join(os.path.dirname(__file__), "..", "skills", "awesome-list-curator")
SKILL_ID_FILE = os.path.join(os.path.dirname(__file__), "..", ".skill-id")


def run():
    client = Anthropic()

    # Check if skill already exists
    if os.path.exists(SKILL_ID_FILE):
        with open(SKILL_ID_FILE) as f:
            skill_id = f.read().strip()
        print(f"Skill already exists: {skill_id}")
        print("Creating new version...")
        client.beta.skills.versions.create(
            skill_id=skill_id,
            files=files_from_dir(SKILL_DIR),
            betas=["skills-2025-10-02"],
        )
        print("Skill version updated.")
        return

    skill = client.beta.skills.create(
        display_title="ACP Awesome List Curator",
        files=files_from_dir(SKILL_DIR),
        betas=["skills-2025-10-02"],
    )

    with open(SKILL_ID_FILE, "w") as f:
        f.write(skill.id)

    print(f"Skill created: {skill.id}")
    print(f"Stored skill ID in .skill-id")


if __name__ == "__main__":
    run()
```

- [ ] **Step 2: Create `scripts/update_list.py`**

```python
"""Use Claude Managed Agents with the awesome-list-curator skill to find and assess new resources."""

import json
import os
import sys

from anthropic import Anthropic

SCRIPTS_DIR = os.path.dirname(__file__)
README_PATH = os.path.join(SCRIPTS_DIR, "..", "README.md")
SKILL_ID_FILE = os.path.join(SCRIPTS_DIR, "..", ".skill-id")


def get_skill_id():
    """Read the skill ID from the .skill-id file, or from CURATOR_SKILL_ID env var."""
    skill_id = os.environ.get("CURATOR_SKILL_ID")
    if skill_id:
        return skill_id
    if os.path.exists(SKILL_ID_FILE):
        with open(SKILL_ID_FILE) as f:
            return f.read().strip()
    print("No skill ID found. Run setup_skill.py first or set CURATOR_SKILL_ID.", file=sys.stderr)
    sys.exit(1)


def run():
    client = Anthropic()
    skill_id = get_skill_id()

    with open(README_PATH) as f:
        current_readme = f.read()

    agent = client.beta.agents.create(
        name="Awesome List Updater",
        model="claude-sonnet-4-6",
        system=(
            "You are a research agent that maintains an awesome-list for the Agent Client Protocol (ACP). "
            "Use the awesome-list-curator skill to guide your search strategy, assessment criteria, "
            "and output format. Follow the skill instructions exactly."
        ),
        tools=[{"type": "agent_toolset_20260401"}],
        skills=[{"type": "custom", "skill_id": skill_id, "version": "latest"}],
    )

    environment = client.beta.environments.create(
        name="updater-env",
        config={"type": "cloud", "networking": {"type": "unrestricted"}},
    )

    session = client.beta.sessions.create(
        agent=agent.id,
        environment_id=environment.id,
        title="Weekly awesome-list update",
    )

    print(f"Session created: {session.id}")
    print(f"Using skill: {skill_id}")

    # Collect all agent message text and track tool use
    collected_text = []

    with client.beta.sessions.events.stream(session.id) as stream:
        client.beta.sessions.events.send(
            session.id,
            events=[
                {
                    "type": "user.message",
                    "content": [
                        {
                            "type": "text",
                            "text": (
                                "Here is the current README.md for the awesome-agent-client-protocol repo.\n\n"
                                "Use the awesome-list-curator skill to:\n"
                                "1. Search for new resources using the search strategy.\n"
                                "2. Assess each candidate against the criteria and score them.\n"
                                "3. Write the assessment JSON and updated README.md to /mnt/session/outputs/.\n"
                                "4. After writing the files, print the assessment JSON, then print the "
                                "exact marker line `===README_START===` followed by the complete updated "
                                "README.md content, followed by `===README_END===`.\n\n"
                                "Only add resources rated A or B.\n\n"
                                "---\n\n"
                                f"{current_readme}"
                            ),
                        }
                    ],
                }
            ],
        )

        for event in stream:
            match event.type:
                case "agent.tool_use":
                    print(f"  [tool: {event.name}]")
                case "agent.message":
                    for block in event.content:
                        if hasattr(block, "text"):
                            collected_text.append(block.text)
                            # Print a preview for progress
                            preview = block.text[:200].replace("\n", " ")
                            if preview.strip():
                                print(f"  {preview}")
                case "session.status_idle":
                    print("Agent finished.")
                    break
                case "session.error":
                    if hasattr(event, "error"):
                        print(f"Session error: {event.error}", file=sys.stderr)
                case "session.status_terminated":
                    print("Agent terminated unexpectedly.", file=sys.stderr)
                    sys.exit(1)

    # Extract README from agent output using markers
    full_output = "\n".join(collected_text)

    start_marker = "===README_START==="
    end_marker = "===README_END==="

    if start_marker not in full_output:
        print("No README markers found in agent output. No changes.", file=sys.stderr)
        sys.exit(0)

    start_idx = full_output.index(start_marker) + len(start_marker)
    end_idx = full_output.index(end_marker) if end_marker in full_output else len(full_output)
    updated_readme = full_output[start_idx:end_idx].strip()

    if not updated_readme:
        print("Empty README extracted. No changes.", file=sys.stderr)
        sys.exit(0)

    if updated_readme.strip() == current_readme.strip():
        print("No new resources found.")
        sys.exit(0)

    with open(README_PATH, "w") as f:
        f.write(updated_readme + "\n")

    print("README.md updated with new resources.")


if __name__ == "__main__":
    run()
```

- [ ] **Step 3: Verify both scripts are syntactically valid and reference ACP correctly**

Run:
```bash
python3 -m py_compile scripts/setup_skill.py scripts/update_list.py && echo "syntax OK"
grep -q "Agent Client Protocol" scripts/update_list.py && echo "topic reference OK"
grep -q "ACP Awesome List Curator" scripts/setup_skill.py && echo "display title OK"
rm -rf scripts/__pycache__
```
Expected: `syntax OK`, `topic reference OK`, `display title OK` all printed.

- [ ] **Step 4: Commit**

```bash
git add scripts/setup_skill.py scripts/update_list.py
git commit -m "Add setup and update scripts for the ACP curator skill"
```

---

### Task 5: GitHub Actions workflow

**Files:**
- Create: `.github/workflows/update-list.yml`

**Interfaces:**
- Consumes: `scripts/update_list.py` (Task 4) by path (`python scripts/update_list.py`), `ANTHROPIC_API_KEY`/`CURATOR_SKILL_ID`/`GITHUB_TOKEN` as env vars (secrets, not created by this task — see note below).
- Produces: nothing consumed by other tasks; this is the last content file.

The peer repo's workflow file contains no topic-specific text (no mention of "Managed Agents" as a *topic*, only as the *mechanism name*, which is unchanged here) — so it is copied byte-for-byte.

- [ ] **Step 1: Create `.github/workflows/update-list.yml`**

```yaml
name: Update awesome list

on:
  schedule:
    - cron: "0 9 * * 1" # Every Monday at 9am UTC
  workflow_dispatch:

permissions:
  contents: write
  pull-requests: write

jobs:
  update:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-python@v5
        with:
          python-version: "3.12"

      - name: Install dependencies
        run: pip install anthropic

      - name: Run update agent
        env:
          ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
          CURATOR_SKILL_ID: ${{ secrets.CURATOR_SKILL_ID }}
        run: python scripts/update_list.py

      - name: Check for changes
        id: diff
        run: |
          git diff --quiet README.md && echo "changed=false" >> "$GITHUB_OUTPUT" || echo "changed=true" >> "$GITHUB_OUTPUT"

      - name: Create pull request
        if: steps.diff.outputs.changed == 'true'
        env:
          GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        run: |
          BRANCH="update/awesome-list-$(date +%Y-%m-%d)-${GITHUB_RUN_ID}"
          git checkout -b "$BRANCH"
          git config user.name "github-actions[bot]"
          git config user.email "41898282+github-actions[bot]@users.noreply.github.com"
          git add README.md
          git commit -m "Add new resources found by Managed Agents"
          git push -u origin "$BRANCH"
          gh pr create \
            --title "Update awesome list with new resources" \
            --body "This PR was generated automatically by a Claude Managed Agents session using the awesome-list-curator skill to search for, assess, and curate new resources. The agent scores each candidate (A-D) and only adds resources rated A or B. Please review the additions before merging."
```

- [ ] **Step 2: Verify the workflow is valid YAML and identical to the peer repo's**

Run:
```bash
diff /Users/paulmeller/Projects/awesome-managed-agents/.github/workflows/update-list.yml .github/workflows/update-list.yml && echo "identical to peer template"
python3 -c "import yaml; yaml.safe_load(open('.github/workflows/update-list.yml')); print('valid YAML')"
```
Expected: `identical to peer template` and `valid YAML` both printed.

- [ ] **Step 3: Commit**

```bash
git add .github/workflows/update-list.yml
git commit -m "Add weekly awesome-list update workflow"
```

**Note (not a task step — do not automate):** This workflow will not run successfully until `ANTHROPIC_API_KEY` and `CURATOR_SKILL_ID` repo secrets are added, and `CURATOR_SKILL_ID` requires first running `scripts/setup_skill.py` locally with a real `ANTHROPIC_API_KEY` to create the skill and obtain its ID. That's a deliberate, separate action for the user to take when ready — out of scope for this plan (see design spec).

---

### Task 6: Create and publish the GitHub repository

**Files:** none (no file changes — this task creates the remote repo and pushes existing history).

**Interfaces:**
- Consumes: the full local git history from Tasks 1–5.
- Produces: `https://github.com/paulmeller/awesome-agent-client-protocol`, remote `origin`, pushed `main` branch.

- [ ] **Step 1: Confirm local state is clean and all 5 prior commits are present**

Run: `git status --porcelain && git log --oneline`
Expected: no output from `git status --porcelain` (clean tree); `git log --oneline` shows 6 commits total (design spec + 5 task commits), oldest-first: spec, license/gitignore/contributing, README, curator skill, scripts, workflow.

- [ ] **Step 2: Create the GitHub repo from the local source and push**

Run:
```bash
gh repo create paulmeller/awesome-agent-client-protocol \
  --public \
  --description "A curated list of resources, SDKs, and implementations for the Agent Client Protocol (ACP)." \
  --source=. \
  --remote=origin \
  --push
```
Expected: output ending with `https://github.com/paulmeller/awesome-agent-client-protocol` and a confirmation the branch was pushed.

- [ ] **Step 3: Verify the repo is live and public with the expected files**

Run:
```bash
gh repo view paulmeller/awesome-agent-client-protocol --json name,visibility,url,description
gh api repos/paulmeller/awesome-agent-client-protocol/contents --jq '.[].name' | sort
```
Expected: JSON showing `"visibility": "PUBLIC"` and the correct `url`/`description`; the file listing includes `CONTRIBUTING.md`, `LICENSE`, `README.md`, `.github`, `.gitignore`, `scripts`, `skills`, `docs`.

No commit needed — nothing local changes in this task.

---

## Post-plan (not part of this plan, for user reference)

To turn on the automated weekly curator once ready:
1. Set a real `ANTHROPIC_API_KEY` locally and run `python3 scripts/setup_skill.py` — this creates the skill on Anthropic's side and writes `.skill-id` (gitignored).
2. Add `ANTHROPIC_API_KEY` and `CURATOR_SKILL_ID` (the contents of `.skill-id`) as GitHub Actions secrets on the new repo: `gh secret set ANTHROPIC_API_KEY --repo paulmeller/awesome-agent-client-protocol` and `gh secret set CURATOR_SKILL_ID --repo paulmeller/awesome-agent-client-protocol`.
3. Optionally trigger a first run manually: `gh workflow run update-list.yml --repo paulmeller/awesome-agent-client-protocol`.
