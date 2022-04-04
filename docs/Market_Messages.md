# Messages

Below are various messages are sent to the market module that triggers state changes detailed below.

## AddMarket:
AddMarket creates the raw price for the asset for this market.

	type MsgAddMarketRequest struct {
		From     string
		Symbol   string
		ScriptID uint64
		Id       uint64
	}

