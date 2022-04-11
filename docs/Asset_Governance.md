#Governance

Below are the various governance proposals available for the asset module that trigger state changes.

## AddAssetsProposal:
NewAddAssetsProposal adds new Assets.

	type AddAssetsProposal struct {
		Title       string
		Description string
		Assets      []Asset
	}

Resulting changes:

- New Assets are created.
	
## UpdateAssetProposal:
UpdateAssetProposal updates the existing Asset.

	type UpdateAssetProposal struct {
		Title       string 
		Description string 
		Asset       Asset
	}

Resulting changes:

- An existing Asset is updated.	
	

## AddPairsProposal:
AddPairsProposal adds new asset pairs through the governance proposals.

	type AddPairsProposal struct {
		Title       string 
		Description string 
		Pairs       []Pair
	}
	
Resulting changes:

- New Pairs are added with AssetIn as the user provided asset.

## UpdatePairProposal:
UpdatePairProposal updates an existing asset pair.

	type UpdatePairProposal struct {
		Title       string 
		Description string 
		Pair        Pair
	}

Resulting changes:

- If any changes in Liquidation Ratio, the Asset pairs are updated accordingly.

