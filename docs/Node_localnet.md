# Running a Local Testnet

After you've gotten the latest version of Comdex Core installed, you can set up a private comdex network to get your bearings in running a Comdex full node before [joining an existing network](join-network.md).

## Single Node Setup

The simplest Comdex network you can set up will be a local testnet with just a single node. You will create one account and be the sole validator signing blocks for the network.

### Step 1. Create network and account

First, initialize your genesis file that will bootstrap the network. Set a name for your local testnet, and provide a moniker to refer to your node.

```bash
comdex init --chain-id=<testnet_name> <node_moniker>
```

You will need a Comdex account to start. You can generate one with:

```bash
comdex keys add <account_name>
```

### Step 2. Add account to genesis

Next, you need to add your account to the genesis. The following commands add your account and set the initial balance:

```bash
comdex add-genesis-account $(comdex keys show <account_name> -a) 100000000ucmdx,1000usd
comdex gentx --name my_account --amount 10000000ucmdx
comdex collect-gentxs
```

### Step 3. Run Comdex daemon

Now, you can start your private Comdex network:

```bash
comdex start
```

Your `comdex` node should now be running a node on `tcp://localhost:26656`, listening for incoming transactions and signing blocks. You've successfully set up your local Comdex network!
