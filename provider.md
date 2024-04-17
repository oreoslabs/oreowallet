# OreoWallet Provider Api

OreoWallet injects the provider API into websites visited by its users using the window.ironfish provider object. You can use the provider properties and methods in your dapp.

## Properties

### window.ironfish

```javascript
function getProvider() {
  const provider = window.ironfish
  if (!provider) {
    throw new Error("Install OreoWallet first.");
  }
  return provider;
}
```
This property is `true` if the user has OreoWallet installed.

## Methods

### connect()

```javascript
/**
 * Connect to the provider
 * @returns {string} return the connected address
 */
async function connect() {
	const provider = getProvider();
	await provider.connect();
	return provider.address;
}
```

### disconnect()

```javascript
/**
 * Disconnect to the provider
 * @returns {boolean} Whether the disconnection is successfully closed
 */
async function disconnect() {
	const provider = getProvider();
	return await provider.disconnect();
}
```

### getBalances()

```javascript
/**
 * Get balances of the connected address
 * @returns {Promise<Array<{balance: string, assetId: string, assetName: string}>>} A promise that resolves with an array of balance objects.
 */
async function getBalances() {
	const provider = getProvider();
	return await provider.getBalances();
}
```

### getTransactionInfo(tx: string)

```javascript
/**
 * Represents the status of a transaction.
 * @typedef {Object} TxStatus
 * @property {string} hash - The transaction hash.
 * @property {string} fee - The transaction fee.
 * @property {string} type - The type of the transaction.
 * @property {string} status - The status of the transaction.
 * @property {number} blockSequence - The block sequence number.
 * @property {string} timestamp - The timestamp of the transaction.
 * @property {AssetBalanceDelta[]} assetBalanceDeltas - Array of asset balance changes.
 */

/**
 * Represents a change in asset balance.
 * @typedef {Object} AssetBalanceDelta
 * @property {string} assetId - The ID of the asset.
 * @property {string} delta - The change in balance.
 * @property {string} assetName - The name of the asset.
 */

/**
 * Retrieves the transaction status.
 * @returns {Promise<TxStatus>} A promise that resolves with transaction status object.
 */
async function getTransactionInfo(txId: string) {
	const provider = getProvider();
	return await provider.getTransaction(txId);
}
```

### getTransactions()

```javascript
/**
 * Retrieves an array of the connected address's transactions' status.
 * @returns {Promise<TxStatus[]>} A promise that resolves with an array of transaction status objects.
 */
async function getAddressTransactions() {
	const provider = getProvider();
	return await provider.getTransactions();
}
```

### getOreos

```javascript
/**
 * Get Orescriptions NFT of the connected address
 * @returns {Promise<Array<{tick: string, tickIndex: number, data: string, removedByOwner: boolean, assetId: string, url: string}>>} A promise that resolves with an array of Oreo objects.
 */
async function getOreos() {
	const provider = getProvider();
	return await provider.getOreos();
}
```

### sendTransaction(txInfo)

```javascript
/**
 * Send a transaction using the provided transaction information.
 * @param {Object} txInfo - The transaction information.
 * @param {string} txInfo.from - The sender's address.
 * @param {string} txInfo.to - The recipient's address.
 * @param {string} txInfo.value - The amount of the asset to send.
 * @param {string} txInfo.memo - A memo for the transaction.
 * @param {string} txInfo.assetId - The ID of the asset being sent.
 * @returns {Promise<string>} A promise that resolves with the transaction result.
 */
async function sendTransaction(txInfo) {
	const provider = getProvider();
	return await provider.sendTransaction(txInfo);
}
```

### generalTransaction(txInfo)

```javascript
/**
 * Represents output part of the transaction.
 * @typedef {Object} OutPutParams
 * @property {string} publicAddress - The recipient's address.
 * @property {string} amount - The amount of the asset to send.
 * @property {string} memo - A memo for the transaction.
 * @property {string} assetId - The ID of the asset being sent.
 * @property {OutPutParams[]} outputs - Array of output.
 */

/**
 * Represents mint part of the transaction.
 * @typedef {Object} MintAssetParams
 * @property {string} value - The value of the asset to mint in the transaction.
 * @property {string} assetId - The ID of the asset being minted.
 * @property {string} metadata - The metadata info of the asset being minted.
 * @property {MintAssetParams[]} mints - Array of mint.
 */

/**
 * Represents burn part of the transaction.
 * @typedef {Object} BurnAssetParams
 * @property {string} value - The value of the asset to burn in the transaction.
 * @property {string} assetId - The ID of the asset being burned.
 * @property {BurnAssetParams[]} burns - Array of burn.
 */

/**
 * Send a transaction using the provided transaction information.
 * @param {Object} txInfo - The transaction information.
 * @param {string} txInfo.from - The sender's address.
 * @param {string} txInfo.fee - The transaction fee.
 * @param {string} txInfo.outputs - Array of output.
 * @param {string} txInfo.mints - Array of mint.
 * @param {string} txInfo.burns - Array of burn.
 * @returns {Promise<string>} A promise that resolves with the transaction result.
 */
async function generalTransaction(txInfo) {
	const provider = getProvider();
	return await provider.generalTransaction(txInfo);
}
```

## Special Thanks

Thanks to the MetaMask team for their contributions to the browser extension wallet community, OreoWallet relies heavily on their contributions.