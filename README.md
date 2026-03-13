# Multi Agent Portfolio
A multi-agent LLM pipeline that generates personalized ETF investment portfolios based on individual investor profiles. Three specialized AI agents collaborate: a market analyst, a risk assessor, and a portfolio constructor. Together they analyze real market data and produce tailored recommendations.

## How It Works
1. **Data Collection**  
Pulls 2 years of historical price data for 43 ETFs across 11 sectors using `yfinance`, computes performance metrics (Sharpe ratio, volatility, max drawdown, etc.), and fetches recent news headlines for each ETF.

2. **User Profiling**  
Accepts investor profiles with age, risk tolerance, investment horizon, goals, and interests.

3. **Market Analyst Agent**  
Analyzes ETF metrics to identify sector trends and top and bottom performers.

4. **Risk Assessment Agent**  
Evaluates the investor profile and recommends a target asset allocation.

5. **Portfolio Construction Agent**  
Combines the outputs from the previous agents to produce a final ETF allocation that sums to 100%.

## Tech Stack
- Python  
- OpenAI API (GPT-4.1)  
- yfinance  
- pandas, numpy  
- matplotlib, seaborn  

## Setup
1. Clone the repo  
2. Install dependencies  
```bash
pip install openai yfinance pandas numpy matplotlib seaborn python-dotenv
```
3. Set your OpenAI API key as an environment variable
```bash
export OPENAI_API_KEY='your-key-here'
```
4. Open and run `AI-Agent.ipynb` in Jupyter

## Sample Investor Profiles
The notebook includes four pre-built profiles to test the pipeline:

| Name | Age | Risk Tolerance | Horizon | Amount |
|------|-----|---------------|---------|--------|
| Alex (Young Professional) | 28 | Aggressive | 30+ years | $5,000 |
| Jamie (Mid-Career) | 45 | Moderate | 15–20 years | $10,000 |
| Richie (Near Retirement) | 60 | Conservative | 5–10 years | $200,000 |
| Raabiyaal (Graduate Student) | 24 | Moderate | 25+ years | $200 |

## Example Output
For an aggressive young investor, the pipeline might recommend a tech-heavy growth portfolio:
```json
{
  "XLK": 40,
  "QQQ": 25,
  "SMH": 10,
  "IYW": 10,
  "BND":  7,
  "SGOV":  3,
  "Cash/Alternatives": 5
}
```
For a conservative near-retirement investor, it shifts toward capital preservation:
```json
{
  "BND":  40,
  "SGOV": 10,
  "BNDX": 10,
  "XLP":  20,
  "VNQ":  10,
  "Cash": 10
}
```
