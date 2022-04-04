#State

## LockedVault

    type LockedVault struct {
	    LockedVaultId                uint64                                  
	    OriginalVaultId              uint64                                  
	    PairId                       uint64                                  
	    Owner                        string                                  
	    AmountIn                     github_com_cosmos_cosmos_sdk_types.Int 
	    AmountOut                    github_com_cosmos_cosmos_sdk_types.Int 
	    Initiator                    string                                  
	    IsAuctionComplete            bool                                   
	    IsAuctionInProgress          bool                                    
	    CrAtLiquidation              github_com_cosmos_cosmos_sdk_types.Dec  
	    CurrentCollaterlisationRatio github_com_cosmos_cosmos_sdk_types.Dec
	    CollateralToBeAuctioned      github_com_cosmos_cosmos_sdk_types.Dec
	    LiquidationTimestamp         time.Time
	    SellOffHistory               []string
    }