#Messages
Below various messages are sent to the rewards module which trigger state changes detailed below.

## MsgMintNewTokensRequest

    type MsgMintNewTokensRequest struct {
        From         string 
        AppMappingId uint64
        AssetId      uint64 
    }