#State

##CDP
A CDP represents a debt position owned by an address. It has a collateral type and records the debt that has been drawn and how much fees should be repaid.

Only the owner can draw or repay the debt, but anyone can deposit collateral to a CDP. Deposits are scoped per address and are recorded separately in Deposit types. Depositors can withdraw their collateral provided it does not put the CDP below the liquidation ratio.

The CDP's collateral is always equal to the total of the deposits.

	type CDP struct {
		Id         uint64
		Owner      string
		Type       string
		Collateral types.Coin
		Debt       types.Coin
	}

