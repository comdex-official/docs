#State
For detail on the state tracked by the cdp module see the types package. In particular keys.go describes how state is stored in the key-value store.

#CDP
A CDP is a struct representing a debt position owned by one address. It has one collateral type and records the debt that has been drawn and how much fees should be repaid.

Only an owner is authorized to draw or repay debt, but anyone can deposit collateral to a CDP. Deposits are scoped per address and are recorded separately in Deposit types. Depositors are free to withdraw their collateral provided it does not put the CDP below the liquidation ratio.

The CDP's collateral always equal to the total of the deposits.

	type CDP struct {
		Id         uint64
		Owner      string
		Type       string
		Collateral types.Coin
		Debt       types.Coin
	}
	

#Deposit
A Deposit is a struct recording collateral added to a CDP by one address. The address only has authorization to change their deposited amount (provided it does not put the CDP below the liquidation ratio).
