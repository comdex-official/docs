#Introduction

Comdex is based on [Tendermint (opens new window)](https://github.com/tendermint/tendermint/tree/master/docs/introduction), which relies on a set of validators that are responsible for committing new blocks in the blockchain. These validators participate in the consensus protocol by broadcasting votes which contain cryptographic signatures signed by each validator's private key.

Validator candidates can bond their own CMDX and have CMDX delegated, or staked, to them by token holders. The Comdex Mainnet will have **X** validators, but over time this will increase to **X** validators according to a predefined schedule. The validators are determined by who has the most stake delegated to them — the top **X** validator candidates with the most stake will become Comdex validators.

Validators and their delegators will earn compute fees in CMDX as block provisions and tokens as transaction fees through execution of the Tendermint consensus protocol. Validators may set minimum gas fees for transactions to be included in their mempool. At the end of every block, the compute fees are disbursed to the participating validators pro-rata to stake.

If validators double sign, are frequently offline or do not participate in governance, their staked Atoms (including Atoms of users that delegated to them) can be slashed. The penalty depends on the severity of the violation.

&nbsp;

#Hardware

There currently exists no appropriate cloud solution for validator key management. This may change in 2018 when cloud SGX becomes more widely available. For this reason, validators must set up a physical operation secured with restricted access. A good starting place, for example, would be co-locating in secure data centers.

Validators should expect to equip their datacenter location with redundant power, connectivity, and storage backups. Expect to have several redundant networking boxes for fiber, firewall and switching and then small servers with redundant hard drive and failover. Hardware can be on the low end of datacenter gear to start out with.

We anticipate that network requirements will be low initially. The current testnet requires minimal resources. Then bandwidth, CPU and memory requirements will rise as the network grows. Large hard drives are recommended for storing years of blockchain history.