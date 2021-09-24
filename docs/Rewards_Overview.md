#Overview

x/rewards is an implementation of a Cosmos SDK Module that allows for governance controlled user rewards for users who take certain actions, such as opening a vault. Governance proposes an array of rewards, with each item representing a collateral type that will be eligible for rewards. Each collateral reward specifies the number of coins awarded per second, the length of rewards periods. Governance can alter the collateral rewards using parameter change proposals as well as adding or removing collateral types. All changes to parameters would take place in the next period. User rewards are opt in, ie. users must claim rewards in order to receive them. If users fail to claim rewards before the claim period expiry, they are no longer eligible for rewards.


LP rewards

Rewards are always paid out in CMDX tokens.

There is a reward pool for each of the trading pairs. These pools get replenished from a master pool which contains tokens allocated for the LP rewards
APY Calculations and adjusting rewards with movement in CMDX price.


