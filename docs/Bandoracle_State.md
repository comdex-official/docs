# State

Below is the message sent to fetch price from the Bandchain Oracle.

## MsgFetchPriceData
	
    type MsgFetchPriceData struct {
	    Creator        string                                   
	    OracleScriptID uint64                                   
	    SourceChannel  string                                   
	    Calldata       FetchPriceCallData                      
	    AskCount       uint64                                   
	    MinCount       uint64                                   
	    FeeLimit       github_com_cosmos_cosmos_sdk_types.Coins 
	    RequestKey     string                                   
	    PrepareGas     uint64                                   
	    ExecuteGas     uint64                                   
	    ClientID       string
    }