# Mersennet Faucet

Testnet faucet for Mersennet — distributes testnet PRIM to developers.

**Live:** [https://faucet.mersennet.com](https://faucet.mersennet.com)

## Features

- Request 1,000 testnet PRIM per address per hour
- MetaMask wallet connect with automatic chain configuration (Chain ID 131071)
- Mock stablecoins (USDC, USDT, DAI) via `faucet()` contract calls
- Light/dark theme toggle (persisted in localStorage, cosmic dark default)
- Transaction confirmation with explorer link

## Architecture

- Single HTML file with inline CSS/JS — no build step
- API calls go to the same-origin `/api` path; in production, Caddy on
  `faucet.mersennet.com` reverse-proxies `/api/*` to the faucet backend
  (`crates/node/src/bin/faucet.rs` in the chain repo) on the testnet host
- Rust backend using `tiny_http`

## Deploy

```bash
rsync index.html root@server:/var/www/faucet/
```

## Related

- [mersennet](https://github.com/mersennet/mersennet) — Core blockchain
- [explorer](https://github.com/mersennet/explorer) — Block explorer
- [trade](https://github.com/mersennet/trade) — Perps trading terminal
