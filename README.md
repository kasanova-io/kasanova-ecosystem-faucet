# Kasanova Ecosystem Faucet

Distribution rules for the [Kasanova](https://kasanova.app) KRC20 token faucet. Projects listed here can distribute free tokens to Kasanova users.

## How it works

1. A KRC20 project adds a rule file to `rules/`
2. The project deposits tokens to the faucet wallet
3. The faucet automatically distributes tokens to eligible users based on the rules
4. When the balance runs out, distributions pause until refilled

## Adding your token

1. Fork this repo
2. Copy `TEMPLATE.yaml` to `rules/YOUR_TOKEN.yaml`
3. Fill in your token ticker and amount per user
4. Submit a PR
5. Once merged, deposit tokens to the faucet wallet

The faucet wallet address and current balances are visible at the `/status` endpoint.

## Rule format

```yaml
tick: YOUR_TOKEN       # required, must match filename
version: 1             # required

eligibility:           # optional, defaults to all_users
  type: all_users      # all_users (default) or new_users
  # max_age_days: 30   # only for new_users

distribution:
  amount_per_user: 500 # required, display units (not raw)
```

## Eligibility types

| Type | Description |
|------|-------------|
| `all_users` | Every Kasanova user (default) |
| `new_users` | Only users who joined within `max_age_days` (default: 30) |

## Fields

| Field | Required | Description |
|-------|----------|-------------|
| `tick` | Yes | Token ticker, must match filename (case-insensitive) |
| `version` | Yes | Always `1` |
| `eligibility.type` | No | `all_users` (default) or `new_users` |
| `eligibility.max_age_days` | No | For `new_users` only. Days since registration (default: 30) |
| `distribution.amount_per_user` | Yes | Tokens each user receives (display units) |

## Current tokens

| Token | Type | Amount per user |
|-------|------|-----------------|
| BITE | new_users (30d) | 500 |
| KSNV | new_users (30d) | 100 |
