#Messages

Users can submit various messages to the cdp module which trigger state changes detailed below.


#CreateCDPRequest
CreateCDP sets up and stores a new CDP, adding collateral from the sender, and drawing Principle debt.

	type MsgCreateCDPRequest struct {
		Sender         string
		Collateral     types.Coin
		Debt           types.Coin
		CollateralType string
	}
	
State changes:

1. a new CDP is created, Sender becomes CDP owner
2. collateral taken from Sender and sent to cdp module account, new Deposit created
3. Principal stable coins are minted and sent to Sender
4. equal amount of internal debt coins created and stored in cdp module account

#DepositCollateral

Deposit adds collateral to a CDP in the form of a deposit. Collateral is taken from Depositor


	type MsgDepositCollateralRequest struct {
		Owner          string
		Collateral     types.Coin
		CollateralType string
	}

State Changes:

1. Collateral taken from depositor and sent to cdp module account
2. the depositor's Deposit struct is updated or a new one created
3. cdp fees are updated

#WithdrawCollateral

Withdraw removes collateral from a CDP, provided it would not put the CDP under the liquidation ratio. Collateral is removed from one deposit only.


	type MsgWithdrawCollateralRequest struct {
		Owner          string
		Collateral     types.Coin
		CollateralType string
	}
	
State Changes:

1. Collateral coins are sent from the cdp module account to Depositor
2. Collateral amount of coins subtracted from the Deposit struct. If the amount is now zero, the struct is deleted

#DrawDebt
DrawDebt creates debt in a CDP, minting new stable asset which is sent to the sender.


	type MsgDrawDebtRequest struct {
		Owner          string
		CollateralType string
		Debt           types.Coin
	}

State Changes:

1. mint Principal coins and send them to Sender, updating the CDP's Principal field
2. mint equal amount of internal debt coins and store in the module account
3. increment total principal for principal denom

	
#RepayDebt
RepayDebt removes some debt from a CDP and burns the corresponding amount of stable asset from the sender. If all debt is repaid, the collateral is returned to depositors and the cdp is removed from the store


	type MsgRepayDebtRequest struct {
		Owner          string
		CollateralType string
		Debt           types.Coin
	}
	
State Changes:

1. burn Payment coins taken from Sender, updating the CDP by reducing Principal field by Paymment
2. burn an equal amount of internal debt coins
3. decrement total principal for payment denom
4. if fees and principal are zero, return collateral to depositors and delete the CDP struct:
5. For each deposit, send coins from the cdp module account to the depositor, and delete the deposit struct from store.

#Liquidate

Liquidate enables Keepers to liquidate a Borrower's CDP. If the CDP is below its Loan-to-Value obligations, the CDP's deposits are seized: a small percentage of the seized funds are sent to the Keeper with the rest auctioned off to recover the CDP's outstanding borrowed amount. Any deposited funds leftover that weren't needed to cover the Borrower's debts are returned to the Borrower.

	type MsgLiquidateCDPRequest struct {
		Owner          string
		CollateralType string
	}

State Changes:

1. the CDP's outstanding interest is synchronized so that the deposit and borrow amount are accurate
2. the liquidation attempt is validated by comparing the CDP's current collateralization ratio to its liquidation ratio
3. the Keeper is paid out a percentage of the liquidated position; the exact percentage is specified in the module's params
4. the CDP's deposits are seized and used to start an Auction to recover the CDP's outstanding borrowed funds
5. the module's TotalPrincipal for the CDP's collateral type is decremented by the CDP's Principal
6. the CDP is deleted from the store and removed from the liquidation index

