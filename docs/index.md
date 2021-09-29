#Overview

##Introducing Comdex

Comdex is a decentralized synthetics protocol of the Persistence ecosystem. Users can collateralize their holdings from the Cosmos ecosystem to take exposure to a range of synthetic assets. Comdex builds solutions to democratize finance by giving investors exposure to an extensive range of asset classes.


##What are synthetic assets?

A synthetic asset is an on-chain derivative that derives its value based on the price of an underlying asset. Synthetics enable investors to take speculative positions on the movement of assets without taking any direct exposure to the underlying asset itself. On Comdex, users can create, trade, and provide liquidity of a range of synthetic commodity assets.


##Why synthetics?

Due to geographical and regulatory limitations, investors today lack the freedom to access a large set of financial assets. Synthetics allow for the tokenization of real-world assets with fewer hurdles than those in the traditional derivatives markets. Synthetics also enable asset originators to gain liquidity on their illiquid debt assets by creating synthetic assets that facilitate a seamless flow of capital between asset classes. 

Comdex enables its users to lever up on their holding to take exposure to various synthetic cAssets. Users can mint cAssets with multiple assets from the Cosmos ecosystem as collateral.

##Why Commodities?

Commodities trade, a $17 trillion industry, is unquestionably the lifeblood of global supply chains. In times of economic uncertainty and high inflation, commodities prices tend to have long term inflation-resistance due to their inherently tangible and pragmatic value. 

Investors today cannot freely access these assets due to several financial and regulatory hurdles. Additionally, SME & MSME borrowers lack the trust and efficiency needed to qualify for financing, causing the $3.4 trillion financing gap. 

By combining the immutability of blockchain and interoperability of IBC, Comdex's synthetics protocol enables investors to take exposure to a broad range of financial assets seamlessly. By creating solutions across the industry, Comdex aims to build bridges for the flow of capital from DeFi and CeFi. Through tokenization of commodity assets and debt, investors can also take exposure to trade finance debt.


##What solutions does Comdex build?

Comdex is building a decentralized synthetics protocol on the Cosmos SDK to allow Cosmos ecosystem investors to trade commodity synthetics. Comdex has built an enterprise trading platform for physical commodities trading, built on the Persistence SDK, that enhances trust and efficiency in the commodities trade and trade finance industries.
Comdex will launch ShipFi, a dApp for digitization and exchange of commodity trade finance debt.


##Vault

A Vault enables the creation of the cAssets by locking up another listed asset as Collateral.

All cAssets are essentially debt, valued as a fraction of the total value of collateralized assets. An annualized (APY) interest rate is charged for users who borrow the cAssets, 	 calculated as a function of the duration of the debt. In the event of a drop in the prices, and thus valuation, of locked-up collaterals, a liquidation event is triggered, causing the collateral assets to be seized and auctioned by the system to reclaim and close the open debt position on the system.

The prices of assets are tracked from decentralized pools on other platforms (such as Osmosis). A liquidation event is triggered when the collateralization ratio of the position falls below the minimum threshold value for a cAsset. 

Collateralization ratio = (Value of collaterals locked up)/(Value of borrowed assets)

The liquidation ratio can vary depending on the collateral asset type and borrowed asset type. Additionally, the liquidation ratios can be modified and changed through governance proposals for each asset. A debt position can be closed when the borrowed cAsset is returned, and the borrower pays a fee (to close the position). Upon closing a position, the cAsset is burned, and the collaterals that were locked up are returned to the borrower. 


The creation of assets through Vaults can be achieved in one of two ways:

- Single collateral Vault: A borrower locks up one type of asset to borrow stable assets or cAssets. For example-
User locks $200 worth of ATOM to borrow $100 value of USD stable assets. 


- Multi collateral Vault: A borrower may lock up multiple types of collaterals assets that can be used to mint or borrow stable assets or cAssets. For example-
User locks $100 worth ATOM and $400 worth of CMDX to borrow $100 value of USD stable assets.
The platform will, over time, enhance its abilities to accept a mix of other stable and volatile assets that users could collateralize to mint cAssets. 


##Oracle
	
An oracle is an account that is whitelisted to provide prices for the assets on the chain. The data feed for the price oracles will be sourced from reputable external platforms sources like Band protocol. It may also receive prices from the cSwap or other AMM-based pools.


##Liquidations
	
At any point in time, the total value of collaterals locked in a Vault must be greater than the value of the position’s debt. This mechanism exists to ensure solvency and to ensure that open debt positions can be sufficiently collateralized to withstand volatility in prices of the collaterals. If the prices of the locked-up Collateral fall, driving the collateralization ratio down below a minimum collateral ratio, the assets locked up as Collateral are auctioned off to recover the amount of the outstanding debt of the position along with the fees charged for the liquidation itself. Any surplus portion of the collateral remaining after covering debt and fees is returned to the owner of the Vault.

