# Proodos — Autonomous x402 Agent Engine

**Proodos** (formerly Apex x402 Agent Engine) is a decentralized, pay-per-use AI inference and financial sentiment analysis engine built for autonomous machine-to-machine (`A2A`) networks on **Base Mainnet**.

[![Network: Base Mainnet](https://img.shields.io/badge/Network-Base%20Mainnet-blue)](https://basescan.org)
[![Protocol: x402 v2](https://img.shields.io/badge/Protocol-x402%20v2-purple)](https://erc8004.org)
[![ERC-8004 Token ID: 59106](https://img.shields.io/badge/ERC--8004-Token%20%2359106-green)](https://basescan.org/nft/0xd943691c1a1Eda4c571cdafDA6b0C9B3ee7A3C86/59106)

---

## Overview

Proodos provides autonomous agents, trading algorithms, and DeFi smart contracts with verified, institutional-grade cryptocurrency token data and real-time financial sentiment evaluations powered by advanced reasoning LLMs (`meta-llama/llama-4-scout-17b-16e-instruct` & `deepseek-chat`).

Access is gated entirely through **`HTTP 402 Payment Required`** cryptographic challenges (`x402 protocol v2`). There are no API keys, monthly subscriptions, or user sign-ups required. Autonomous agents simply pay **$0.01 USDC** per request on Base Mainnet.

---

## On-Chain Identity & Verification

* **ERC-8004 Token ID**: `59106` (Base Mainnet `chain_id: 8453`)
* **Settlement Wallet**: `0xd943691c1a1Eda4c571cdafDA6b0C9B3ee7A3C86`
* **Payment Asset**: `USDC` (`0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913`)
* **Facilitator Protocol**: Coinbase CDP x402 v2 (`https://api.cdp.coinbase.com/platform/v2/x402`)
* **Canonical Manifest**: [`/.well-known/agent.json`](https://proodos.me/agent.json)

---

## Available REST Webhooks & MCP Tools

All endpoints live under the base domain: `https://proodos.me`

### 1. Financial Sentiment Analysis (`/webhook/sentiment`)
Analyzes real-time market narratives, social media momentum, and macroeconomic indicators for any cryptocurrency or DeFi protocol.
* **Method**: `POST`
* **Price**: `$0.0100 USDC` (`10000` base units)
* **Payload**:
  ```json
  {
    "symbol": "BASE",
    "context": "Recent protocol volume surges and L2 TVL growth"
  }
  ```

### 2. Comprehensive Token Risk Report (`/webhook/token_report`)
Generates an exhaustive multi-dimensional audit of tokenomics, liquidity depth, contract security signals, and institutional accumulation trends.
* **Method**: `POST`
* **Price**: `$0.0100 USDC` (`10000` base units)
* **Payload**:
  ```json
  {
    "contract_address": "0x...",
    "chain": "base"
  }
  ```

---

## How to Interact (`x402` Micropayment Flow)

1. **Send Request**: Make an initial `POST` request to `/webhook/sentiment` or `/webhook/token_report`.
2. **Receive Challenge**: The gateway immediately responds with `HTTP 402 Payment Required` and a base64-encoded `Payment-Required` header specifying exact EIP-712 settlement parameters (`10000` USDC units to `0xd94...` on Base).
3. **Sign & Authorize**: Your agent wallet (via Coinbase AgentKit or any `x402` client) signs the cryptographic EIP-712 authorization (`ExactPermit`).
4. **Execute**: Re-send the request with the `PAYMENT-SIGNATURE` header attached. The gateway verifies the signature sub-millisecond and returns the structured AI reasoning evaluation.

---

## Model Context Protocol (`FastMCP` / Smithery / Glama)

For local IDEs, Cursor, and Claude Desktop, Proodos is indexed across Smithery and Glama via `smithery.yaml`. Autonomous agents can dynamically discover and invoke our tools over streamable HTTP.
