#Overview

##Introducing Comdex

Comdex is an ecosystem of solutions built to bridge the gap between DeFi & CeFi by creating synthetic representations of real-world assets.

Investors holding a range of crypto assets can, on Comdex, collateralize and leverage their holdings to take exposure to synthetic assets. Users can lock-up their crypto holding in vaults and mint cAssets (synthetic assets on Comdex) which can be traded on a native exchange with other holders of cAssets.

This mechanism essentially enables holders of crypto assets to take simultaneous “long” positions on their holdings and other Assets.


##Challenges addressed by Comdex

Ordinary investors today are easily able to access equity & forex investments due to rapid advancements in the fields of technology and finance. These same asset classes were previously more restricted and more complicated for the ordinary investor to access. Similarly, advances in DeFi are enabling users today to access a wide range of financial services that were previously restricted to qualified investors only. 

Much to the tune of the innovations brought about by DeFi, Comdex aims to lead the movement towards enhancing the access of ordinary investors to a wide range of financial assets. Investors today are faced with the following challenges-

- Lack of global accessibility
- Lack of 24/7 markets
- Jurisdictional hurdles for cross-border capital movement
- Lengthy KYC AML processes.

A permissionless system where users can democratically create, hold, trade, and transact in synthetic assets helps users genuinely overcome the challenges and circumvent any hurdles they face in traditional financial markets.


##cAssets on Comdex

cAssets on Comdex are created by creating Collateralized Debt Positions (CDPs) upon locking up of collateral assets.

##CDP

A Collateralized Debt Position(CDP) enables the creation of the cAssets by locking up another listed asset as Collateral.

All cAssets are essentially debt, valued as a fraction of the total value of collateralized assets. An annualized (APY) interest rate is charged for users who borrow the cAssets, 	 calculated as a function of the duration of the debt. In the event of a drop in the prices, and thus valuation, of locked-up collaterals, a liquidation event is triggered, causing the collateral assets to be seized and auctioned by the system to reclaim and close the open debt position on the system.

The prices of assets are tracked from decentralized pools on other platforms (such as Osmosis). A liquidation event is triggered when the collateralization ratio of the position falls below the minimum threshold value for a cAsset. 

Collateralization ratio = (Value of collaterals locked up)/(Value of borrowed assets)

The liquidation ratio can vary depending on the collateral asset type and borrowed asset type. Additionally, the liquidation ratios can be modified and changed through governance proposals for each asset. A debt position can be closed when the borrowed cAsset is returned, and the borrower pays a fee (to close the position). Upon closing a position, the cAsset is burned, and the collaterals that were locked up are returned to the borrower. 


The creation of assets through CDPs can be achieved in one of two ways:

- Single collateral CDP: A borrower locks up one type of asset to borrow stable assets or cAssets. For example-
User locks $200 worth of ATOM to borrow $100 value of USD stable assets. 


- Multi collateral CDP: A borrower may lock up multiple types of collaterals assets that can be used to mint or borrow stable assets or cAssets. For example-
User locks $100 worth ATOM and $400 worth of CMDX to borrow $100 value of USD stable assets.
The platform will, over time, enhance its abilities to accept a mix of other stable and volatile assets that users could collateralize to mint cAssets. 


##Oracle
	
An oracle is an account that is whitelisted to provide prices for the assets on the chain. The data feed for the price oracles will be sourced from reputable external platforms sources like Band protocol. It may also receive prices from the cSwap or other AMM-based pools.



##Liquidations
	
At any point in time, the total value of collaterals locked in a CDP must be greater than the value of the position’s debt. This mechanism exists to ensure solvency and to ensure that open debt positions can be sufficiently collateralized to withstand volatility in prices of the collaterals. If the prices of the locked-up Collateral fall, driving the collateralization ratio down below a minimum collateral ratio, the assets locked up as Collateral are auctioned off to recover the amount of the outstanding debt of the position along with the fees charged for the liquidation itself. Any surplus portion of the collateral remaining after covering debt and fees is returned to the owner of the CDP.

During times of extreme price fluctuations and market volatility, there may occur an instance when the cumulative value of the locked-up assets doesn’t sufficiently cover the value of the debt and liquidation fees. This leads to the creation of system debt that can be absorbed by the CMDX token via a debt auction.
	
##Auctions
	
	
##cSwap

cSwap enables users on Comdex to swap their cAssets through an AMM (automated market maker). Swapping enables investors to take profit from the movement in relative prices of cAssets. An AMM is a decentralized finance protocol that facilitates the swapping of two assets without the need for a centralized intermediary. As is the case with trading firms, who make traditional markets, AMMs help establish prices and facilitate trades through permissionless liquidity pools. Assets are swapped through the AMM, and a trading fee is charged for each executed order. In addition, users of the platform can deposit their assets into liquidity pools that facilitate trading on cSwap, to earn CMDX token rewards and a portion of the trading fees earned by the pool.

