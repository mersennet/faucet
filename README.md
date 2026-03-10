# Prime Chain Faucet

Testnet faucet for Prime Chain — distributes testnet PRIM and mock tokens to developers.

**Live:** [http://46.225.30.187:4005](http://46.225.30.187:4005)

## Features

- Request 1,000 testnet PRIM per address per hour
- MetaMask wallet connect with automatic chain configuration
- Mock stablecoins (USDC, USDT, DAI) via `faucet()` contract calls
- Light/dark theme toggle (persisted in localStorage)
- Transaction confirmation with explorer link

## Design

Branded with the PrimeFi/PrimeStaking design system:

- **Sora** font (300 weight default)
- Purple-dominant palette (`#9461FF` primary, `#6A2FFF` secondary)
- Light mode default, dark mode via toggle
- Gradient CTAs matching `primestaking-ui-v2`

## Stack

- Single HTML file with inline CSS/JS
- Rust backend (`faucet.rs`) using `tiny_http`

## Deploy

```bash
scp index.html user@server:/var/www/faucet/
```

## Related

- [prime-chain](https://github.com/PrimeNumbersLabs/prime-chain) — Core blockchain
- [primenodes-dashboard](https://github.com/PrimeNumbersLabs/primenodes-dashboard) — Validator dashboard
- [primescan-explorer](https://github.com/PrimeNumbersLabs/primescan-explorer) — Block explorer
