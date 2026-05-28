# Vertus Reverse Engineering Blueprint
*How to Build a Vertus-Like AI Trading System: A Technical Blueprint*

> **Disclaimer:** This is a technical analysis and educational blueprint. Trading involves substantial risk of loss. This document is for research and educational purposes only.

---

## Section 1: What We Know for Certain

### Verified Facts (from audited claims and public sources)

| Fact | Source | Confidence |
|------|---------|------------|
| 51.15% annual return, 2025 | Independently audited (Alpha Performance Verification Services) | HIGH |
| 2.13 Sharpe ratio, 2025 | Independently audited | HIGH |
| $600M+ average daily volume, $1B+ peak (Nov 25, 2025) | Independently audited | HIGH |
| Tested in Isle of Man FSA sandbox | Digital Isle of Man article | HIGH |
| Uses genetic algorithms explicitly | vertus.ai/investment | HIGH |
| Uses proprietary broker flow data | vertus.ai/investment | HIGH (claimed) |
| 1M+ subsystems processing simultaneously | vertus.ai | HIGH (claimed) |
| Started with founders' personal capital | Digital Isle of Man | HIGH |
| Co-founders: Julius Franck, Alex Foster, Michal Prywata | All sources | HIGH |
| Julius: quant finance master's, Germany copy trading platform | TechEchelon Q&A | HIGH |
| Michal: MIT background, Bionik Laboratories, Phantom Space | Multiple sources | HIGH |
| Alex: London Academy of Trading, Alexander William, Vanquish | TechEchelon Q&A | HIGH |
| Reached 7-figure ARR within 1 month of B2B launch | Digital Isle of Man | MEDIUM |
| Technology licensed to funds, family offices, asset managers | Multiple sources | HIGH |
| No GIPS compliance claimed | Not mentioned anywhere | HIGH |

### What We Don't Know
- Exact trading strategies employed
- Asset classes traded
- AUM (assets under management) — only volume disclosed
- Gross vs. net returns
- Maximum drawdown figures
- Leverage used
- Specific technology architecture
- Programming languages/frameworks
- Data vendors used
- Prime broker relationships
- Whether returns are from prop trading or client accounts

---

## Section 2: What We Can Infer

### Logical Deductions from Their Claims

**On Strategy:**
- *Inference 1:* Medium-frequency strategies (minutes to days), not HFT
  - *Reason:* "Machine reasoning" implies multi-step decisions that take >milliseconds. HFT is pure speed arbitrage.
  - *Reason:* Isle of Man sandbox testing doesn't support co-location HFT infrastructure.
  
- *Inference 2:* Primarily directional alpha, not pure market-making
  - *Reason:* B2B clients want returns, not bid-ask spread
  - *Reason:* "Cognitive systems that reason" implies directional view formation

- *Inference 3:* Equity-focused with likely futures/FX exposure
  - *Reason:* Broker money flow data most meaningful in equity markets
  - *Reason:* $600M+ daily volume consistent with equities or futures
  - *Reason:* Institutional client base (funds, family offices) primarily equity-focused

**On Architecture:**
- *Inference 4:* Large ensemble of many small models (the "1M subsystems")
  - *Reason:* 2.13 Sharpe requires diversification across uncorrelated signals
  - *Reason:* "1 million trading strategies processed daily" = ensemble voting system

- *Inference 5:* Reinforcement learning for live adaptation
  - *Reason:* "Consequential learning" and "real-time adaptation" match RL perfectly
  - *Reason:* Genetic algorithms used for evolution/selection of strategies

- *Inference 6:* Proprietary alternative data is their core moat
  - *Reason:* "Broker money flows invisible to public markets" is the key differentiator
  - *Reason:* Without proprietary data, their edge could be replicated

**On Business:**
- *Inference 7:* Prop trading profits are primary revenue, licensing is secondary
  - *Reason:* They started with personal capital; licensing came later
  - *Reason:* Returns are high enough that prop trading is the primary wealth generator

- *Inference 8:* The 51% return is from a relatively small capital base
  - *Reason:* Capacity constraints — high-Sharpe strategies typically have limited AUM capacity
  - *Reason:* No institutional AUM disclosure; $600M is likely notional volume, not managed capital

---

## Section 3: The Core Architecture

### System Diagram (Inferred)

