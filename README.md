# Necta Agents

An autonomous, multi-agent DeFi system that automates stablecoin yield optimization and portfolio management on Base. Built with Bun, Hono, the Vercel AI SDK, OpenAI, Stakekit, Brahma ConsoleKit, Safe Smart Account, and Supabase.

## Overview

Necta Agents is an AI-powered DeFi yield automation backend that:

- **Continuously monitors** market conditions and wallet status through **Stakekit APIs**
- **Identifies optimal yield opportunities** to maximize returns using **Stakekit's real-time yield data**
- **Executes transactions securely** through **Brahma accounts** (powered by **Safe Smart Account**)
- **Operates autonomously** with no human intervention required

## System Architecture

The system consists of three specialized AI agents working together:

1. **Sentinel Agent** — Market analysis and opportunity detection
   - Monitors market conditions
   - Tracks wallet status
   - Generates intelligence reports

2. **Curator Agent** — Strategy formulation and task generation
   - Analyzes Sentinel reports
   - Determines optimal actions
   - Curates executable tasks

3. **Executor Agent** — Secure transaction execution
   - Processes tasks into transactions
   - Executes via Brahma ConsoleKit
   - Verifies transaction success

### Architectural Diagram

![Architecture](./architecture.png)

### User Flow Diagram

![User Flow](./user-flow.png)

### Core Components

1. **Infrastructure**
   - Event Bus: Inter-agent communication system
   - Memory System: Supabase for persistent storage

2. **Data Sources**
   - Market Data: Stakekit yield API for protocol yields
   - Wallet Status: Account balances and positions

3. **Onchain Execution:** Brahma ConsoleKit

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Runtime | [Bun](https://bun.sh/) |
| Server | [Hono](https://hono.dev/) |
| AI / LLM | [Vercel AI SDK](https://sdk.vercel.ai/), [OpenAI](https://openai.com/) |
| Database | [Supabase](https://supabase.com/) |
| Yield Data | [Stakekit](https://stakek.it/) |
| Onchain Execution | [Brahma ConsoleKit](https://consolekit.brahma.fi/) |
| Smart Account | [Safe](https://safe.global/) |

## Project Structure

```
src/
├── agents/                    # Agent implementations
│   ├── agent.ts              # Base agent class
│   ├── index.ts              # Agent system initialization
│   ├── curator/              # Curator agent
│   │   ├── index.ts
│   │   └── toolkit.ts
│   ├── executor/             # Executor agent
│   │   ├── index.ts
│   │   └── toolkit.ts
│   └── sentinel/             # Sentinel agent
│       ├── index.ts
│       └── toolkit.ts
├── services/                 # External services integration
│   └── console-kit/          # ConsoleKit integration
│       ├── index.ts
│       ├── core-actions.ts
│       ├── deploy-automation-account.ts
│       ├── register-executor.ts
│       ├── types.ts
│       └── utils.ts
├── system-prompts/          # Agent behavior definitions
│   ├── index.ts
│   ├── curator-system-prompt.ts
│   ├── executor-system-prompt.ts
│   └── sentinel-system-prompt.ts
├── data/                    # Data fetching and processing
│   ├── index.ts
│   ├── stakekit.ts         # Stakekit integration
│   ├── stakekit.test.ts    # Stakekit integration test
│   └── types.ts
├── comms/                   # Inter-agent communication
│   ├── index.ts
│   └── event-bus.ts
├── config/                  # Chain and protocol configs
│   ├── index.ts
│   └── chains.ts
├── app.ts                   # Hono app setup
├── env.ts                   # Environment configuration
├── index.ts                # Main entry point
└── setup.ts                # System initialization
```

## Security

- **Non-custodial:** All funds remain in user's Brahma account
- **Secure execution:** ConsoleKit handles transaction security
- **Limited permissions:** Executor only signs transaction data
- **Transaction simulation:** All transactions are simulated before execution

## Local Setup

1. Clone and install:

```bash
git clone https://github.com/NectaFi/necta-agents.git
cd necta-agents
bun install
```

2. Configure environment:

```bash
cp .env.example .env
```

3. Start the server:

```bash
ENABLE_AGENTS=true bun src/index.ts
```

## Related

- **Frontend:** [necta-app](https://github.com/NectaFi/necta-app)

## License

MIT License — See [LICENSE](LICENSE) for details.

## Disclaimer

This code is provided as-is with no guarantees. It has not been audited. Do not use with real funds. This is not financial advice.
