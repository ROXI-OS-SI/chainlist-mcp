# 🔗 chainlist-mcp

`chainlist-mcp` is the chain metadata module of **[ROXI OS](https://github.com/ROXI-OS-SI)**, the Reasoning-Oriented Execution Interface for onchain agents.

It gives an agent up-to-date network information from [Chainlist](https://chainlist.org/) (chain IDs, RPC endpoints, explorers and native currencies), so nothing has to be hardcoded. Ask _"Which RPC can I use for Arbitrum?"_ and the agent can look it up.

📖 Docs: [roxi-ten.vercel.app/docs/servers/chainlist-mcp](https://roxi-ten.vercel.app/docs/servers/chainlist-mcp)

---

## ✨ Features

- **Live chain data** — fetched from Chainlist, including RPC endpoints and whether each one tracks users.
- **No configuration** — no API keys and no wallet needed.
- **Model-agnostic** — works with Claude, GPT, or any client that speaks the Model Context Protocol (MCP).
- **Composable** — feeds network details to [`metamask-mcp`](https://github.com/ROXI-OS-SI/metamask-mcp) and [`erc20-mcp`](https://github.com/ROXI-OS-SI/erc20-mcp).

## 🧱 How it fits

```
Agent → chainlist-mcp → RPC · chain ID · symbol → Transaction modules
```

---

## 🚀 Quick start

Requires **Node.js 20+**.

Add it to your MCP client (for example Claude Desktop's `claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "chainlist": {
      "command": "npx",
      "args": ["-y", "@roxi-os/chainlist-mcp"]
    }
  }
}
```

### From source

```bash
git clone https://github.com/ROXI-OS-SI/chainlist-mcp.git
cd chainlist-mcp
pnpm install
pnpm build
```

Then point your client at the build:

```json
{
  "mcpServers": {
    "chainlist": {
      "command": "node",
      "args": ["/absolute/path/to/chainlist-mcp/build/index.js"]
    }
  }
}
```

---

## ⚙️ Tools

| Tool | Description |
| --- | --- |
| `get-chain-list` | Get a list of all chains information. |

---

## ⚖️ License

MIT
