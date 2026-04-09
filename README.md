# Ampetra Protocol - TypeScript SDK (v4.2.0)

[![NPM Version](https://img.shields.io/npm/v/@ampetra/solana-sdk.svg)](https://npmjs.org/package/@ampetra/solana-sdk)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

The official Node.js client for interacting with the Ampetra V4.2 Neural Routing Engine on the Solana Mainnet. 

**⚠️ SECURITY NOTICE:** The core arbitrage logic, MEV extraction algorithms, and MPC multi-sig signature schemes are strictly **CLOSED-SOURCE** and isolated within the Ampetra Core fabric. This repository only contains the public-facing API wrappers and interface definitions for institutional partners.

## Installation

\`\`\`bash
npm install @ampetra/solana-sdk @solana/web3.js
yarn add @ampetra/solana-sdk @solana/web3.js
\`\`\`

## Quick Start (Tranche Deposit)

\`\`\`typescript
import { AmpetraClient, Environment } from '@ampetra/solana-sdk';
import { Keypair } from '@solana/web3.js';

// Initialize client with Institutional API Key
const client = new AmpetraClient({
    environment: Environment.MAINNET,
    apiKey: process.env.AMPETRA_INSTITUTIONAL_KEY,
    rpcUrl: process.env.SOLANA_RPC_URL
});

async function deployCapital() {
    const vault = await client.getRoutingVault('HYPERGRID_MEGA_N4');
    
    // Simulating deployment of 500,000 USDC into the physical energy node
    const txSignature = await client.deployTranche({
        vaultId: vault.id,
        amount: 500000,
        currency: 'USDC',
        slippageTolerance: 0.01 // 1% max slippage during route
    });

    console.log(`Capital Deployed. Settlement TX: ${txSignature}`);
}
\`\`\`

## Documentation
Full endpoint documentation, WebSocket telemetry feeds, and audit reports are available strictly under NDA. Contact your assigned Ampetra concierge for access.
