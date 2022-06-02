# Messages

Below are various messages are sent to the LOCEKR module that triggers state changes detailed below.

## MsgCreateLockerRequest
    type MsgCreateLockerRequest struct {
        Depositor    string                                 
        Amount       github_com_cosmos_cosmos_sdk_types.Int 
        AssetId      uint64                                 
        AppMappingId uint64                                 
    }

## MsgAddWhiteListedAssetRequest

    type MsgAddWhiteListedAssetRequest struct {
        From         string 
        AppMappingId uint64 
        AssetId      uint64 
    }

## MsgDepositAssetRequest
    type MsgDepositAssetRequest struct {
        Depositor    string                                 
        LockerId     string                                 
        Amount       github_com_cosmos_cosmos_sdk_types.Int
        AssetId      uint64                                 
        AppMappingId uint64                                 
    } 

## MsgWithdrawAssetRequest
    type MsgWithdrawAssetRequest struct {
        Depositor    string                              
        LockerId     string                                
        Amount       github_com_cosmos_cosmos_sdk_types.Int 
        AssetId      uint64                       
        AppMappingId uint64                             
    }
