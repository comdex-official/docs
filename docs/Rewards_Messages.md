#Messages

## MsgDepositMintingRewardAmountRequest
    type MsgDepositMintingRewardAmountRequest struct {
	    MintingRewardId uint64    `protobuf:"varint,1,opt,name=minting_reward_id,json=mintingRewardId,proto3" json:"minting_reward_id,omitempty"`
	    StartTimestamp  time.Time `protobuf:"bytes,2,opt,name=start_timestamp,json=startTimestamp,proto3,stdtime" json:"start_timestamp" yaml:"start_timestamp"`
	    From            string    `protobuf:"bytes,3,opt,name=from,proto3" json:"from,omitempty"`
    }

## MsgUpdateMintRewardStartTimeRequest

    type MsgUpdateMintRewardStartTimeRequest struct {
	    MintingRewardId   uint64    `protobuf:"varint,1,opt,name=minting_reward_id,json=mintingRewardId,proto3" json:"minting_reward_id,omitempty"`
	    NewStartTimestamp time.Time `protobuf:"bytes,2,opt,name=new_start_timestamp,json=newStartTimestamp,proto3,stdtime" json:"new_start_timestamp" yaml:"new_start_timestamp"`
	    From              string    `protobuf:"bytes,3,opt,name=from,proto3" json:"from,omitempty"`
    }