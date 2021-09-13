#State

#Asset

	type Asset struct {
		Id       uint64
		Name     string
		Denom    string
		Decimals int64
	}


#Pair
	type Pair struct {
		Id               uint64
		AssetIn          uint64
		AssetOut         uint64
		LiquidationRatio types.Dec
	}