```
┌─────────────────────────────────────────────────────────────┐
│                     DATA LAYER                              │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐   │
│  │ Market Data  │  │ Proprietary  │  │ Alternative Data │   │
│  │ (L1/L2/L3)   │  │ Broker Flows │  │ (News/Alt/Macro) │   │
│  └──────┬───────┘  └──────┬───────┘  └────────┬─────────┘   │
└─────────┼──────────────────┼──────────────────┼─────────────┘
          │                  │                  │
┌─────────▼──────────────────▼──────────────────▼────────────-─┐
│                   SIGNAL GENERATION LAYER                    │
│  ┌─────────────────────────────────────────────────────────┐ │
│  │            Ensemble of 1M+ Subsystems                   │ │
│  │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐    │ │
│  │  │ML Model 1│ │ML Model 2│ │ GA Pool  │ │ RL Agent │    │ │
│  │  │(Momentum)│ │(StatArb) │ │(Evolved) │ │(Adaptive)│    │ │
│  │  └──────────┘ └──────────┘ └──────────┘ └──────────┘    │ │
│  │           ... × 999,996 more subsystems ...             │ │
│  └─────────────────────┬───────────────────────────────────┘ │
│                         │                                    │
│  ┌─────────────────────▼───────────────────────────────────┐ │
│  │          Signal Aggregation / Meta-Learning             │ │
│  │      (Ensemble weighting, confidence scoring,           │ │
│  │       mathematical validation, conflict resolution)     │ │
│  └─────────────────────┬───────────────────────────────────┘ │
└────────────────────────┼─────────────────────────────────────┘
                         │
┌────────────────────────▼─────────────────────────────────────┐
│                  RISK MANAGEMENT LAYER                       │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐    │
│  │ Position     │  │  Portfolio   │  │   Real-time      │    │
│  │ Sizing (Kelly│  │  Risk Limits │  │   VaR / CVaR     │    │
│  │ / Vol Target)│  │  (Drawdown)  │  │   Monitoring     │    │
│  └──────┬───────┘  └──────┬───────┘  └────────┬─────────┘    │
└─────────┼──────────────────┼──────────────────┼─────────────-┘
          │                  │                  │
┌─────────▼──────────────────▼──────────────────▼─────────────┐
│                     EXECUTION LAYER                         │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐   │
│  │ Order Gen    │  │ Smart Order  │  │  Execution       │   │
│  │ (Signal→     │  │ Routing      │  │  Monitoring      │   │
│  │  Order)      │  │ (Best Fill)  │  │  (Slippage)      │   │
│  └──────┬───────┘  └──────┬───────┘  └────────┬─────────┘   │
└─────────┼──────────────────┼──────────────────┼─────────────┘
          │                  │                  │
         MARKET (exchanges, dark pools, broker internalization)
                         │
┌────────────────────────▼─────────────────────────────────────┐
│                    LEARNING LOOP                             │
│  Trade Results → P&L Attribution → Model Update              │
│  (Which signals worked? Retrain, evolve, reweight)           │
└──────────────────────────────────────────────────────────────┘
```

### Component Deep Dives

#### A. Data Layer
**Market Data (Level 1, 2, 3):**
- L1: Best bid/ask + last trade (real-time)
- L2: Full order book (10–20 levels deep)
- L3: Individual order flow (requires exchange membership or prime broker access)
- Sources: Bloomberg, Refinitiv, direct exchange feeds

