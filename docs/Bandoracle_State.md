# State

## MsgFetchPriceData
The MsgFetchPriceData struct saves all the necessary data required to get data from the Bandchain Oracle. FetchPriceData Packets are created and then relayed through the relayers to get the price back from the Bandchain Oracle.
	
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
