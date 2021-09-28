#Messages

Below various messages are sent to the asset module which trigger state changes detailed below.

##AddAsset:
AddAssetRequest creates new Asset.

	type MsgAddAssetRequest struct {
		From     string
		Name     string
		Denom    string
		Decimals int64
	}

Resulting changes:

- A new Asset is created, sender becomes the Asset owner.
	
##UpdateAsset:
UpdateAsset updates the existing Asset.

	type MsgUpdateAssetRequest struct {
		From     string
		Id       uint64
		Name     string
		Denom    string
		Decimals int64
	}

Resulting changes:

- An existing Asset is updated with the latest price.	
	

##AddPair:
AddPair creates a new asset pair.

	type MsgAddPairRequest struct {
		From             string
		AssetIn          uint64
		AssetOut         uint64
		LiquidationRatio types.Dec
	}
	
Resulting changes:

- AssetIn will be the user provided asset.
- CMDX will be AssetOut.

##UpdatePair:
UpdatePair updates an existing asset pair.

	type MsgUpdatePairRequest struct {
		From             string
		Id               uint64
		LiquidationRatio types.Dec
	}

Resulting changes:

- If any changes in price the Asset pairs are updated accordingly.

