# 👻 PhantomVault

**Decentralized P2P Lending Protocol with Quantitative Risk Engine**

A DeFi lending protocol where users can lend and borrow crypto assets against collateral, powered by dynamic interest rate models, real-time risk assessment, and automated liquidation — deployed on Ethereum testnet.

---

## 🧠 What is PhantomVault?

PhantomVault is a trustless, smart contract-based lending platform that eliminates the need for traditional financial intermediaries. Lenders deposit assets into liquidity pools to earn dynamic yields, while borrowers lock collateral to take out loans — all governed by on-chain logic and a quantitative risk engine running off-chain.

**Core thesis:** Interest rates, collateral thresholds, and liquidation penalties shouldn't be static — they should adapt to real-time market conditions using quantitative models.

---

## ✨ Features

### Protocol Layer (Smart Contracts)
- **Lending Pools** — Deposit assets into shared liquidity pools and earn variable APY
- **Collateralized Borrowing** — Lock collateral to borrow against it at algorithmically determined rates
- **Dynamic Interest Rates** — Utilization-based kinked rate model (inspired by Aave/Compound) that adjusts borrowing costs in real time
- **Auto-Liquidation** — Positions that breach the health factor threshold are automatically liquidated with an on-chain penalty mechanism
- **Multi-Asset Support** — Support for multiple ERC-20 tokens as collateral and borrowable assets

### Quantitative Risk Engine (Off-Chain)
- **Value-at-Risk (VaR)** — Calculates portfolio-level risk exposure for the protocol's collateral pool
- **Monte Carlo Simulations** — Stress-tests the protocol under extreme market scenarios (flash crashes, sustained drawdowns)
- **Volatility Tracking** — Real-time historical and implied volatility analysis for supported assets
- **Liquidation Threshold Optimizer** — Uses historical price data and volatility to recommend optimal collateral ratios
- **Health Factor Monitoring** — Continuously monitors all open positions and flags at-risk accounts

### Dashboard (Frontend)
- **Live Pool Metrics** — TVL, utilization rate, APY curves, and pool composition
- **Position Manager** — Deposit, borrow, repay, and withdraw with real-time health factor display
- **Risk Dashboard** — VaR heatmaps, Monte Carlo distribution charts, and volatility graphs
- **Liquidation Feed** — Real-time log of liquidation events with transaction details
- **Portfolio Analytics** — Track your lending/borrowing history, earnings, and interest paid

---

## 🏗️ Architecture

```
┌──────────────────────────────────────────────────────┐
│                    Frontend (React)                   │
│         Dashboard · Position Manager · Analytics      │
└──────────────────────┬───────────────────────────────┘
                       │
                       ▼
┌──────────────────────────────────────────────────────┐
│                Backend (Node.js / Python)             │
│     REST API · WebSocket Server · Price Feeds         │
│                                                       │
│  ┌─────────────────────────────────────────────────┐  │
│  │          Quantitative Risk Engine               │  │
│  │   VaR · Monte Carlo · Volatility · Optimizer    │  │
│  └─────────────────────────────────────────────────┘  │
│                                                       │
│  ┌─────────────────────────────────────────────────┐  │
│  │          Liquidation Bot                        │  │
│  │   Health Monitor · Auto-Liquidator · Alerts     │  │
│  └─────────────────────────────────────────────────┘  │
└──────────────────────┬───────────────────────────────┘
                       │
                       ▼
┌──────────────────────────────────────────────────────┐
│            Smart Contracts (Solidity)                 │
│    LendingPool · RateModel · Liquidator · Oracle     │
│                Ethereum Testnet (Sepolia)             │
└──────────────────────────────────────────────────────┘
```

---

## 🛠️ Tech Stack

| Layer            | Technology                                      |
|------------------|--------------------------------------------------|
| Smart Contracts  | Solidity, Hardhat, OpenZeppelin                  |
| Backend API      | Node.js (Express) / Python (FastAPI)             |
| Risk Engine      | Python (NumPy, SciPy, Pandas)                    |
| Price Feeds      | Chainlink Oracles / CoinGecko API                |
| Frontend         | React, Tailwind CSS, Recharts, ethers.js         |
| Database         | PostgreSQL (position history, analytics)          |
| Real-time        | WebSockets (Socket.io)                           |
| Testing          | Chai, Mocha, Pytest, Hardhat Network             |
| Deployment       | Sepolia Testnet, Vercel (frontend), Railway (API) |

