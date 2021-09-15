#Messages

Below various messages are sent to the asset module which trigger state changes detailed below.

#AddAsset:

	type MsgAddAssetRequest struct {
		From     string
		Name     string
		Denom    string
		Decimals int64
	}
	
#UpdateAsset:	

	type MsgUpdateAssetRequest struct {
		From     string
		Id       uint64
		Name     string
		Denom    string
		Decimals int64
	}
	
#AddMarketForAsset:
	
	type MsgAddMarketForAssetRequest struct {
		From   string
		Id     uint64
		Symbol string
	}
	
#RemoveMarketForAsset:

	type MsgRemoveMarketForAssetRequest struct {
		From   string
		Id     uint64
		Symbol string
	
	}

#AddPair:

	type MsgAddPairRequest struct {
		From             string
		AssetIn          uint64
		AssetOut         uint64
		LiquidationRatio types.Dec
	}

#UpdatePair:

	type MsgUpdatePairRequest struct {
		From             string
		Id               uint64
		LiquidationRatio types.Dec
	}


