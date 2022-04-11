# State

## CollateralAuction
The CollateralAuction struct creates a record for all the bids and tracks them. It follows if the offer is active or not and keeps track of the bidder. A bid is active for 6 hours from the time initialized, and the user with the highest bid gets the collateral.

    type CollateralAuction struct {
	    Id                  uint64                                        
	    LockedVaultId       uint64                                       
	    AuctionedCollateral github_com_cosmos_cosmos_sdk_types.Coin       
	    DiscountQuantity    github_com_cosmos_cosmos_sdk_types.Coin       
	    ActiveBiddingId     uint64                                        
	    Bidder              github_com_cosmos_cosmos_sdk_types.AccAddress 
	    Bid                 github_com_cosmos_cosmos_sdk_types.Coin       
	    MinBid              github_com_cosmos_cosmos_sdk_types.Coin      
	    MaxBid              github_com_cosmos_cosmos_sdk_types.Coin      
	    EndTime             time.Time                                   
	    Pair                types1.Pair                                   
	    BiddingIds          []uint64                                   
    }
