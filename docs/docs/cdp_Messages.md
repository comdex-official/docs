#Messages

Below are the messages in CDP module.


#CreateCDP
CreateCDP creates and stores a new CDP, adding collateral from the sender.

	type MsgCreateCDPRequest struct {
		Sender         string
		Collateral     types.Coin
		Debt           types.Coin
		CollateralType string
	}
	
Resulting changes:

1. A new CDP is created, Sender becomes CDP owner.
2. Collateral is taken from the Sender and sent to cdp module account.
3. Principal stable coins are minted and sent to Sender.
4. Equivalent amount of internal debt coins created and stored in cdp module account.

#DepositCollateral

Deposit adds collateral to a CDP in the form of a deposit. Collateral is taken from Owner.


	type MsgDepositCollateralRequest struct {
		Owner          string
		Collateral     types.Coin
		CollateralType string
	}

Resulting Changes:

1. Collateral taken from owner and sent to cdp module account.
2. The depositor's Deposit Collateral struct is updated or a new one created.

#WithdrawCollateral

Withdraw removes collateral from a vault, provided it does not put the CDP under the liquidation ratio.


	type MsgWithdrawCollateralRequest struct {
		Owner          string
		Collateral     types.Coin
		CollateralType string
	}
	
State Changes:

1. Collateral assets are sent from the vault to Owner.

#DrawDebt
DrawDebt creates debt in a CDP, minting new stable asset which is sent to the owner.


	type MsgDrawDebtRequest struct {
		Owner          string
		CollateralType string
		Debt           types.Coin
	}

Resulting Changes:

1. Mint Principal coins and send it to Owner.
2. Mint equal amount of internal debt coins.

	
#RepayDebt
RepayDebt repays the debt by returning the minted asset to the vault at which point it will be burned and the provided collateral is unlocked.


	type MsgRepayDebtRequest struct {
		Owner          string
		CollateralType string
		Debt           types.Coin
	}
	
Resulting Changes:

1. Burn minted asset an equal amount of internal debt coins.
2. Decrements the total principal for debt.
3. If debt is completely repayed, the collateral is returned to depositors.

#Liquidate

During the liquidation, the collaterals locked in the vault, equivalent in value to the outstanding debt & fees, are auctioned in exchange for the borrowed asset and burned to close the debt position. Comdex then returns any collateral remaining over and above the auctioned sum to the minter of the synthetic asset.

	type MsgLiquidateCDPRequest struct {
		Owner          string
		CollateralType string
	}

Resulting Changes:

1. Liquidation ratio is validated.
2. CDP's deposits are seized and used to start an Auction to recover the CDP's outstanding borrowed funds.
3. TotalPrincipal for the CDP's collateral type is decremented by the CDP's Principal.
4. CDP is deleted from the store.