**Proprietary Broker Flow Data:**
This is Vertus's stated moat. How it works:
- Prime brokers aggregate orders from many clients
- They sell "flow analytics" — not individual client data, but aggregated patterns
- "Buy-side flow" data shows which sectors/stocks institutions are accumulating/distributing
- This is legal (it's not front-running) but expensive and relationship-dependent
- Key vendors: Citi Velocity, Morgan Stanley Matrix, Goldman Sachs GSIS, ITG (now Virtu)

**Alternative Data:**
- News sentiment (RavenPack, Bloomberg News Analytics)
- Earnings call transcripts (NLP analysis)
- Satellite imagery (supply chain intelligence)
- Credit card transaction data (consumer spending)
- Web scraping (job postings, pricing data)
- Social media sentiment (Twitter/X, Reddit finance communities)

#### B. Signal Generation Layer
The "1M+ subsystems" is almost certainly an **ensemble of micro-strategies**, each generating weak signals that combine into strong aggregate signals.

Each micro-strategy might be:
- A simple moving average crossover on a specific ticker/timeframe
- A mean-reversion signal triggered by z-score thresholds
- A sector rotation signal based on relative momentum
- A volatility breakout signal
- An order flow imbalance signal

The ensemble aggregation uses genetic algorithms to evolve which strategies get more weight, dropping underperformers and promoting outperformers over time.

**The "Dynamic Neural Topology"** is likely:
- **Mixture of Experts (MoE):** Different sub-networks for different market regimes (trending, mean-reverting, volatile, calm)
- **Or: Hypernetworks** — a meta-network that generates weights for the main network based on current market state
- **Or: Neural Architecture Search (NAS)** — the architecture itself evolves

#### C. Execution Layer
For $600M average daily volume:
- **Algorithmic execution:** VWAP, TWAP, Implementation Shortfall algorithms
- **Smart Order Routing:** Automatic routing to best-priced liquidity across venues
- **Liquidity sourcing:** Dark pools (reduce market impact), lit exchanges (price discovery)
- **Transaction cost analysis (TCA):** Continuous monitoring of slippage vs. theoretical

---

## Section 4: Technology Stack to Replicate

### Programming Languages
| Component | Language | Why |
|-----------|----------|-----|
| Signal generation / ML | **Python** | NumPy, pandas, scikit-learn, PyTorch, TensorFlow ecosystem |
| High-performance execution | **C++** | Microsecond-level order management, FIX protocol |
| Database queries | **SQL + Python** | TimescaleDB, InfluxDB, ClickHouse for time-series |
| Infrastructure / DevOps | **Bash / Terraform** | Automation, cloud deployment |
| Research / backtesting | **Python + Jupyter** | Vectorbt, Backtrader, QuantLib |
| Real-time data processing | **Python (asyncio) or Rust** | Kafka consumers, streaming data |

### Frameworks and Libraries (Core Stack)

**Machine Learning:**
```python
# Core ML
torch              # PyTorch for deep learning
tensorflow         # Alternative deep learning
scikit-learn       # Classical ML, ensemble methods
xgboost            # Gradient boosting (excellent for tabular financial data)
lightgbm           # Faster gradient boosting
catboost           # Handles categorical features

# Genetic Algorithms / Evolutionary Optimization
deap               # Distributed Evolutionary Algorithms in Python
pygad              # PyGAD genetic algorithm library
optuna             # Hyperparameter optimization (can use evolutionary search)

# Reinforcement Learning
stable-baselines3  # RL algorithms (PPO, SAC, TD3)
gymnasium          # RL environment framework
ray[rllib]         # Distributed RL

# Specialized Financial ML
alphalens          # Factor analysis (Quantopian/FactSet)
pyfolio            # Portfolio and risk analytics
zipline            # Backtesting (Quantopian's open-source)
vectorbt           # Fast backtesting with vectorized operations
```

**Data Processing:**
```python
pandas             # Data manipulation
polars             # Faster pandas alternative (Rust-based)
numpy              # Numerical computing
dask               # Parallel computing for large datasets
kafka-python       # Real-time data streaming
redis              # Low-latency in-memory data store
```

**Time-Series Databases:**
- **TimescaleDB** (PostgreSQL extension, excellent for market data)
- **InfluxDB** (purpose-built time-series, open source)
- **ClickHouse** (columnar, fast analytical queries, used by Yandex/Cloudflare)
- **kdb+/q** (industry standard at quant funds, but expensive)

**Execution:**
```
FIX Protocol       # Standard financial messaging (every broker supports it)
Interactive Brokers TWS API  # Best for initial development
Alpaca             # Commission-free equities API (US)
IBKR Pro           # Full institutional access
QuickFIX/J         # Java FIX implementation (most production use)
```

### Infrastructure Requirements

**Minimum Viable Version (MVP):**
- A $5K–$20K/month budget
- 1–3 engineers
- Cloud (AWS/GCP): $500–$2K/month
- Market data (Polygon.io basic): $200/month
- Broker API (IBKR): $10/month + commissions
- 1 server for backtesting, 1 for live trading

**Full Scale (Vertus-Like):**
- $50K–$250K/month operating costs
- 10–30 engineers (quant, software, data science)
- Co-location at exchange data centers
- Bloomberg Terminal(s): $24K/year each
- Level 2 data feeds: $1K–$20K/month
- Prime broker relationship (min $5M–$10M capital typically required)
- Proprietary data agreements: $100K–$500K/year

### Data Sources by Priority

**Free / Low-Cost (MVP Phase):**
- **Polygon.io** — US equities, options, forex, crypto; $29–$200/month
- **Alpha Vantage** — Free tier; stock data, fundamentals
- **Yahoo Finance / yfinance** — Historical data, free
- **Quandl/Nasdaq Data Link** — Economic data, some equity data
- **SEC EDGAR** — Filings, fundamentals, 13F institutional holdings (free)

**Professional (Production):**
- **Refinitiv Eikon / LSEG** — Professional financial data
- **Bloomberg B-PIPE** — Institutional-grade real-time data
- **FactSet** — Fundamentals, estimates, ownership data
- **S&P Global Market Intelligence** — Credit, fundamentals

**Alternative Data (Vertus's Claimed Edge):**
- **RavenPack** — News sentiment and event data ($thousands/month)
- **Quandl/NASDAQ Data Link Alt Data** — Various datasets
- **Earnest Research** — Credit card transaction data
- **Orbital Insight / Planet Labs** — Satellite imagery

---

## Section 5: Key Trading Strategies to Implement

### Strategy 1: ML-Enhanced Cross-Sectional Momentum (Start Here)
**What:** Predict which stocks will outperform next week/month based on past returns + ML features  
**Why Start Here:** Well-researched, works across markets, adaptable to ML enhancement  
**Expected Sharpe (pure momentum):** 0.5–0.8; with ML enhancement: 0.8–1.5

```python
# Simplified implementation sketch
import pandas as pd
import numpy as np
from sklearn.ensemble import GradientBoostingClassifier

# Features: returns over multiple lookback periods + volume + volatility
def build_features(price_data, volume_data):
    features = pd.DataFrame()
    for period in [5, 10, 21, 63, 126]:  # 1w, 2w, 1m, 3m, 6m
        features[f'return_{period}d'] = price_data.pct_change(period)
    features['volatility_21d'] = price_data.pct_change().rolling(21).std()
    features['volume_ratio'] = volume_data / volume_data.rolling(21).mean()
    return features

# Target: whether stock is in top quintile next month
def build_target(price_data, forward_period=21):
    forward_returns = price_data.pct_change(forward_period).shift(-forward_period)
    return (forward_returns > forward_returns.quantile(0.8)).astype(int)

# Train ensemble
model = GradientBoostingClassifier(n_estimators=500, max_depth=3)
model.fit(X_train, y_train)

# Portfolio: long top decile, short bottom decile (if allowed)
signals = model.predict_proba(X_test)[:, 1]
weights = signals / signals.sum()  # Long-only version
```

**Enhancement for Vertus-style:** Add genetic algorithm to evolve feature selection and hyperparameters. Add broker flow data as additional features.

---

### Strategy 2: Statistical Arbitrage with Order Flow Features
**What:** Identify equity pairs with temporary mispricings; trade the spread  
**Why:** Order flow data (institutional positioning) gives edge on when spreads will close  
**Expected Sharpe:** 1.5–2.5 (depends heavily on data quality)

```python
import statsmodels.api as sm
from statsmodels.tsa.stattools import coint

# Find cointegrated pairs
def find_cointegrated_pairs(returns_df, pvalue_threshold=0.05):
    pairs = []
    tickers = returns_df.columns
    for i, t1 in enumerate(tickers):
        for t2 in tickers[i+1:]:
            score, pvalue, _ = coint(returns_df[t1], returns_df[t2])
            if pvalue < pvalue_threshold:
                pairs.append((t1, t2, pvalue))
    return sorted(pairs, key=lambda x: x[2])

# Signal: z-score of spread
def calc_spread_zscore(prices_a, prices_b, lookback=60):
    spread = prices_a - prices_b  # After hedge ratio adjustment
    zscore = (spread - spread.rolling(lookback).mean()) / spread.rolling(lookback).std()
    return zscore

# Trade when z-score is extreme
entry_threshold = 2.0
exit_threshold = 0.5
```

**Order flow enhancement:** If institutional flow data shows persistent buying in stock A (suggesting a large accumulation program), that's a signal that the spread will close in A's favor. This is Vertus's likely edge.

---

### Strategy 3: Ensemble Genetic Algorithm Factory (Vertus-Like "1M Strategies")
**What:** Automated generation and selection of many micro-strategies via genetic algorithms  
**Why:** Scales to many weak signals; ensemble reduces variance (higher Sharpe)  
**Expected Sharpe:** 1.0–2.5 (depends on quality of gene pool)

```python
from deap import algorithms, base, creator, tools
import random

# Define a simple strategy gene: parameters for a moving average crossover
# Each "gene" = [fast_period, slow_period, position_size, stop_loss_pct]
def evaluate_strategy(individual, price_data):
    fast, slow, pos_size, stop = individual
    fast = max(2, int(fast))
    slow = max(fast+1, int(slow))
    
    signals = price_data.rolling(fast).mean() > price_data.rolling(slow).mean()
    returns = (signals.shift(1) * price_data.pct_change()).dropna()
    
    if returns.std() == 0:
        return (-999,)
    
    sharpe = (returns.mean() / returns.std()) * np.sqrt(252)
    return (sharpe,)

# Setup DEAP genetic algorithm
creator.create("FitnessMax", base.Fitness, weights=(1.0,))
creator.create("Individual", list, fitness=creator.FitnessMax)

toolbox = base.Toolbox()
toolbox.register("attr_float", random.uniform, 2, 200)
toolbox.register("individual", tools.initRepeat, creator.Individual, 
                 toolbox.attr_float, n=4)
toolbox.register("population", tools.initRepeat, list, toolbox.individual)
toolbox.register("evaluate", evaluate_strategy, price_data=your_price_data)
toolbox.register("mate", tools.cxBlend, alpha=0.5)
toolbox.register("mutate", tools.mutGaussian, mu=0, sigma=20, indpb=0.2)
toolbox.register("select", tools.selTournament, tournsize=3)

# Run evolution: creates and selects strategies
population = toolbox.population(n=10000)  # Start with 10K strategies
algorithms.eaSimple(population, toolbox, cxpb=0.5, mutpb=0.2, 
                    ngen=100, verbose=True)
```

**At scale (Vertus-style):**
- Run this on thousands of tickers, multiple timeframes, multiple indicator types
- Parallel GPU processing for fast evaluation
- Keep top 1% of strategies (surviving = "1M subsystems" = ensemble of best micro-strats)
- Combine signals using weighted voting based on recent Sharpe performance

---

### Strategy 4: Reinforcement Learning Execution Agent
**What:** RL agent learns optimal execution (not prediction, but when/how to execute)  
**Why:** Dramatically reduces slippage; improves effective return by 0.5–2%/year  
**Expected improvement:** +0.5–2% annualized (compounding over many trades)

```python
import gymnasium as gym
from stable_baselines3 import PPO
from stable_baselines3.common.env_util import make_vec_env

class ExecutionEnv(gym.Env):
    """RL environment for optimal order execution"""
    
    def __init__(self, target_quantity, price_data, timeframe_minutes=30):
        super().__init__()
        self.target = target_quantity  # Total shares to buy/sell
        self.remaining = target_quantity
        self.price_data = price_data
        self.timeframe = timeframe_minutes
        
        # Action: proportion of remaining to execute now (0 to 1)
        self.action_space = gym.spaces.Box(low=0, high=1, shape=(1,))
        
        # State: remaining quantity, time elapsed, current price, bid-ask spread, volume
        self.observation_space = gym.spaces.Box(
            low=-np.inf, high=np.inf, shape=(5,), dtype=np.float32
        )
    
    def step(self, action):
        qty_to_execute = self.remaining * action[0]
        # Calculate execution cost (market impact model)
        slippage = self._estimate_slippage(qty_to_execute)
        reward = -slippage  # Minimize execution cost
        self.remaining -= qty_to_execute
        done = self.remaining <= 0 or self.time_elapsed >= self.timeframe
        return self._get_obs(), reward, done, False, {}
    
    def _estimate_slippage(self, qty):
        # Square-root market impact model (standard in practice)
        return qty ** 0.5 * self.current_spread
```

---

## Section 6: Risk Management Framework

### Achieving a 2.13 Sharpe — The Framework

Sharpe = (Mean Return - Risk Free Rate) / Standard Deviation of Returns

To get Sharpe of 2.13 with 51% gross return:
- Annualized daily standard deviation ≈ 24% (using 51%/2.13 ≈ 24%)
- Daily volatility ≈ 24%/√252 ≈ 1.5% per day
- This implies relatively low daily volatility despite high annual returns

**How to achieve this:**

**1. Volatility Targeting**
```python
def vol_target_position_size(signal, target_vol=0.15, realized_vol=None, 
                              max_leverage=2.0):
    """Scale positions so portfolio annualized vol = target_vol"""
    if realized_vol is None:
        realized_vol = calculate_ewm_vol(returns, halflife=21)
    
    vol_scalar = target_vol / (realized_vol * np.sqrt(252))
    vol_scalar = min(vol_scalar, max_leverage)
    return signal * vol_scalar
```

**2. Kelly Criterion (Fractional)**
```python
def kelly_position_size(win_rate, avg_win, avg_loss, kelly_fraction=0.25):
    """Conservative fractional Kelly sizing"""
    b = avg_win / avg_loss  # Win/loss ratio
    p = win_rate
    q = 1 - win_rate
    
    full_kelly = (b * p - q) / b  # Kelly formula
    fractional_kelly = full_kelly * kelly_fraction  # Use 25% of Kelly (conservative)
    
    return max(0, min(fractional_kelly, 0.10))  # Cap at 10% per position
```

**3. Portfolio Risk Limits**
```python
RISK_LIMITS = {
    'max_single_position': 0.05,      # 5% max in any one stock
    'max_sector_exposure': 0.25,       # 25% max in any one sector
    'max_daily_drawdown': 0.02,        # 2% daily loss = reduce risk
    'max_drawdown_from_peak': 0.10,    # 10% drawdown = go to cash
    'max_leverage': 2.0,               # 2x max gross leverage
    'max_correlation_threshold': 0.7,  # Avoid positions >70% correlated
    'volatility_target': 0.15,         # Target 15% annualized portfolio vol
}
```

**4. Drawdown Controls**
```python
class DrawdownController:
    def __init__(self, max_dd=0.10, warning_dd=0.05):
        self.peak_value = 0
        self.max_dd = max_dd
        self.warning_dd = warning_dd
        self.risk_multiplier = 1.0
    
    def update(self, portfolio_value):
        self.peak_value = max(self.peak_value, portfolio_value)
        current_dd = (self.peak_value - portfolio_value) / self.peak_value
        
        if current_dd > self.max_dd:
            self.risk_multiplier = 0.0  # Full stop: go to cash
        elif current_dd > self.warning_dd:
            # Linear reduction: scale down risk
            self.risk_multiplier = 1 - (current_dd - self.warning_dd) / \
                                   (self.max_dd - self.warning_dd)
        else:
            self.risk_multiplier = 1.0
        
        return self.risk_multiplier
```

**5. VaR and CVaR Targets**
```python
import numpy as np
from scipy import stats

def calculate_var_cvar(returns, confidence=0.95, holding_period=1):
    """Historical VaR and CVaR"""
    var = -np.percentile(returns, (1-confidence)*100)
    
    # CVaR (Expected Shortfall): average loss beyond VaR
    cvar = -returns[returns < -var].mean()
    
    return var, cvar

# Target: 1-day 95% VaR should not exceed 2% of portfolio
# If it does, reduce positions until within limit
def check_and_adjust_for_var(positions, returns_matrix, var_limit=0.02):
    portfolio_returns = (positions * returns_matrix).sum(axis=1)
    var, cvar = calculate_var_cvar(portfolio_returns)
    
    if var > var_limit:
        scale_factor = var_limit / var
        return positions * scale_factor  # Scale down all positions
    return positions
```

---

## Section 7: Operational Requirements

### Capital Requirements

**Phase 1: Research & Development (0–6 months)**
- Initial capital: **$50K–$200K** (personal capital sufficient)
- Paper trading: $0 additional
- Infrastructure: $1K–$5K/month
- Data: $200–$2K/month
- Primary cost: time and computing

**Phase 2: Small Live (6–18 months)**
- Live capital: **$100K–$1M** (enough to prove the strategy works live)
- IBKR Pro account: $100K minimum recommended
- Monthly costs: $5K–$20K
- Regulatory: US persons need RIA registration >$100M AUM; below that, state-registered or exempt

**Phase 3: Institutional Scale (18–36 months)**
- Capital: **$5M–$50M** (prime brokerage relationships typically require $5M+)
- Monthly costs: $50K–$250K
- Team: 5–15 people
- Regulatory: Depends on jurisdiction; Isle of Man FSA sandbox is an excellent starting point

**Phase 4: Vertus-Like Scale ($600M+ daily volume)**
- AUM: Likely **$20M–$200M** (achieving $600M daily with 3–30x daily turnover)
- Monthly costs: $100K–$500K
- Team: 15–30+ people
- Prime broker: Full institutional relationship (GS, MS, Citi, IBKR Prime)

### Team Composition (Priority Order)

| Role | Skills Needed | Timing |
|------|---------------|--------|
| **Quantitative Researcher** | Statistics, finance theory, Python, backtesting | Day 1 |
| **Software Engineer (Back-end)** | Python, C++, databases, APIs | Day 1 |
| **Data Engineer** | Data pipelines, cloud infrastructure, databases | Month 3 |
| **ML/AI Engineer** | PyTorch, sklearn, model deployment | Month 3 |
| **Execution/Infra Engineer** | FIX protocol, C++, latency optimization | Month 6 |
| **Risk Manager** | VaR, CVaR, portfolio theory, compliance | Month 6 |
| **Business Development** | Institutional sales, client management | Month 12 |
| **Compliance/Legal** | Financial regulation, fund setup | Month 12 |

### Regulatory Path (Recommended)

**Option A: Isle of Man (Vertus Model)**
1. Contact Digital Isle of Man and IoM FSA
2. Apply for Innovation Hub / Observatory Pathway
3. Develop and test under sandbox conditions
4. Graduate to full licensing as strategy is proven
5. Cost: Low; timelines: 6–18 months to full authorization

**Option B: Cayman Islands / BVI (Classic Hedge Fund)**
1. Form Cayman exempted limited partnership (fund vehicle)
2. Appoint regulated AIFM (easy in Cayman)
3. Open prime brokerage account
4. Minimal regulation for non-US investors
5. Cost: $50K–$100K setup; $30K–$50K/year maintenance

**Option C: UK (FCA)**
1. Register as Alternative Investment Fund Manager
2. More costly ($100K+ setup) but gives EU/UK credibility
3. FCA's Innovation Pathways available for novel approaches

---

## Section 8: 90-Day Build Plan

### Month 1: Foundation

**Week 1–2: Data Infrastructure**
```
□ Set up PostgreSQL + TimescaleDB instance (AWS RDS or local)
□ Subscribe to Polygon.io (equities L1 data, $29/month to start)
□ Build data ingestion pipeline: market data → database
□ Download 5 years historical data for S&P 500 universe (500 stocks)
□ Build data quality checks (missing data, outliers, splits, dividends)
□ Set up Jupyter Lab environment + git repository
```

**Week 3: Backtesting Framework**
```
□ Install vectorbt or write simple event-driven backtester
□ Build: data loader, signal calculator, portfolio constructor, P&L calculator
□ Implement: realistic transaction costs (commission + slippage model)
□ Critical: avoid lookahead bias (future data leaking into past decisions)
□ Validate backtest: check against known factor returns (Fama-French)
```

**Week 4: First Strategy + Baseline**
```
□ Implement simple cross-sectional momentum (1-month returns → next-month)
□ Backtest 2019–2023 (out-of-sample: 2024)
□ Target: Sharpe > 0.5 in-sample, > 0.3 out-of-sample
□ Add transaction cost sensitivity analysis
□ Build performance reporting: returns, Sharpe, drawdown, turnover
```

**Deliverable:** Working backtesting system + 1 baseline strategy. Understand what "realistic" backtest performance looks like before adding ML.

---

### Month 2: ML/AI Layer

**Week 5–6: Feature Engineering**
```
□ Expand features: 
  - Return-based: 5d, 10d, 21d, 63d, 126d, 252d returns
  - Volatility: realized vol, vol ratio, vol skew
  - Volume: turnover, dollar volume, volume trend
  - Fundamental (if using): P/E, P/B, ROE, momentum of earnings
  - Technical: RSI, MACD, Bollinger Bands, ATR
□ Build feature matrix: (stocks × days) × features
□ Handle survivorship bias: include delisted stocks in training data
□ Build walk-forward validation framework (no future data in model training)
```

**Week 7: ML Models**
```
□ Train gradient boosting (XGBoost/LightGBM) on cross-sectional features
□ Train LSTM on individual time-series for momentum/mean-reversion
□ Compare: which model adds most alpha over baseline?
□ Implement genetic algorithm for feature selection (use DEAP library)
□ Build: 100 random strategy variants; keep top 20 by Sharpe
□ Combine top strategies: equal-weight ensemble
□ Target: Ensemble Sharpe > 1.0 in out-of-sample
```

**Week 8: Alternative Data + Enhanced Signals**
```
□ Add free alternative data:
  - SEC 13F filings (institutional ownership changes → signals)
  - Short interest data (high short interest + momentum = squeeze signal)
  - Insider buying data (SEC Form 4 filings)
  - Earnings surprise data (EPS surprise → post-earnings drift)
□ Test each data source: does it add alpha independently?
□ Build meta-model: which data sources work in which market regimes?
□ Target: Sharpe > 1.3 with alt data
```

**Deliverable:** ML-enhanced strategy with Sharpe > 1.0 in out-of-sample. Clear understanding of what drives the alpha.

---

### Month 3: Live Deployment

**Week 9: Paper Trading Setup**
```
□ Open Interactive Brokers paper trading account (free)
□ Connect Python → IBKR API (ibkr_api or ib_insync library)
□ Deploy strategy to paper trading environment
□ Compare paper trading vs backtest: identify execution issues
□ Build: order management, position tracking, real-time P&L monitoring
□ Set up: kill switch (auto-stop if daily loss > 2%)
```

**Week 10: Risk System + Monitoring**
```
□ Implement all risk limits (see Section 6)
□ Build real-time dashboard:
  - Current positions and weights
  - Daily/weekly/monthly P&L
  - Sharpe ratio (rolling 30-day, 90-day)
  - Drawdown chart
  - VaR and CVaR
  - Signal confidence levels
□ Set up alerts: Telegram/email for:
  - Drawdown > 2% daily
  - Strategy signal anomalies
  - System errors
□ Run paper trading for minimum 4 weeks
```

**Week 11: Small Live Capital**
```
□ Fund live account: start with $10K–$50K personal capital
□ Execute SAME strategy as paper trading (no changes)
□ Trade at 10% of paper trading position sizes initially
□ Monitor: is live performance close to paper? (slippage, fills)
□ Key metric: is the live/paper return correlation > 0.9?
□ If yes: good. If no: execution issues to fix first.
```

**Week 12: Scale and Iterate**
```
□ If live performance validates paper trading → increase position sizes 2x
□ Add second strategy from Month 2 ensemble
□ Begin building proprietary data relationships (if targeting Vertus scale)
□ Document everything: what works, what doesn't, why
□ Prepare: investor pitch deck if planning to raise capital
□ Set 90-day performance review: have we achieved Sharpe > 1.5 live?
```

**Deliverable:** Live trading system with real capital, working risk management, Sharpe > 1.0 over first 90 days of live trading.

---

## Section 9: Tools & Resources

### Open Source Libraries
```
# Backtesting
vectorbt            # Fastest vectorized backtesting
backtrader          # Event-driven, more realistic
zipline             # Quantopian's open-source (legacy but comprehensive)
nautilus_trader     # Professional-grade, C++/Python hybrid

# Portfolio Optimization
PyPortfolioOpt      # Black-Litterman, mean-variance, risk parity
riskfolio-lib       # Advanced portfolio optimization
cvxpy               # Convex optimization (for custom constraints)

# Factor Analysis  
alphalens           # Alpha factor research and analysis
pyfolio             # Risk/performance analytics (from Quantopian)

# Statistics / Econometrics
statsmodels         # Econometric models, cointegration tests
scipy               # Scientific computing
arch                # GARCH models for volatility

# Alternative Data
yfinance            # Free Yahoo Finance data
alpha_vantage       # Free API for stocks, forex, crypto
quandl              # Economic data (some free)
pandas-datareader   # Multiple data sources

# Infrastructure
redis               # In-memory data store for real-time data
kafka-python        # Message streaming (Apache Kafka)
fastapi             # API framework for strategy deployment
celery              # Task queue for async processing
```

### Data Vendors (By Budget)

**$0–$500/month (Bootstrap Phase):**
- Polygon.io — US equities, options, forex, crypto
- Alpha Vantage — Free tier + premium
- SEC EDGAR — Free regulatory filings
- Yahoo Finance (via yfinance) — Historical data
- FRED (Federal Reserve Economic Data) — Macro data

**$500–$5K/month (Early Stage):**
- Norgate Data — US/Australian equities, survivorship-bias free
- Tiingo — End-of-day US equities + news sentiment
- FirstRate Data — Minute-level historical data
- Intrinio — Fundamentals + alternative data

**$5K–$50K/month (Growth Stage):**
- Bloomberg B-PIPE / Open Symbology
- Refinitiv Tick History
- RavenPack (news analytics)
- S&P Global Market Intelligence
- FactSet Research

**Proprietary Data (Vertus-Level Edge):**
- Prime broker flow analytics (requires >$5M AUM and prime brokerage relationship)
- Bank TCA data (Transaction Cost Analysis from executing brokers)
- Dark pool statistics (requires institutional relationships)

### Broker APIs

| Broker | Min Balance | API Quality | Commission | Best For |
|--------|-------------|-------------|------------|----------|
| **Interactive Brokers** | $0 (paper), $2K (live) | Excellent | Low | Best overall; institutional-grade |
| **Alpaca** | $0 | Good | Commission-free | US equities, beginner |
| **TD Ameritrade** (Schwab) | $0 | Good | $0 commissions | Options + equities |
| **Tradier** | $0 | Good | Low | Options heavy |
| **QuantConnect** | $0 | Excellent | N/A (research platform) | Strategy development |

### Research Papers to Study (Priority Order)

**Foundations:**
1. Fama & French — "Common Risk Factors in Returns on Stocks and Bonds" (1993) — *Factor investing foundation*
2. Jegadeesh & Titman — "Returns to Buying Winners and Selling Losers" (1993) — *Momentum effect*
3. Asness, Moskowitz, Pedersen — "Value and Momentum Everywhere" (2013) — *Cross-asset momentum*

**Machine Learning in Finance:**
4. Gu, Kelly, Xiu — "Empirical Asset Pricing via Machine Learning" (2020) — *Best ML finance paper*
5. Lopez de Prado — "Advances in Financial Machine Learning" (book, 2018) — *Essential reference*
6. Rasekhschaffe & Jones — "Machine Learning for Stock Selection" (2019)

**Execution and Market Microstructure:**
7. Almgren & Chriss — "Optimal Execution of Portfolio Transactions" (2000) — *Execution algorithm foundations*
8. Glosten & Milgrom — "Bid, Ask, and Transaction Prices" (1985) — *Order flow toxicity*

**Genetic Algorithms / Evolutionary Methods:**
9. Holland — "Adaptation in Natural and Artificial Systems" (book) — *GA foundations*
10. Genetic Algorithms in Finance (multiple papers on SSRN)

**Reinforcement Learning:**
11. Mnih et al. — "Human-level control through deep reinforcement learning" (DQN, 2015)
12. Schulman et al. — "Proximal Policy Optimization Algorithms" (PPO, 2017)
13. Hambly et al. — "Recent Advances in Reinforcement Learning in Finance" (2023)

---

## Section 10: Critical Success Factors

### What Separates the 51% Returners from the 5% Ones

**1. Data Edge Is Everything**
The single most important factor. Vertus's claimed moat — proprietary broker flow data — is the kind of data that creates sustainable alpha. Strategies built on public data get arbitraged away quickly. 

*Actionable:* Spend 50% of your budget on data. Especially: institutional ownership changes (free via SEC 13F), insider transactions (free via SEC Form 4), earnings surprise databases, and eventually broker flow data.

**2. Ensemble Over Single Model**
No single strategy produces 2+ Sharpe over time. The path to high Sharpe is diversification of signals. 100 strategies with Sharpe 0.5 each, if uncorrelated, combine to Sharpe ~5. The correlation is never zero in practice, so the actual combined Sharpe is lower — but the principle holds.

*Actionable:* Never trade a single strategy. Build a factory of strategies and combine them. Genetic algorithms are excellent for this.

**3. Treat Drawdown as a Hard Stop, Not a Guideline**
The most common way funds blow up: ignoring drawdown limits because "the strategy will come back." It might. Or it might not. Renaissance's Medallion Fund has strict risk controls even at 66% gross returns.

*Actionable:* Build automatic position scaling: at 5% drawdown from peak, reduce all positions by 50%. At 10%, go to cash entirely. No exceptions, no overrides.

**4. Walk-Forward Validation, Not Backtesting**
Anyone can curve-fit a backtest to look great. Walk-forward testing (training on past data, testing on truly unseen future data, period by period) is the only honest test.

*Actionable:* Never optimize parameters on the same period you're testing. Always use at minimum 3:1 in-sample:out-of-sample split. Test on 2022 (bear market) specifically — that's where most strategies fail.

**5. Execution Quality Matters as Much as Signal Quality**
A strategy with Sharpe 2.0 in backtest can become Sharpe 0.5 live due to poor execution. Transaction costs, slippage, and market impact are the great equalizers.

*Actionable:* Use IBKR's smart order routing. Implement VWAP execution for larger orders. Measure actual vs. theoretical execution prices daily. Optimize continuously.

**6. The Environment Trains the Intelligence**
Vertus's key insight: training AI in an environment where errors cost real money creates more robust systems than backtesting. Live trading — even with small capital — produces better intelligence than any simulation.

*Actionable:* Go live early with small capital. Don't wait until you have "the perfect strategy." A $5K live account teaches you more in one month than a year of backtesting. Start with 0.1% of your target allocation sizes.

**7. Regime Awareness**
2025 was a good year for equities. Strategies that work in bull markets often fail catastrophically in bear markets or volatility spikes. The best strategies (and best Sharpe ratios) work across regimes.

*Actionable:* Build a regime detector (using volatility, cross-asset correlations, macro signals). Have different strategy weights for different regimes. Test specifically on 2018, 2020 (March), 2022 — the hard years.

**8. Compounding Requires Not Blowing Up**
Buffett's first rule: "Never lose money." The second rule: "Never forget rule #1." A 50% drawdown requires a 100% gain to recover. Preserving capital during bad periods allows compounding during good periods to create extraordinary long-term returns.

*Actionable:* Optimize for Sharpe (risk-adjusted return), not absolute return. A Sharpe 2.0 strategy with 25% return compounded over 10 years beats a 50% return strategy that occasionally blows up.

**9. The Technology Moat Must Be Defended Continuously**
Quant edges decay. What worked in 2020 may not work in 2025. Markets adapt. Other quant funds copy strategies. The edge must be continuously replenished with new signals, new data sources, and new models.

*Actionable:* Allocate 30% of your research capacity to discovering new signals, not optimizing existing ones. Build a culture of continuous research.

**10. Know the Difference Between Alpha and Beta**
51% returns in a year when the market went up 17% could be: (a) 34% of genuine alpha, or (b) high-beta strategy that got lucky. The Sharpe ratio helps distinguish these. A Sharpe of 2.13 with 51% return implies ~24% annualized volatility — consistent with moderate leverage on market beta, OR genuine alpha with lower leverage.

*Actionable:* Run factor attribution on all your returns. How much is market beta? How much is size/value/momentum factor? The residual after factor attribution is your true alpha. Focus relentlessly on alpha, not leveraged beta.

---

## Quick Reference: Build vs. Buy Decision Matrix

| Component | Build | Buy/License | Notes |
|-----------|-------|-------------|-------|
| Backtesting framework | ✅ Build | | Full control needed |
| Market data pipeline | ✅ Build | | Standard, teachable |
| Signal generation | ✅ Build | | Core proprietary value |
| Order management | ✅ Build | | Need control |
| Risk management | ✅ Build | | Non-negotiable |
| Execution algorithms | ⚡ Buy initially | Then build | IBKR algo orders first |
| Historical market data | ❌ Buy | | Polygon.io, Norgate |
| Alternative data | ❌ Buy | | RavenPack, etc. |
| Monitoring/dashboard | ⚡ Either | | Grafana + custom |
| Prime brokerage | ❌ Use broker | | IBKR Pro initially |
| Compliance/legal | ❌ Hire | | Specialist required |

---

*Total estimated time from zero to first live dollars: 90 days.*  
*Total estimated time to Sharpe > 1.5 live: 12–18 months.*  
*Total estimated time to Vertus-comparable scale: 3–5 years.*

---

*Blueprint compiled from: Vertus public statements, industry research, academic literature, open-source quant resources. All code examples are illustrative pseudocode, not production-ready systems.*