cSwap adjusts the relative prices of cAssets to rebalance the pools to as close to “k” as possible. 

To preserve the constant product invariant (mentioned in the section above), the cSwap will change the relative prices of cAssets to ensure that the product of the resultant balances of the pool is as close to “k” as possible. 

With k being the current balance of the pool’s source assets and X & Y is that of the target asset


XY = k = (X + Ain) (Y - Bout)

With  being the current balance of the pool’s source asset and being that of the target asset:
XY=k=(X+Ain​)(Y−Bout​)

To determine the true value of  given the trader’s offered asset :
Bout​=XAin/(Y+Ain​)
​​

cSwap can execute trades with only the current balances of the pool and the number of incoming tokens. The market price is encoded as the pool’s target tokens divided by the source asset (also called the pool ratio). The spread between the executed and the expected trade is:

spread=max(​YAin/(X+Ain)​​−YAin/X​​,0)

When a pool has large balances of tokens on both sides from liquidity providers, the spread becomes smaller and helps the pool execute closer to its reported price of Y/X.

##AMM
	
An AMM is a decentralized finance protocol that facilitates the swapping of two assets without the need for a centralized intermediary. As is the case with trading firms, who make traditional markets, AMMs help establish prices and facilitate trades through permissionless liquidity pools. 

Assets are swapped through the AMM, and a trading fee is charged for each executed order. Users of the platform can deposit their assets into liquidity pools that facilitate trading on cSwap, to earn CMDX token rewards and a portion of the trading fees earned by the pool. cSwap then enables users on the platform to swap between cAssets based on the available liquidity pools


##Liquidity Pools
	
Liquidity providers are users of the platform who deposit their assets into an AMM pool to earn CMDX token rewards and a portion of the trading fees collected on the pool. Upon providing the liquidity, liquidity providers are issued LP shares (liquidity provider shares), representing their share of the total liquidity in the pool. 

Users pay a fee for each trade on the cSwap to buy from or sell to the liquidity pools. These transaction fees are added to the pool assets, which in essence, results in a pro-rata distribution of the proceeds to the LP shareholders.

To enable trading of a cAsset, a liquidity pool must be created containing the cAsset and a stable asset. For instance, users buying the cAsset can do so by swapping their stable assets against cAssets from the liquidity pool, causing the share of stable assets in the pool to increase and the share of cAssets to decrease. 

At this point, the liquidity pool must rebalance itself to ensure that it can continue to facilitate trades on the cSwap. This is done by changing the relative prices of the cAsset and stable asset to incentivize liquidity providers to increase the share of the asset in deficit. This dynamic rebalancing of the assets in the pools is achieved through the constant product formula.

(Balance of cAsset token Balance of stable asset token = k)

The constant product formula, “k”, represents a constant value that must be obtained through the product of the balance of the two tokens in the pool. For example, in a pool containing cAsset and stable asset, every time a cAsset is bought, the price of the cAsset goes up, incentivizing holders of the cAsset to sell to cSwap, leading to an increase in the share of the cAsset in the pool. 

##Features

The use of CDPs in minting synthetic assets and trading synthetic assets on AMM are key innovations in DeFi. They have empowered investors to diversify and hedge their exposures truly. Comdex aims to leverage these technologies and enhance them with some innovative features to help better integrate with the ecosystem and create more rewarding and sustainable incentive structures.


##Liquid- Staking assets as Collateral

cSwap enables users on Comdex to swap their cAssets through an AMM (automated market maker). Swapping enables investors to take profit from the movement in relative prices of cAssets. An AMM is a decentralized finance protocol that facilitates the swapping of two assets without the need for a centralized intermediary. As is the case with trading firms, who make traditional markets, AMMs help establish prices and facilitate trades through permissionless liquidity pools. Assets are swapped through the AMM, and a trading fee is charged for each executed order. In addition, users of the platform can deposit their assets into liquidity pools that facilitate trading on cSwap, to earn CMDX token rewards and a portion of the trading fees earned by the pool. 


##Perpetual Options rewards

Comdex will provide incentives to liquidity farmers in the form of Perpetual Call options on CMDX. These options, when exercised, allow their holders to purchase CMDX at a pre-determined discount from the market price. 

By doing so, we reduce the selling pressure on the CMDX token and establish a natural price floor. It also helps earn additional fee revenue.

##Real-world asset collateralization
