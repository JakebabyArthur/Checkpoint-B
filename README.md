# Checkpoint-B
Summary from Checkpoint A
# ETF Term Project: The Future Technologies and Infrastructure ETF  
**Hongduo Shan**

## Introduction & Investment Philosophy

The Future Technologies and Infrastructure ETF (FTI-ETF) is a long-term, fundamental growth ETF that invests in durable leaders in artificial intelligence, cloud computing, and digital infrastructure, complemented by broad-market exposure for stability. The core thesis is: buy and hold companies with strong financial health, market leadership, and sustained innovation, while compounding returns through full dividend reinvestment. A lightweight momentum-based risk gate temporarily avoids names exhibiting persistent negative total-return trends (e.g., six-month declines) without introducing active trading or short-term timing. The fund targets investors seeking secular technology and infrastructure growth with a disciplined, low-turnover ownership approach.

### Strategy Statement
- **Primary return driver:** Fundamental ownership of best-in-class AI, cloud, and infrastructure companies selected for financial resilience, innovation investment, and competitive positioning; held long term with dividends reinvested.  
- **Secondary risk management rule:** Delay or flag inclusion of names showing sustained negative momentum (rolling six-month total return decline); review quarterly.  
- **Rebalancing cadence:** Annual or semi-annual to correct drift while minimizing turnover.  
- **Benchmarking:** Evaluate performance against broad-market benchmarks (e.g., S&P 500 total return) to compute alpha and other risk-adjusted metrics.

### Focused Investment Universe

#### Core Equity Holdings (Technology / AI / Cloud Infrastructure)
- Microsoft (MSFT): Cloud platform, AI infrastructure, recurring enterprise revenue.  
- Nvidia (NVDA): AI compute (GPUs), critical for model training/inference.  
- Alphabet (GOOGL): Cloud services and AI applications with strong balance sheet.  
- Amazon (AMZN): AWS cloud leadership with embedded AI capabilities.  
- Meta Platforms (META): AI/AR infrastructure and large-scale engagement.  
- Adobe (ADBE): SaaS creative/cloud tools augmented by AI.  
- Salesforce (CRM): Cloud SaaS with enterprise stickiness and AI features.  
- ASML (ASML) and Taiwan Semiconductor (TSM): Semiconductor supply-chain enablers essential to the AI/infrastructure ecosystem.  
- ServiceNow (NOW): Enterprise cloud workflow automation with growing AI integration.

#### Diversifying Core Exposure
- Broad-market index exposure, e.g., S&P 500 total return proxy to stabilize and anchor market beta.

#### Fundamental Selection Criteria
1. Profitability and free-cash-flow generation.  
2. Consistent or growing R&D investment (innovation signal).  
3. Strong balance-sheet metrics (low leverage, healthy liquidity).  
4. Market leadership / economic moat.  
5. History of dividend distributions to enable compounding.

## Checkpoint B: Literature Review, Market Data Plan, and Methodological Justification

### 1. Literature Review

#### 1.1 Fundamental, Buy-and-Hold Investing and Compounding  
Long-horizon ownership of quality firms with dividend reinvestment is rooted in classic investment philosophy. Disciplined fundamental selection and compounding via dividends justify a buy-and-hold core.

#### 1.2 Portfolio Diversification and Efficient Trade-offs  
Markowitz’s mean-variance framework motivates balancing return and risk through diversification, combining concentrated high-quality names with broad-market ballast. Sharpe’s performance metrics (Sharpe ratio, alpha, beta) decompose active selection versus market exposure.

#### 1.3 Total Return Accounting  
Accurate total return (price appreciation plus reinvested dividends) construction is essential to capture the full economic benefit of long-term ownership and comparing against benchmarks.

#### 1.4 Trend Information as Risk Gate  
A conservative trend filter (six-month declining total return) is used as a risk gate, not an active timing mechanism, to avoid embedding names in pronounced deterioration phases while preserving the long-term buy-and-hold orientation.

#### 1.5 Benchmarking and Evaluation  
Measuring alpha and beta relative to a broad benchmark (e.g., S&P 500 total return) clarifies active value versus systematic market exposure. Risk-adjusted metrics like the Sharpe ratio contextualize returns for investors.

### 2. Market Data Plan

#### 2.1 Data Sources
- Yahoo Finance via yfinance: Primary source for daily adjusted prices and dividend distributions for core equities and benchmark proxies.  
- Benchmark: S&P 500 total return (constructed or proxied via dividend-reinvesting ETF).  
- Supplementary: Optional cross-checks or gap-filling via QuantConnect APIs.

#### 2.2 Time Horizon  
January 1, 1999 to Augest 1, 2025. This range captures major regime events: dot-com bust, 2007–2008 financial crisis, European debt crisis, COVID-19 shock and recovery.

#### 2.3 Frequency and Aggregation  
Base frequency: daily.  
Aggregates: weekly or monthly as needed (e.g., for computing six-month total returns for the risk gate).

#### 2.4 Total Return Construction  
Construct cumulative total return series by reinvesting dividends on payment dates. Use adjusted close carefully (verify inclusion of distributions) or apply dividend amounts explicitly for compounding.

#### 2.5 Implementation Sketch (Python)
```python
import yfinance as yf  
import pandas as pd  

def get_total_return(ticker, start="1999-01-01", end="2025-08-01"):  
    data = yf.download(ticker, start=start, end=end, progress=False)  
    # Adjusted Close may reflect splits/dividends; verify or explicitly reconstruct reinvested dividends.  
    data = data[['Adj Close', 'Dividends']].copy()  
    # Placeholder: build total return assuming reinvestment at next available price.  
    return data  
