# Validator Setup

This is a detailed step-by-step guide for setting up a Comdex validator. Please be aware that while it is easy to set up a rudimentary validating node, running a performant production-quality validator node with a robust architecture and security features can require a non-trivial setup.

### Requirements

This guide starts with the following assumptions:

- You have [installed](https://docs.comdex.one/Node_installation/) the Comdex Full Node Software.
- You have [configured the node](https://docs.comdex.one/Node_config/) properly.
- You have [connected the node](https://docs.comdex.one/Node_join_testnet/) to an existing network.

### Register your Validator

You will need to know the consensus PubKey (`comdexvalconspub-`) of your node to create a new validator. You can find it with:

```
comdex tendermint show-validator
```

To create your validator, just use the following command:

```
comdex tx staking create-validator \
  --amount=1000000ucmdx \
  --pubkey=$(comdex tendermint show-validator) \
  --moniker="choose a moniker" \
  --chain-id=<chain_id> \
  --commission-rate="0.10" \
  --commission-max-rate="0.20" \
  --commission-max-change-rate="0.01" \
  --min-self-delegation="1000000" \
  --gas="auto" \
  --gas-prices="0.025ucmdx" \
  --from=<key_name>
```

> **NOTE**
>
> * When specifying commission parameters, the `commission-max-change-rate` is used to measure % *point* change over the `commission-rate`. E.g. 1% to 2% is a 100% rate increase, but only 1 percentage point.
> * `Min-self-delegation` is a stritly positive integer that represents the minimum amount of self-delegated voting power your validator must always have. A `min-self-delegation` of `1000000` (**??**) means your validator will never have a self-delegation lower than `1cmdx`

### Confirm Your Validator is Running

Your validator is active if the following command returns anything:

```
comdex query tendermint-validator-set | grep "$(comdex tendermint show-address)" 
```

You should now see your validator in one of the Comdex mainnet explorers. You are looking for the `bech32` encoded `address` in the `~/.comdex/config/priv_validator.json` file.

> **NOTE:**  To be in the validator set, you need to have more total voting power than the **130th** (**TODO**) validator.

### Edit Validator Description

You can edit your validator's public description. This info is to identify your validator, and will be relied on by delegators to decide which validators to stake to. Make sure to provide input for every flag below. If a flag is not included in the command the field will default to empty (`--moniker` defaults to the machine name) if the field has never been set or remain the same if it has been set in the past.

The <key_name> specifies which validator you are editing. If you choose to not include certain flags, remember that the --from flag must be included to identify the validator to update.

The `--identity` can be used as to verify identity with systems like Keybase or UPort. When using with Keybase `--identity` should be populated with a 16-digit string that is generated with a [keybase.io](https://keybase.io/) account. It's a cryptographically secure method of verifying your identity across multiple online networks. The Keybase API allows us to retrieve your Keybase avatar. This is how you can add a logo to your validator profile.

```
comdex tx staking edit-validator
  --moniker="choose a moniker" \
  --website="https://comdex.one" \
  --identity=6A0D65E29A4CBC8E \
  --details="To infinity and beyond!" \
  --chain-id=<chain_id> \
  --gas="auto" \
  --gas-prices="0.025ucmdx" \
  --from=<key_name> \
  --commission-rate="0.10"
```

> **NOTE**: The `commission-rate` value must adhere to the following invariants:
>
> - Must be between 0 and the validator's `commission-max-rate`
> - Must not exceed the validator's `commission-max-change-rate` which is maximum % point change rate **per day**. In other words, a validator can only change its commission once per day and within `commission-max-change-rate` bounds.

### View Validator Description

View the validator's information with this command:

```
comdex query staking validator <account_comdex>
```

### Track Validator Signing Information

In order to keep track of a validator's signatures in the past you can do so by using the `signing-info` command:

```
comdex query slashing signing-info <validator-pubkey> --chain-id=<chain_id>
```

### Unjail Validator

When a validator is `jailed` for downtime, you must submit an `Unjail` transaction from the operator account in order to be able to get block proposer rewards again (depends on the zone fee distribution).

```
comdex tx slashing unjail --from=<key_name> --chain-id=<chain_id>
```

### Halting Your Validator

When attempting to perform routine maintenance or planning for an upcoming coordinated upgrade, it can be useful to have your validator systematically and gracefully halt. You can achieve this by either setting the `halt-height` to the height at which you want your node to shutdown or by passing the `--halt-height` flag to `comdex`. The node will shutdown with a zero exit code at that given height after committing the block.

## Common Problems

### Problem #1: My validator has `voting_power: 0`

Your validator has become jailed. Validators get jailed, i.e. get removed from the active validator set, if they do not vote on `500` of the last `10000` blocks, or if they double sign.

If you got jailed for downtime, you can get your voting power back to your validator. First, if `comdex` is not running, start it up again:

```
comdex start
```

Wait for your full node to catch up to the latest block. Then, you can unjail your validator by following the procedure described in the preceding section.

Lastly, check your validator again to see if your voting power is back.

```
comdex status 
```

You may notice that your voting power is less than it used to be. That's because you got slashed for downtime!

### Problem #2: My `comdex` crashes because of `too many open files`

The default number of files Linux can open (per-process) is `1024`. `comdex` is known to open more than `1024` files. This causes the process to crash. A quick fix is to run `ulimit -n 4096` (increase the number of open files allowed) and then restart the process with `comdex start`. If you are using `systemd` or another process manager to launch `comdex` this may require some configuration at that level. A sample `systemd` file to fix this issue is below:

```
# /etc/systemd/system/comdex.service
[Unit]
Description=Comdec Node
After=network.target

[Service]
Type=simple
User=ubuntu
WorkingDirectory=/home/ubuntu
ExecStart=/home/ubuntu/go/bin/comdex start
Restart=on-failure
RestartSec=3
LimitNOFILE=4096

[Install]
WantedBy=multi-user.target
```

