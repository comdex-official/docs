# Messages
Below are various messages are sent to the Liquidity module that triggers state changes detailed below.


## MsgBondPoolTokens
    type MsgBondPoolTokens struct {
	    UserAddress string 
	    PoolId      uint64
	    PoolCoin    types.Coin
    }

## MsgUnbondPoolTokens

    type MsgUnbondPoolTokens struct {
	    UserAddress string 
	    PoolId      uint64
	    PoolCoin    types.Coin
    }