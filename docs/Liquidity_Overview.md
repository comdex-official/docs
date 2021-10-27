#Overview

The liquidity module integrates the Gravity Dex Protocol. This module enables users on Comdex to Swap, transfer, and pool assets.

##cSWAP

cSwap enables users of the platform to swap their cAssets through an AMM (automated market maker). An AMM is a decentralized finance protocol that facilitates the swapping of two assets without the need for a centralized intermediary. As is the case with trading firms, who make traditional markets, AMMs help establish prices and facilitate trades through permissionless liquidity pools. Assets are swapped through the AMM, and a trading fee is charged for each executed order. Users of the platform can deposit their assets into liquidity pools that facilitate trading on cSwap, to earn CMDX token rewards and a portion of the trading fees earned by the pool. 

##AMM – Automated Market Maker

The Cosmos-based liquidity module enables the creation of an AMM that governs the swapping between two pairs of assets. As one asset is swapped for the other, the relative prices shift, with a new market rate for both determined. In this dynamic, a trader directly deals with the pool.
The liquidity pool must re-balance itself to ensure that it can continue to facilitate trades on the cSwap. This is done by changing the relative prices of the cAsset and stable assets to incentivize liquidity providers to increase the share of the asset in deficit. This dynamic re-balancing of the assets in the pools is achieved through the constant product formula.

Balance of cAsset token * Balance of stable asset token = k

In the constant product formula, “k” represents a constant value that must be obtained through the product of the balance of the two tokens in the pool. For example, in a pool containing cAsset and stable assets, every time a cAsset is bought, the price of the cAsset goes up, incentivizing holders of the cAsset to sell to the pool on cSwap, leading to an increase in the share of the cAsset in the pool. 

##Liquidity Pool

A liquidity pool is a collection of assets that people pool together to give the exchange the liquidity it requires in order to power the AMM. For example, if cAssets are lent to the liquidity pool, it provides the protocol with the necessary liquidity to facilitate trading. The pool facilitates trading between a particular pair of assets by holding reserves of both assets. 

##Liquidity Provider (LP)

Liquidity providers are users of the platform who deposit their assets into an AMM pool to earn CMDX token rewards and a portion of the trading fees collected on the pool. For each trade on the cSwap, users pay a fee to buy from or sell to the liquidity pools. 

For more information on Gravity Dex visit : [Gravity Dex](https://cosmos.network/gravity-dex/)

