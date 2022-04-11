# Messages

Below are various messages are sent to the Auction module that triggers state changes detailed below.

## MsgPlaceBidRequest
MsgPlaceBidRequest creates a bid as the user enters the bid amount.

    type MsgPlaceBidRequest struct {
	    AuctionId uint64    
	    Bidder    string    
	    Amount    types.Coin 
    }

Resulting changes:

- The user with the highest bid wins an auction, and then the collateral is transferred to its account after the bidding ends.
