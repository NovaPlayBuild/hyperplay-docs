---
description: Make any JSON-RPC call with this endpoint.
---

# RPC Endpoint

## JSON-RPC Documentation

Ethereum: [https://ethereum.org/en/developers/docs/apis/json-rpc/](https://ethereum.org/en/developers/docs/apis/json-rpc/)

MetaMask: [https://docs.metamask.io/guide/rpc-api.html#table-of-contents](https://docs.metamask.io/guide/rpc-api.html#table-of-contents)

Polygon: [https://wiki.polygon.technology/docs/edge/get-started/json-rpc-commands/](https://wiki.polygon.technology/docs/edge/get-started/json-rpc-commands/)

For other EVM chains, check with their own developer docs.

## POST `localhost:9680/rpc`

### Parameters

`request` - `Object` used in the JSON-rpc call. See your chain's developer docs for the specific format.

`chain` - `Object` used to ensure the user is on the correct chain (follows the [MetaMask specification](https://docs.metamask.io/guide/rpc-api.html#unrestricted-methods))

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

`Object` - See your chain's developer documentation for more details
