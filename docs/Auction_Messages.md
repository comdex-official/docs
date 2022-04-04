# Messages

Below are various messages are sent to the Auction module that triggers state changes detailed below.

## MsgPlaceBidRequest

    type MsgPlaceBidRequest struct {
	    AuctionId uint64    
	    Bidder    string    
	    Amount    types.Coin 
    }