---

## 📁 Project Structure

```
PhantomVault/
├── contracts/                # Solidity smart contracts
│   ├── LendingPool.sol
│   ├── InterestRateModel.sol
│   ├── Liquidator.sol
│   ├── PriceOracle.sol
│   └── mocks/               # Mock tokens for testing
├── scripts/                  # Deployment & interaction scripts
├── test/                     # Smart contract test suite
├── backend/
│   ├── api/                  # REST API routes
│   ├── services/             # Business logic
│   ├── risk-engine/          # Quantitative risk models
│   │   ├── var_model.py
│   │   ├── monte_carlo.py
│   │   ├── volatility.py
│   │   └── optimizer.py
│   ├── liquidation-bot/      # Health monitor & auto-liquidator
│   └── websocket/            # Real-time event broadcasting
├── frontend/
│   ├── src/
│   │   ├── components/       # UI components
│   │   ├── pages/            # Dashboard, Pool, Risk, Portfolio
│   │   ├── hooks/            # Custom React hooks
│   │   ├── contracts/        # ABI & contract addresses
│   │   └── utils/            # Helpers & formatters
│   └── public/
├── docs/                     # Architecture docs & math writeups
├── hardhat.config.js
├── package.json
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- Node.js >= 18
- Python >= 3.10
- MetaMask browser extension
- Sepolia testnet ETH ([faucet](https://sepoliafaucet.com))

### Installation

```bash
# Clone the repo
git clone https://github.com/yourusername/PhantomVault.git
cd PhantomVault

# Install smart contract dependencies
npm install

# Install backend dependencies
cd backend
pip install -r requirements.txt

# Install frontend dependencies
cd ../frontend
npm install
```

### Deploy Contracts

```bash
# Compile contracts
npx hardhat compile

# Deploy to Sepolia
npx hardhat run scripts/deploy.js --network sepolia
```

### Run the App

```bash
# Terminal 1 — Start backend
cd backend
python main.py

# Terminal 2 — Start frontend
cd frontend
npm run dev
```

---

## 📊 Quantitative Models

### Interest Rate Model
Uses a **kinked utilization curve** where rates increase gradually below optimal utilization and spike sharply above it — incentivizing liquidity equilibrium.

```
Rate = BaseRate + (Utilization / Optimal) × Slope1           if U ≤ Optimal
Rate = BaseRate + Slope1 + ((U - Optimal) / (1 - Optimal)) × Slope2   if U > Optimal
```

### Value-at-Risk (VaR)
Estimates the maximum expected loss on the collateral pool at a given confidence interval (95%/99%) over a specified time horizon using historical simulation.

### Monte Carlo Stress Testing
Runs N simulated price paths using geometric Brownian motion to model collateral value under extreme scenarios and determine protocol solvency thresholds.

### Liquidation Threshold Optimizer
Analyzes historical drawdown data and rolling volatility to recommend per-asset collateral ratios that minimize liquidation risk while maximizing capital efficiency.

---

## 🧪 Testing

```bash
# Smart contract tests
npx hardhat test

# Risk engine tests
cd backend
pytest risk-engine/tests/

# Frontend tests
cd frontend
npm run test
```

---

## 🗺️ Roadmap

- [x] Project architecture & smart contract design
- [ ] Core lending pool contract with deposit/withdraw
- [ ] Interest rate model implementation
- [ ] Collateral & borrowing logic
- [ ] Liquidation mechanism
- [ ] Price oracle integration (Chainlink)
- [ ] Off-chain risk engine (VaR, Monte Carlo)
- [ ] Liquidation bot with health monitoring
- [ ] Frontend dashboard with pool metrics
- [ ] Risk visualization dashboard
- [ ] Portfolio analytics & history
- [ ] Testnet deployment & end-to-end testing
- [ ] Documentation & math writeups

---

## 👥 Team

| Name | Role | Focus |
|------|------|-------|
| [Your Name] | Developer | Smart Contracts, Risk Engine |
| [Partner's Name] | Developer | Backend API, Frontend, Liquidation Bot |

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- [Aave Protocol](https://aave.com) — Interest rate model inspiration
- [Compound Finance](https://compound.finance) — Lending pool architecture reference
- [Chainlink](https://chain.link) — Decentralized price feeds
- [OpenZeppelin](https://openzeppelin.com) — Secure smart contract libraries

---

<p align="center">
  Built with 💀 by the PhantomVault team
</p>
