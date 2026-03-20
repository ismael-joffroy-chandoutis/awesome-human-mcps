# Awesome Human MCPs

> A curated list of MCP servers that let AI agents delegate tasks to real humans.

The missing link between AI agents and the physical world. When your agent can't make a phone call, pick up a package, or attend a meeting — these MCPs bridge the gap.

---

## Marketplaces — AI hires humans

| Platform | MCP | Tasks | Pricing | Notes |
|----------|-----|-------|---------|-------|
| [RentAHuman.ai](https://rentahuman.ai/) | `https://rentahuman.ai/mcp` | Physical errands, photos, meetings, document signing | $15-175/h | 645K+ registered workers, 100+ countries. [MCP guide](https://rentahuman.ai/blog/mcp-integration-guide) |
| [HumanMCP.ai](https://www.humanmcp.ai/) | `https://www.humanmcp.ai/mcp` | Phone calls, research, verification, localized copy | ~$28/task | Specialized in tasks AI fundamentally can't do (voice calls, physical verification) |
| [HireAHuman.ai](https://www.hireahuman.ai/) | `https://www.hireahuman.ai/mcp` | Freelance work, revenue-sharing model | Variable | Automation revenue funds human livelihoods |

## Approval Layers — Human-in-the-loop

| Platform | MCP | Use Case | Install |
|----------|-----|----------|---------|
| [GoToHuman](https://gotohuman.com) | `npx @gotohuman/mcp-server` | Approval workflows before sensitive actions | [GitHub](https://github.com/gotohuman/gotohuman-mcp-server) |
| [ask-human-mcp](https://github.com/Masony817/ask-human-mcp) | Self-hosted | Zero-config: AI writes to markdown, human edits, agent resumes | GitHub |
| [human-in-the-loop](https://github.com/KOBA789/human-in-the-loop) | Self-hosted (Rust) | AI asks questions via Discord, waits for reply | 221 stars |
| [human-mcp](https://github.com/upamune/human-mcp) | Self-hosted (Python) | Human as MCP server (eye, hand, mouth tools). Streamlit UI | 45 stars |
| [mcp-human-loop](https://github.com/boorich/mcp-human-loop) | Self-hosted | Scores requests on complexity/risk to decide if human review needed | GitHub |
| [telegram-human-in-the-loop](https://github.com/theohero/telegram-human-in-the-loop) | Self-hosted | HITL via Telegram | GitHub |

## Gig Economy — Delivery & Services

| Platform | MCP | Type | Notes |
|----------|-----|------|-------|
| [DoorDash Drive](https://developer.doordash.com) | [Community MCP](https://github.com/JordanDalton/DoorDash-MCP-Server) | B2B logistics (not consumer ordering) | 14 tools, requires developer credentials |
| [Instacart](https://docs.instacart.com/developer_platform_api/guide/tutorials/mcp/) | `https://mcp.instacart.com/mcp` | Official. Recipes + shopping lists | API key required |
| Uber Eats | [Community MCP](https://github.com/ericzakariasson/uber-eats) | Playwright-based POC | Experimental |
| Fiverr | [Bright Data MCP](https://brightdata.com/ai/mcp-server/fiverr) | Scraper (5000 free req/month) | No official API |

## Not Available (yet)

| Platform | Status |
|----------|--------|
| TaskRabbit | No API, no MCP |
| Upwork | No MCP. CEO confirmed agents already trying to post jobs (March 2026) |
| Uber Rides | Internal MCP gateway exists but not public |

---

## Quick Start

Add to your Claude Code MCP config (`~/.claude.json`):

```json
{
  "mcpServers": {
    "rentahuman": {
      "type": "http",
      "url": "https://rentahuman.ai/mcp"
    },
    "gotohuman": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@gotohuman/mcp-server"],
      "env": {
        "GOTOHUMAN_API_KEY": "your-key"
      }
    },
    "instacart": {
      "type": "http",
      "url": "https://mcp.instacart.com/mcp"
    },
    "humanmcp": {
      "type": "http",
      "url": "https://www.humanmcp.ai/mcp"
    }
  }
}
```

Restart Claude Code. Type `/mcp` to verify servers are connected.

---

## Protocol-Level: MCP Elicitation

The MCP spec added **Elicitation** (June 2025, draft) — a built-in mechanism for MCP servers to pause execution and request structured input from the user. This is the standardized answer to human-in-the-loop at the protocol level.

---

## Industry Context

- **RentAHuman.ai** launched Feb 2, 2026. Covered by Nature, Newsweek, Futurism, Wired.
- **Upwork CEO** revealed in March 2026 that AI agents are already attempting to create accounts and hire freelancers.
- **DoorDash** launched "Tasks" app (March 19, 2026) paying Dashers to collect AI training data.
- **Uber** has built an internal MCP gateway exposing all endpoints. 84% of Uber devs use agentic coding.

---

## Contributing

PRs welcome. Add new platforms, fix broken links, share your integration experience.

## License

CC0 1.0 Universal — Public Domain
