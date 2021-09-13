#State

Below various messages are sent to the asset module which trigger state changes detailed below.

#Market
	
	type Market struct {
		Symbol   string
		ScriptID uint64
	}

#Calldata
	
	type Calldata struct {
		Symbols    []string
		Multiplier uint64
	}
	
#Result

	type Result struct {
		Rates []uint64
	}
