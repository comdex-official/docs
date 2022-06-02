# Messages

Below are various messages are sent to the Locking module that triggers state changes detailed below.

## MsgLockTokens

    type MsgLockTokens struct {
        Owner    string                                  
        Duration time.Duration                          
        Coin     github_com_cosmos_cosmos_sdk_types.Coin 
}

## MsgBeginUnlockingTokens

    type MsgBeginUnlockingTokens struct {
        Owner  string                                 
        LockId uint64                                  
        Coin   github_com_cosmos_cosmos_sdk_types.Coin 
    }