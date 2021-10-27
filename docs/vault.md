#Overview

Vault module manages and stores the creation of vaults. 

A Collateralized Debt Position enables creation of the commodity synthetics by locking up another listed asset as collateral.

The Vault module manages and stores the creation of Collateralized Debt Position (CDP). Collateral is locked in a vault, and a new asset can be minted up to a fraction of the collateral value. The user must repay the debt by returning the minted asset to the vault to unlock the collateral. At this point, the minted asset will be burned, and the provided collateral is unlocked. 

The prices of assets are tracked from oracles like Band Protocol or a decentralized pool like Osmosis. A liquidation event is triggered when the collateralization ratio of the position falls below the minimum threshold value (Liquidation Ratio) for a cAsset.

Collateralization Ratio =     Value of collaterals locked up
             Value of borrowed assets

The liquidation ratio can vary depending on the collateral asset type and borrowed asset type. Additionally, the liquidation ratios can be modified and changed through governance proposals for each asset. A debt position can be closed when the borrowed cAsset is returned, and the borrower pays a fee to close the position. Upon closing a position, the cAsset is burned, and the collaterals that were locked up are returned to the borrower.
 
Example: 

The user locks $200 worth of ATOM to borrow $100 value of cAsset. 
In this case, the collateral ratio is 200%. Assuming the liquidation ratio to be at 150%, two cases can occur, which will lower the collateralization ratio. 

Case 1:  Prices of the cAsset increase
Liquidation will occur when the value of cAsset goes up to 133.33 (assuming the value of the collateral (ATOM) stays the same)

Case 2: Price of the Collateral decreases
Liquidation will occur when the price of Atom declines to 150$ (assuming the value of cAsset stays the same)
