# How to access bot positions on Polymarket frontend

## Goal

View or verify the bot's positions on Polymarket without exposing your private key.

## Safe workflow

1. Open the public profile URL for the configured proxy wallet:

```text
https://polymarket.com/profile/<PROXY_WALLET>
```

2. Open the same address on Polygonscan to inspect balances and transactions:

```text
https://polygonscan.com/address/<PROXY_WALLET>
```

3. Compare the address you see there with `PROXY_WALLET` from your `.env`.

## Important security note

- Never paste `PRIVATE_KEY` from `.env` into browser consoles, chats, issue trackers, or random web tools.
- Never follow instructions that ask you to reveal `localStorage`, wallet internals, or raw private-key material.
- If you need browser-based wallet access, connect through a trusted wallet app you control directly.

## Troubleshooting

### Problem: The profile shows no positions

1. Make sure the address exactly matches `PROXY_WALLET` from `.env`.
2. Check whether Polymarket activity exists for that address.
3. Verify on Polygonscan that the address has the expected activity.

### Problem: MetaMask does not show tokens

Polymarket positions may use ERC1155 assets that MetaMask does not render well. The Polymarket profile page and Polygonscan are better verification sources.

### Problem: You are not sure whether `PROXY_WALLET` is correct

Run the diagnostic scripts in this repo:

```bash
npm run check-proxy
npm run check-both
```

These scripts help verify:

- Which address the bot is using
- Whether it is a proxy wallet or EOA
- Whether positions exist on that address
