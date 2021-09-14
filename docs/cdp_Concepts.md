#Concepts

A Collateralized Debt Position(CDP) enables creation of the cAssets by locking up another listed asset as collateral.

All cAssets are essentially debt, valued as a fraction of the total value of collateralized assets. An annualized (APY) interest rate is charged for users who borrow the cAssets, calculated as a function of the duration of the debt. In the event of a drop in the prices, and thus valuation, of locked-up collaterals, a liquidation event is triggered, causing the collateral assets to be seized and auctioned by the system to reclaim and close the open debt position on the system.

The prices of assets are tracked from decentralised pools on other platforms (such as Osmosis). A liquidation event is triggered when the collateralization ratio of the position falls below the minimum threshold value for a cAsset. 

Collateralization ratio= Value of collaterals locked upValue of borrowed assets

The liquidation ratio can vary depending on the collateral asset type and borrowed asset type. Additionally, the liquidation ratios can be modified and changed through governance proposals for each asset. A debt position can be closed when the borrowed cAsset is returned and a fee (to close the position) is paid by the borrower. Upon closing a position, the cAsset is burned and the collaterals that were locked-up are returned to the borrower. 


The creation of assets through CDPs can be achieved by one of two ways:

Single collateral CDP: A borrower locks up one type of asset in order to borrow stable assets or cAssets. For example-

User locks $200 worth of ATOM to borrow $100 worth of USD stable assets. 


Multi collateral CDP: A borrower may lock up multiple types of collaterals assets that can be used to mint or borrow stable assets or cAssets. For example-

User locks $100 worth ATOM and $400 worth of CMDX to borrow $100 worth of USD stable assets.

The platform will, over time, enhance its abilities to accept a mix of other stable and volatile assets that users could collateralise to mint cAssets.
