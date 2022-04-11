#State

##Asset

An asset represents an on-chain representation of a real-world asset like Gold, Silver & Oil.

	type Asset struct {
		Id       uint64
		Name     string
		Denom    string
		Decimals int64
	}


##Pair

An asset pair represents pair of synthetics assets and ibc- assets. These pairs create a vault to mint cAssets. Where AssetIn is the collateral provided, AssetOut is the cAsset which we want to mint, and LiquidationRatio Defines the liquidation ratio for that particular pair.

	type Pair struct {
		Id               uint64
		AssetIn          uint64
		AssetOut         uint64
		LiquidationRatio types.Dec
	}
