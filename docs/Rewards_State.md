#State

##MintingRewards

    type MintingRewards struct {
	    Id                   uint64                                        
	    AllowedCollateral    string                                        
	    AllowedCasset        string                                        
	    TotalRewards         github_com_cosmos_cosmos_sdk_types.Coin      
	    CassetMaxCap         uint64                                        
	    DurationDays         uint64                                        
	    IsActive             bool                                          
	    AvailableRewards     github_com_cosmos_cosmos_sdk_types.Coin       
	    Depositor            github_com_cosmos_cosmos_sdk_types.AccAddress 
	    StartTimestamp       time.Time                                     
	    EndTimestamp         time.Time                                     
	    MinLockupTimeSeconds uint64                                        
    }
