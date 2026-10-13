# 🔗 chainlist-mcp

[![npm](https://img.shields.io/npm/v/@roxi-os/chainlist-mcp?label=npm&color=c5f24a)](https://www.npmjs.com/package/@roxi-os/chainlist-mcp)
[![license](https://img.shields.io/badge/license-MIT-blue)](./LICENSE)
[![docs](https://img.shields.io/badge/docs-roxi--os.si-black)](https://roxi-os.si/docs/servers/chainlist-mcp)

**The network module of [ROXI OS](https://roxi-os.si)**, the Reasoning-Oriented Execution Interface.

`chainlist-mcp` gives an AI agent live network data from [Chainlist](https://chainlist.org): chain IDs, RPC endpoints, block explorers and native currencies. Nothing has to be hardcoded, and the agent can pick an RPC endpoint that doesn't track you.

---

## ✨ Features

- **Live chain data:** every network on Chainlist, fetched when the agent asks.
- **Privacy-aware RPCs:** each endpoint comes with its tracking policy (`none`, `limited`, and so on).
- **No setup:** no API keys, no wallet, no configuration.
- **Safe to enable:** read-only, with no wallet access at all.
- **Model-agnostic:** works with Claude, GPT, or any client that supports MCP servers over stdio.

---

## 🚀 Quick start

Requires **Node.js 20+** and an MCP client such as Claude Desktop.

Add the server to your client's config (`claude_desktop_config.json`):

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

Restart the client, then try:

```
What's the chain ID for Arbitrum One?
Which RPC endpoints for Base don't track users?
Which explorer should I use for Polygon?
```

---

## ⚙️ Tools

| Tool | Description |
| --- | --- |
| `get-chain-list` | Get every chain on Chainlist: name, chain ID, native currency, explorers, and RPC endpoints with their tracking policy. |

Example entry (excerpt):

```json
{
  "name": "Ethereum Mainnet",
  "chain": "ETH",
  "rpc": [
    { "url": "https://xrpc.cl/eth", "tracking": "none" },
    { "url": "https://rpc.hostdefi.com/api/rpc/ethereum", "tracking": "limited" }
  ]
}
```

Reference: [chainlist-mcp docs](https://roxi-os.si/docs/servers/chainlist-mcp).

---

## 🧱 How it fits

```
Agent → chainlist-mcp → chain ID · RPC · explorer → metamask-mcp / erc20-mcp
```

The agent looks up network details here, then uses them with [`metamask-mcp`](https://github.com/ROXI-OS-SI/metamask-mcp) and [`erc20-mcp`](https://github.com/ROXI-OS-SI/erc20-mcp) to act on the right chain.

---

## 🛠️ Build from source

```bash
git clone https://github.com/ROXI-OS-SI/chainlist-mcp.git
cd chainlist-mcp
pnpm install
pnpm build        # on Windows: npx tsc
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

## 🧩 Part of ROXI OS

| Server | Purpose |
| --- | --- |
| [metamask-mcp](https://github.com/ROXI-OS-SI/metamask-mcp) | Wallet connection and signing |
| **chainlist-mcp** | Chain metadata and RPC endpoints |
| [erc20-mcp](https://github.com/ROXI-OS-SI/erc20-mcp) | ERC-20 transfers, approvals and reads |
| [solc-mcp](https://github.com/ROXI-OS-SI/solc-mcp) | Solidity compilation |

📖 [Documentation](https://roxi-os.si/docs) · 📦 [npm](https://www.npmjs.com/org/roxi-os)

## ⚖️ License

MIT
