#Overview

The x/asset module includes asset creation, asset pair creation.

##What are cAssets?

cAssets are synthetics that reflect commodity derivative contracts whose prices are reflected on-chain. This gives users price exposure to commodity assets and enables open access. Synthetics help us eliminate borders and truly decentralize commodity trading. Unlike traditional commodities, which represent a real, underlying asset, cAssets are purely synthetic and, therefore, capture the underlying asset's price movement. For example, cXAU (Gold) captures the price movement of real-world gold derivative contracts.

##Listing of cAsset 

A cAsset will get listed on the Comdex Synthetics Protocol once the following steps have been achieved:
    • Create the cAsset token and define all parameters 
    • Assign the oracle feeder
    • Create the cAsset-UST trading pair on cSwap and its LP token
Listing is approved by a new governance proposal and immediately implemented once 51% of the total governance votes have been garnered. Once a cAsset has been listed, it can be used for minting against Cosmos ecosystem assets as collaterals and available on cSwap. Liquidity providers earn CMDX tokens which can be used to create more cAssets. 

##Removal of cAsset

Due to external circumstances, when there is a possibility that trading activity with respect to the commodity could be halted, floated in the form of a governance proposal in the protocol, a cAsset can be delisted. 
    • CDPs can no longer mint new tokens of the cAsset to be delisted.
    • Burns will take effect at the fixed end price set by the oracle feeder for withdrawing collateral from existing mint positions.
Users will be asked to burn the cAsset to recover collateral from any open positions on the Comdex Synthetics Protocol. The old cAsset will be retired and marked as delisted, only allowing burn, close CDP, withdrawal of collateral, and liquidity.
