# BLUE Buyback Monitor — Static Site

A single-page, Bluefin-styled dashboard to track **$BLUE buybacks on Sui** (on-chain only).  
Language: **English**. No BTC section.

## Files
- `index.html` — all-in-one page (embedded CSS & JS, uses Chart.js via CDN).

## Quick Start
1. Open `index.html` locally in your browser **or** upload the file to any static host (GitHub Pages, Netlify, Vercel, S3, Nginx).
2. Click **Load Demo Data** to preview.
3. When you have the correct wallet/indexer, replace the fetcher:
   - In `index.html`, find `fetchOnChainTx(...)` and plug your API calls (Sui explorer or your own indexer).
   - Expected output format per row:
     ```js
     { date: 'ISO string', hash: 'txHash', type: 'BUYBACK', amountBLUE: Number, priceUSD: Number, counterparty: 'Pool|...' }
     ```

## Defaults
- Contract: 0xe1b45a0e641b9955a20aa0ad1c1f4ad86aad8afb07296d4085e349a50e90bdca::blue::BLUE
- Aggregation wallet (placeholder): 0xf59fe3c0f25f1415a44b1d29392c36b092926443615cb05753438eeb1b3f5cfa

## Notes
- **No build** needed — it's just one HTML file.
- Chart.js is loaded from a CDN to keep the page self-contained.
- Pricing: the page uses a placeholder `priceBLUE_USD`. Replace it with a real feed if needed.
