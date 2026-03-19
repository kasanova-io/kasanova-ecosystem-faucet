# Kasanova Ecosystem Faucet Rules

Distribution rules for the [Kasanova](https://kasanova.app) KRC20 token faucet. Projects listed here can distribute free tokens to new Kasanova users.

## How it works

1. A KRC20 project adds a rule file to `rules/`
2. The project deposits tokens to the faucet wallet
3. The faucet automatically distributes tokens to eligible users based on the rules

## Adding your token

1. Fork this repo
2. Create `rules/YOUR_TOKEN.yaml` following the format below
3. Submit a PR
4. Deposit tokens to the faucet wallet address (shown at the faucet `/status` endpoint)

## Rule format

```yaml
tick: YOUR_TOKEN       # Must match the filename
version: 1

eligibility:
  type: new_user       # Currently the only supported type
  max_age_days: 30     # Optional, default: 30. Users who joined within this many days.

distribution:
  amount_per_user: 500 # Tokens per eligible user (display units, not raw)
```

## Fields

| Field | Required | Description |
|-------|----------|-------------|
| `tick` | Yes | Token ticker, must match filename (case-insensitive) |
| `version` | Yes | Always `1` |
| `eligibility.type` | Yes | `new_user` (only supported type in v1) |
| `eligibility.max_age_days` | No | How recent the user must be (default: 30 days) |
| `distribution.amount_per_user` | Yes | Tokens each eligible user receives (display units) |

## Funding

There is no distribution cap. The faucet distributes until your token's balance runs out. Send more tokens to the faucet wallet to keep distributions going. Check the faucet `/status` endpoint to see your token's remaining balance.

## Current tokens

| Token | Amount per user |
|-------|----------------|
| BITE | 500 |
| KSNV | 100 |