During times of extreme price fluctuations and market volatility, there may occur an instance when the cumulative value of the locked-up assets doesn’t sufficiently cover the value of the debt and liquidation fees. This leads to the creation of system debt that can be absorbed by the CMDX token via a debt auction.
	
	
##cSwap

cSwap enables users on Comdex to swap their cAssets through an AMM (automated market maker). Swapping enables investors to take profit from the movement in relative prices of cAssets. An AMM is a decentralized finance protocol that facilitates the swapping of two assets without the need for a centralized intermediary. As is the case with trading firms, who make traditional markets, AMMs help establish prices and facilitate trades through permissionless liquidity pools. Assets are swapped through the AMM, and a trading fee is charged for each executed order. In addition, users of the platform can deposit their assets into liquidity pools that facilitate trading on cSwap, to earn CMDX token rewards and a portion of the trading fees earned by the pool.

cSwap adjusts the relative prices of cAssets to rebalance the pools to as close to “k” as possible. 

To preserve the constant product invariant (mentioned in the section above), the cSwap will change the relative prices of cAssets to ensure that the product of the resultant balances of the pool is as close to “k” as possible. 

With k being the current balance of the pool’s source assets and X & Y is that of the target asset

---
XY = k = (X + Ain) (Y - Bout)

---

To determine the true value of  given the trader’s offered asset

---
Bout​ = XAin/(Y+Ain​)

----

cSwap can execute trades with only the current balances of the pool and the number of incoming tokens. The market price is encoded as the pool’s target tokens divided by the source asset (also called the pool ratio). The spread between the executed and the expected trade is

---
spread = max(​YAin/(X+Ain)​​−YAin/X​​,0)

---

When a pool has large balances of tokens on both sides from liquidity providers, the spread becomes smaller and helps the pool execute closer to its reported price of Y/X.

##AMM
	
An AMM is a decentralized finance protocol that facilitates the swapping of two assets without the need for a centralized intermediary. As is the case with trading firms, who make traditional markets, AMMs help establish prices and facilitate trades through permissionless liquidity pools. 

Assets are swapped through the AMM, and a trading fee is charged for each executed order. Users of the platform can deposit their assets into liquidity pools that facilitate trading on cSwap, to earn CMDX token rewards and a portion of the trading fees earned by the pool. cSwap then enables users on the platform to swap between cAssets based on the available liquidity pools


##Liquidity Pools
	
Liquidity providers are users of the platform who deposit their assets into an AMM pool to earn CMDX token rewards and a portion of the trading fees collected on the pool. Upon providing the liquidity, liquidity providers are issued LP shares (liquidity provider shares), representing their share of the total liquidity in the pool. 

Users pay a fee for each trade on the cSwap to buy from or sell to the liquidity pools. These transaction fees are added to the pool assets, which in essence, results in a pro-rata distribution of the proceeds to the LP shareholders.

To enable trading of a cAsset, a liquidity pool must be created containing the cAsset and a stable asset. For instance, users buying the cAsset can do so by swapping their stable assets against cAssets from the liquidity pool, causing the share of stable assets in the pool to increase and the share of cAssets to decrease. 

At this point, the liquidity pool must rebalance itself to ensure that it can continue to facilitate trades on the cSwap. This is done by changing the relative prices of the cAsset and stable asset to reward liquidity providers to increase the share of the asset in deficit. This dynamic rebalancing of the assets in the pools is achieved through the constant product formula.

(Balance of cAsset token Balance of stable asset token = k)

The constant product formula, “k”, represents a constant value that must be obtained through the product of the balance of the two tokens in the pool. For example, in a pool containing cAsset and stable asset, every time a cAsset is bought, the price of the cAsset goes up, rewarding holders of the cAsset to sell to cSwap, leading to an increase in the share of the cAsset in the pool. 

##Features

The use of Vaults in minting synthetic assets and trading synthetic assets on AMM are key innovations in DeFi. They have empowered investors to diversify and hedge their exposures truly. Comdex aims to leverage these technologies and enhance them with some innovative features to help better integrate with the ecosystem and create more rewarding and sustainable rewards structures.


##Liquid- Staking assets as Collateral

cSwap enables users on Comdex to swap their cAssets through an AMM (automated market maker). Swapping enables investors to take profit from the movement in relative prices of cAssets. An AMM is a decentralized finance protocol that facilitates the swapping of two assets without the need for a centralized intermediary. As is the case with trading firms, who make traditional markets, AMMs help establish prices and facilitate trades through permissionless liquidity pools. Assets are swapped through the AMM, and a trading fee is charged for each executed order. In addition, users of the platform can deposit their assets into liquidity pools that facilitate trading on cSwap, to earn CMDX token rewards and a portion of the trading fees earned by the pool. 


##Perpetual Options rewards

Comdex will provide rewards to liquidity farmers in the form of Perpetual Call options on CMDX. These options, when exercised, allow their holders to purchase CMDX at a pre-determined discount from the market price. 

By doing so, we reduce the selling pressure on the CMDX token and establish a natural price floor. It also helps earn additional fee revenue.


