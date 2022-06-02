# Messages
Below are various messages are sent to the liquidation module that triggers state changes detailed below.

## WhitelistAppId
    
    type WhitelistAppId struct {
    AppMappingId uint64
    From         string
    }

## RemoveWhitelistAppId

    type RemoveWhitelistAppId struct {
        AppMappingId uint64
        From         string
    }
