#Messages

Below various messages are sent to the oracle module which trigger state changes detailed below.

##AddMarket:
AddMarket creates the raw price for the asset for this market.

	type MsgAddMarketRequest struct {
		From     string
		Symbol   string
		ScriptID uint64
		Id       uint64
	}


##UpdateMarket:
Update the raw price for the asset for this market.
	
	type MsgupdateMarketRequest struct {
		From     string
		Symbol   string
		ScriptID uint64
	}

Resulting Changes:
- This replaces any previous price for that oracle.	


##FetchPrice:
FetchPrice fetches the price of an asset from the market.

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

