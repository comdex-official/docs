#Messages

Below are the messages in the Vault module.


##CreateRequest
CreateRequest creates and stores a new Vault, adding collateral from the sender.

	type MsgCreateRequest struct {
		From      string
		PairID    uint64
		AmountIn  types.Int
		AmountOut types.Int
	}
	
Resulting changes:

- A new Vault is created, sender becomes the Vault owner.
- Collateral is taken from the sender and sent to the Vault module account.
- Principal stable coins are minted and sent to the sender.
- Equivalent amount of internal debt coins created and stored in Vault module account.

##DepositRequest

Deposit adds collateral to a Vault in the form of a deposit. Collateral is taken from owner.


	type MsgDepositRequest struct {
		From   string
		ID     uint64
		Amount types.Int
	}

Resulting Changes:

- Collateral is taken from the owner and sent to the Vault module account.
- The depositor's Deposit Collateral struct is updated, or a new one created.

##WithdrawRequest

Withdraw removes collateral from a vault, provided it does not put the Vault under the liquidation ratio.


	type MsgWithdrawRequest struct {
		From   string
		ID     uint64
		Amount types.Int
	}
	
State Changes:

- Collateral assets are sent from the vault to the owner.

##DrawRequest
DrawDebt creates debt in a Vault, minting a new stable asset which is sent to the owner.


	type MsgDrawRequest struct {
		From   string
		ID     uint64
		Amount types.Int
	}

Resulting Changes:

- Mint Principal coins and send them to the owner.
- Mint equal amount of internal debt coins.

	
##RepayRequest
RepayDebt repays the debt by returning the minted asset to the vault, at which point it will be burned, and the provided collateral is unlocked.


	type MsgRepayRequest struct {
		From   string
		ID     uint64
		Amount types.Int
	}
	
Resulting Changes:

- Burn minted assets an equal amount of internal debt coins.
- Decrements the total principal for debt.
- If the debt is completely repaid, the collateral is returned to depositors.

##CloseRequest

During the liquidation, the collaterals locked in the vault, equivalent in value to the outstanding debt & fees, are auctioned in exchange for the borrowed asset and burned to close the debt position. Comdex then returns any collateral remaining over and above the auctioned sum to the minter of the synthetic asset.

	type MsgCloseRequest struct {
		From string
		ID   uint64
	}

Resulting Changes:

- Liquidation ratio is validated.
- Vault's deposits are seized and used to start an Auction to recover the Vault's outstanding borrowed funds.
- Vault is deleted from the store.

