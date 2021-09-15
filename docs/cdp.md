#Overview

CDP module manages and stores the creation of vaults/CDP's. 

A CDP enables the creation of an asset pegged to an external price (US Dollar) by collateralization with another asset. Collateral is locked in a vault, and a new stable asset can be minted up to a fraction of the collateral value. To unlock the collateral, the debt must be repaid by returning the minted asset to the vault at which point it will be burned, and the provided collateral is unlocked.

Pegged assets remain fully collateralized by the value locked in CDPs. In the event of price changes, this collateral can be seized and sold off in auctions by the system to reclaim and reduce the supply of minted assets.
