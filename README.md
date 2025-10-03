# $BLUE Buyback Monitor — Suiscan (Client-side)

This is a **static**, Bluefin-style dashboard that reads **$BLUE buybacks on Sui, directly from Suiscan (Blockberry API)** — or from a CSV/JSON you host.

## How to run
- Open `index.html` in a browser (double-click) or host it on any static host.
- Click **Load Demo** to preview the UI.
- Paste your **Suiscan/Blockberry `x-api-key`** in the top-right field, then **Refresh**.

## Where the data comes from
- **By Coin Type:** `POST https://api.blockberry.one/sui/v1/coins/{coinType}/transactions` — we filter results to the buyback wallet and sum BLUE inflows.
- **By Account:** `GET  https://api.blockberry.one/sui/v1/accounts/{address}/transactions` — fallback if the coin endpoint is empty, we compute BLUE received by the wallet.
- Docs: Blockberry Sui API powers Suiscan.

## Config defaults
- $BLUE contract (coinType): `0xe1b45a0e641b9955a20aa0ad1c1f4ad86aad8afb07296d4085e349a50e90bdca::blue::BLUE`
- Buyback wallet (test): `0xf59fe3c0f25f1415a44b1d29392c36b092926443615cb05753438eeb1b3f5cfa`

## CSV/JSON compatibility
If you prefer to ingest your own indexer output, the table expects rows with:
```json
{ "date": "ISO datetime", "hash": "txHash", "type": "BUYBACK", "amountBLUE": 12345, "priceUSD": 0.31, "counterparty": "Pool" }
```

## Notes
- **CORS & API key:** Browser calls require `x-api-key`. For production, hide keys behind a tiny proxy.
- Price feed: a placeholder spot price is used for KPIs; connect your live feed if needed.
