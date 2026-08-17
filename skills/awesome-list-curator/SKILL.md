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
