# Governance

Below are the various governance proposals available for the Bandoracle module that trigger state changes.

## AddAssetsProposal:
NewAddAssetsProposal adds new Assets.

    type FetchPriceProposal struct {
	    Title       string
	    Description string
	    FetchPrice  MsgFetchPriceData
    }

Resulting changes:

- After the proposal passes, packets are relayed from our chain to the band chain network through relayers. After successfully fetching prices through the oracles, the prices are being mappped in the market module.