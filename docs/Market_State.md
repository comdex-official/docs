# State

## Market

A Market is a struct that adds the latest price fetched from the oracles to a particular asset and the oracle script Id used to bring the price.
	
	type Market struct {
		Symbol   string 
		ScriptID uint64 
		Rates    uint64 
	}
