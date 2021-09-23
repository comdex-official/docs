#Messages

Below various messages are sent to the oracle module which trigger state changes detailed below.

##AddMarket:

	type MsgAddMarketRequest struct {
		From     string
		Symbol   string
		ScriptID uint64
		Id       uint64
	}


##UpdateMarket:
	
	type MsgupdateMarketRequest struct {
		From     string
		Symbol   string
		ScriptID uint64
	}

	
##FetchPrice:

	type MsgFetchPriceRequest struct {
		From             string
		SourcePort       string
		SourceChannel    string
		TimeoutHeight    types.Height
		TimeoutTimestamp uint64
		Symbols          []string
		ScriptID         uint64
		FeeLimit         types.Coins
		PrepareGas       uint64
		ExecuteGas       uint64
	}
	

	
