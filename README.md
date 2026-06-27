# Agent Swarm

Multi-Agent Orchestration — Swarm Intelligence fuer das DEVKiTZ Ecosystem.

## Features

- Multi-agent orchestration with NanoChat bridge (Port 3040)
- BotNet fleet: Antigravity (Gemini), OpenCode (Gemma), DeepSeek (R1)
- Hermes messenger for cross-agent communication
- Iceberg archive system for agent memory persistence
- Health check system for swarm monitoring

## Tech Stack

Node.js 18+ · JavaScript ES6+ · WebSocket · MCP Server

## Quick Start

```bash
git clone https://github.com/D-VKITZ/agent-swarm.git
cd agent-swarm
npm install
# Start NanoChat bridge
node bridge/nanochat-server.js
```

## License

MIT
