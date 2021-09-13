#CDP

Overview
The x/cdp module stores and manages Collateralized Debt Positions (or CDPs).

A CDP enables the creation of a stable asset pegged to an external price (usually US Dollar) by collateralization with another asset. Collateral is locked in a CDP and new stable asset can be minted up to some fraction of the value of the collateral. To unlock the collateral, the debt must be repaid by returning some stable asset to the CDP at which point it will be burned and the collateral unlocked.

Pegged assets remain fully collateralized by the value locked in CDPs. In the event of price changes, this collateral can be seized and sold off in auctions by the system to reclaim and reduce the supply of stable assets.


