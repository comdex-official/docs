#Concepts

A Vault enables the creation of the cAssets by locking up another listed asset as collateral.

All cAssets are essentially debt, valued as a fraction of the total value of collateralized assets. An annualized (APY) interest rate is charged for users who borrow the cAssets, calculated as a function of the duration of the debt. In the event of drop in the prices, and thus valuation, of locked-up collaterals, a liquidation event is triggered, causing the collateral assets to be seized and auctioned by the system to reclaim and close the open debt position on the system.

##Example

The user locks $200 worth of ATOM to borrow $100 value of cAsset. 
In this case, the collateral ratio is 200%. Assuming the liquidation ratio to be at 150%, two cases can occur, which will lower the collateralization ratio. 

Case 1:  Prices of the cAsset increase
Liquidation will occur when the value of cAsset goes up to 133.33 (assuming the value of the collateral (ATOM) stays the same)

Case 2: Price of the Collateral decreases
Liquidation will occur when the price of Atom declines to 150$ (assuming the value of cAsset stays the same)


