# OreoWallet Provider Api

OreoWallet injects the provider API into websites visited by its users using the window.ironfish provider object. You can use the provider properties and methods in your dapp.

## Properties

### window.ironfish.isOreoWallet

This property is `true` if the user has OreoWallet installed.

## Methods

### isConnected()

Return `true` if the provider is connect to current chain.

### getAccount()

Return `ViewAccount` of the connected wallet.

### getNetwork()

Return `Network` of current wallet (mainnet or testnet).

### getBalances(address: string)

Return `Balance[]` of cureent connected wallet.

### getOrescriptions(address: string)

Return `Orescriptions[]` of cureent connected wallet.

### sendNativeCoin({toAddress: string, amount: BigInt, memo?: string, fee?: string})

Send native IRON coin to others, return `hash` of submitted transaction if succeed.

### sendAsset({toAddress: string, amount: BigInt, assetId: string, memo?: string, fee?: string})

Send user created token to others, return `hash` of submitted transaction if succeed.

### mintAsset({value: string, assetId?: string, name?: string, metadata?: string, fee?: string})

Create new asset(token), return `hash` of submitted transaction if succeed.

### burnAsset({value: string, assetId: string, fee?: string})

Burn owned asset(token/coin), return `hash` of submitted transaction if succeed.

<!-- TBD
### signMessage(message: string)

Return signed in hex string. -->

## Special Thanks

Thanks to the MetaMask team for their contributions to the browser extension wallet community, OreoWallet relies heavily on their contributions.