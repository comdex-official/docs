#Messages

Below are the messages in the CDP module.


##CreateCDP
CreateCDP creates and stores a new CDP, adding collateral from the sender.

	type MsgCreateCDPRequest struct {
		Sender         string
		Collateral     types.Coin
		Debt           types.Coin
		CollateralType string
	}
	
Resulting changes:

- A new CDP is created, sender becomes the CDP owner.
- Collateral is taken from the sender and sent to the CDP module account.
- Principal stable coins are minted and sent to the sender.
- Equivalent amount of internal debt coins created and stored in CDP module account.

##DepositCollateral

Deposit adds collateral to a CDP in the form of a deposit. Collateral is taken from owner.


	type MsgDepositCollateralRequest struct {
		Owner          string
		Collateral     types.Coin
		CollateralType string
	}

Resulting Changes:

- Collateral is taken from the owner and sent to the CDP module account.
- The depositor's Deposit Collateral struct is updated, or a new one created.

##WithdrawCollateral

Withdraw removes collateral from a vault, provided it does not put the CDP under the liquidation ratio.


	type MsgWithdrawCollateralRequest struct {
		Owner          string
		Collateral     types.Coin
		CollateralType string
	}
	
State Changes:

- Collateral assets are sent from the vault to the owner.

##DrawDebt
DrawDebt creates debt in a CDP, minting a new stable asset which is sent to the owner.


	type MsgDrawDebtRequest struct {
		Owner          string
		CollateralType string
		Debt           types.Coin
	}

Resulting Changes:

- Mint Principal coins and send them to the owner.
- Mint equal amount of internal debt coins.

	
##RepayDebt
RepayDebt repays the debt by returning the minted asset to the vault, at which point it will be burned, and the provided collateral is unlocked.


	type MsgRepayDebtRequest struct {
		Owner          string
		CollateralType string
		Debt           types.Coin
	}
	
Resulting Changes:

- Burn minted assets an equal amount of internal debt coins.
- Decrements the total principal for debt.
- If the debt is completely repaid, the collateral is returned to depositors.

##Liquidate

During the liquidation, the collaterals locked in the vault, equivalent in value to the outstanding debt & fees, are auctioned in exchange for the borrowed asset and burned to close the debt position. Comdex then returns any collateral remaining over and above the auctioned sum to the minter of the synthetic asset.

	type MsgLiquidateCDPRequest struct {
		Owner          string
		CollateralType string
	}

Resulting Changes:

- Liquidation ratio is validated.
- CDP's deposits are seized and used to start an Auction to recover the CDP's outstanding borrowed funds.
- CDP is deleted from the store.

