---
description: Interact easily with Smart Contracts with this endpoint
---

# Send Contract Endpoint

## POST `localhost:9680/sendContract`

### Parameters

* `contractAddress` - `string` Contract address to interact with
* `functionName` - `string` Smart contract function to interact with
* `abi` - `Array<AbiItem>` (Optional) ABI of the contract to call
* `params` - `Array<string>` (Optional) Params to call the smart contract function with
* `valueInWei` - `string` (Optional) Amount of wei to send
* `gasLimit` - `string` (Optional) Gas limit for the function call
* `chain` - `Object` used to ensure the user is on the correct chain (follows the [MetaMask specification](https://docs.metamask.io/guide/rpc-api.html#unrestricted-methods))
  * `chainId` - `string` Base 10 string matching the chain id on [Chainlist](https://chainlist.org/)
  * `chainMetadata` (Optional) - `Object` used to add the chain if the user does not have the chain added to their wallet
    * `chainName` - `string`&#x20;
    * `nativeCurrency` - `Object`
      * `name` - `string` is the currency's name
      * `symbol` - `string` 2-6 characters long symbol for the chain
      * `decimals` - `18`
    * `rpcUrls` - `Array<string>` is an array of rpc node urls that can be used to make requests. We recommend selecting a few from the listing on [Chainlist](https://chainlist.org/)
    * `blockExplorerUrls` (Optional) - `Array<string>` is an array of block explorers that can be used with the chain
    * `iconUrls` (Optional) - `Array<string>` is currently unused by MetaMask

### Returns

`string` - transaction hash&#x20;
