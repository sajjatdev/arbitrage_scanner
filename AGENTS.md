# AGENTS.md

## Project goal
Arbitrage scanner for multi-exchange crypto/forex/stocks. Display matched symbols, spread, buy/sell exchange names, fees per side, profit after fees for 1 unit.

## Stack (must use)
- HTML, JS, jQuery, Tailwind CSS (CDN)
- CCXT via browser build: 
  - `https://cdnjs.cloudflare.com/ajax/libs/ccxt/4.5.90/ccxt.browser.min.js`
  - `integrity="sha512-SDXT2RIoe/tiXvXYPfmrMZbRQTJBd2oUzuoySkUFJaRTMiZrZet+V4ZYM14BIWgtX4krI5GG938EiVzE/5HH4g=="` `crossorigin="anonymous"` `referrerpolicy="no-referrer"`

## Required UI
- Filters (asset class: crypto/forex/stocks; exchanges; min spread; fees toggle; etc.)
- Search
- Table with: symbol, asset class, buy exchange, sell exchange, buy price, sell price, spread %, fees (buy/sell/total), profit after fees (per 1 unit)

## Rules
- Use CCXT exchange objects; normalize symbols per exchange.
- Compute spread = sellPrice - buyPrice (or %), apply trading fees (maker/taker) from exchange markets/fees if available.
- Show buy/sell exchange names explicitly.
- Support crypto, forex, stocks.
- Keep logic client-side (static HTML/JS).
- Prefer CDN assets only as specified.

## Gotchas
- CCXT browser build loads exchanges; some require CORS/proxy or have rate limits - handle gracefully.
- Symbol formats differ across exchanges (e.g. BTC/USDT vs BTCUSDT).
- Fee fields vary (tradingFees, fees.trading, taker/maker). Fallbacks needed.
- Forex/stocks coverage depends on exchange - filter unsupported pairs.

## Commands
- Open `index.html` in browser (no build step). If local fetch fails due to CORS,
