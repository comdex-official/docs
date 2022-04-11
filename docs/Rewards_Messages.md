#Messages
Below various messages are sent to the rewards module which trigger state changes detailed below.

## MsgDepositMintingRewardAmountRequest
    type MsgDepositMintingRewardAmountRequest struct {
	    MintingRewardId uint64    
	    StartTimestamp  time.Time 
	    From            string    
    }

## MsgUpdateMintRewardStartTimeRequest

    type MsgUpdateMintRewardStartTimeRequest struct {
	    MintingRewardId   uint64   
	    NewStartTimestamp time.Time 
	    From              string 
    }
