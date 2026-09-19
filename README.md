<p align="center"><a href="https://mersennet.com"><img src="https://raw.githubusercontent.com/mersennet/.github/main/profile/mark.svg" width="72" alt="Mersennet"></a></p>
<h1 align="center">Mersennet Faucet</h1>
<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-7dff9b?style=flat-square" alt="MIT license"></a>
  <a href="https://github.com/mersennet/faucet/actions/workflows/ci.yml"><img src="https://github.com/mersennet/faucet/actions/workflows/ci.yml/badge.svg?branch=main" alt="CI"></a>
  <a href="https://faucet.mersennet.com"><img src="https://img.shields.io/badge/docs-mersennet-1c1c1c?style=flat-square" alt="Docs"></a>
  <a href="https://t.me/Mersennet"><img src="https://img.shields.io/badge/telegram-%40Mersennet-26A5E4?style=flat-square" alt="Telegram"></a>
</p>

Testnet faucet for Mersennet — distributes testnet MRSN to developers.

**Live:** [https://faucet.mersennet.com](https://faucet.mersennet.com)

## Features

- Request 1,000 testnet MRSN per address per hour
- MetaMask wallet connect with automatic chain configuration (Chain ID 131071)
- Mock stablecoins (USDC, USDT, DAI) via `faucet()` contract calls
- Light/dark theme toggle (persisted in localStorage, cosmic dark default)
- Transaction confirmation with explorer link

## Architecture

- Single HTML file with inline CSS/JS — no build step
- The page POSTs the drip request to the same-origin `/faucet` path; in
  production, Caddy on `faucet.mersennet.com` reverse-proxies `POST /faucet`
  to the faucet backend (`crates/node/src/bin/faucet.rs` in the chain repo,
  listening on `0.0.0.0:8080` on the testnet host). Without that proxy, POST
  hits the static file server and returns 405.
- Rust backend using `tiny_http`

## Deploy

```bash
rsync index.html root@server:/var/www/faucet/
# Install the vhost so the drip endpoint is reachable (see Caddyfile):
#   cp Caddyfile /etc/caddy/sites/faucet.mersennet.com  (replace FAUCET_BACKEND)
#   caddy reload
```

`Caddyfile` in this repo is the required `faucet.mersennet.com` vhost: it serves
the static page and proxies `POST /faucet` (+ `/claim-token`, `/health`) to the
backend.

## Related

- [mersennet](https://github.com/mersennet/mersennet) — Core blockchain
- [explorer](https://github.com/mersennet/explorer) — Block explorer
- [trade](https://github.com/mersennet/trade) — Perps trading terminal

---

<p align="center">
  Part of the <a href="https://github.com/mersennet">Mersennet</a> ecosystem —
  <a href="https://trade.mersennet.com">trade</a> ·
  <a href="https://explorer.mersennet.com">explorer</a> ·
  <a href="https://docs.mersennet.com">docs</a> ·
  <a href="https://mersennet.com/downloads/">run a node</a> ·
  <a href="https://t.me/Mersennet">Telegram</a><br>
  <sub>© 2026 Mersennet Foundation · MIT License · security@mersennet.com</sub>
</p>
