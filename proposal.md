# Project proposal

**Student:** Dimejesi Francisca
**Course:** Data Visualisation (data_visualisation_26)

## Project title

Gold vs Bitcoin: an interactive comparison of two stores of value

## Project description

Gold is the classic safe-haven asset, and Bitcoin is often called "digital gold". This project lets a user test that claim with real market data. The user chooses a time period and sees how the two assets performed, how risky each one was, how deep their losses went, and whether they moved together or independently.

The topic is financial and economic data. The application is a React web app (JavaScript) that runs fully in the browser, with no backend of its own.

## Data sources and how they will be used

1. **Bitcoin: Binance public market data API** (daily BTC/USDT candles, free, no API key). Used for the Bitcoin daily closing price and trading volume.
2. **Gold: FreeGoldAPI** (freegoldapi.com, an open historical gold price dataset in US dollars, no API key). Used for the gold price series.
3. **Backup source:** CoinGecko public API for Bitcoin if the main source is unavailable.

Both series are loaded in the browser, aligned on common dates and cached in localStorage. Gold is only traded on weekdays and Bitcoin trades every day, so the comparison uses weekday closes (or weekly closes for the correlation charts). From these prices the app calculates daily returns, rolling volatility, drawdowns and rolling correlation.

## Proposed visualizations and interactivity

- **Price comparison chart (D3.js).** Both assets rebased to 100 at the start date, so they can be compared on one axis. A date-range brush selects the period, and a switch changes between linear and logarithmic scale. Hovering shows a synchronized tooltip for both assets.
- **Summary cards.** Total return, yearly return, yearly volatility and maximum drawdown for the selected period, updated when the brush moves.
- **Rolling volatility chart.** Standard deviation of returns over a window that the user sets with a slider (30, 60 or 90 days).
- **Drawdown chart.** Shows how far each asset fell from its previous peak and how long it took to recover.
- **Rolling correlation chart.** Shows whether gold and Bitcoin moved together or in opposite directions over time.
- **Returns scatter plot.** One point per week, gold return against Bitcoin return, with a trend line.
- **"What if I invested" calculator.** The user enters an amount and a start date, and the chart shows what that investment would be worth today in each asset.

## Timeline for completion

| Period | Work |
|---|---|
| Weeks 1-2 | Set up the React project, load and cache data from both APIs, align the two series and calculate returns |
| Weeks 3-4 | Price comparison chart with brush, tooltip and log scale, plus the summary cards |
| Weeks 5-6 | Rolling volatility, drawdown and rolling correlation charts with the window slider |
| Week 7 | Returns scatter plot, investment calculator, loading and error states, mobile layout |
| Week 8 | Testing, polishing, deployment to GitHub Pages, short project report |
