#State

##Vault
A Vault represents a debt position owned by an address. It has a collateral type and records the debt that has been drawn and how much fees should be repaid.

Only the owner can draw or repay the debt, but anyone can deposit collateral to a Vault. Deposits are scoped per address and are recorded separately in Deposit types. Depositors can withdraw their collateral provided it does not put the Vault below the liquidation ratio.

The Vault's collateral is always equal to the total of the deposits.

	type Vault struct {
		ID        uint64
		PairID    uint64
		Owner     string
		AmountIn  types.Int
		AmountOut types.Int
	}	

