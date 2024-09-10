# Call Contract Example

{% embed url="https://youtu.be/jXAaIAA2tz4" %}

## Parameters

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

## Request

This request reads the name of a contract.

{% tabs %}
{% tab title="curl" %}
```bash
curl --location --request POST "localhost:9680/callContract" \
--header 'Content-Type: application/json' \
--data-raw '{
    "contractAddress": "0xdac17f958d2ee523a2206206994597c13d831ec7",
    "functionName": "totalSupply",
    "params": [],
    "abi": [
      {
        "inputs": [],
        "name": "totalSupply",
        "outputs": [
          {
            "internalType": "uint256",
            "name": "",
            "type": "uint256"
          }
        ],
        "stateMutability": "view",
        "type": "function"
      }
    ],
    "chain": { "chainId": "1", "chainMetadata": { "chainName": "Ethereum", "nativeCurrency": { "name": "ETH", "symbol": "ETH", "decimals": 18 }, "rpcUrls": ["https://rpc.ankr.com/eth"] } }
}'

```
{% endtab %}

{% tab title="Unity" %}
```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Networking;

public class CallContract : MonoBehaviour
{
    void Start()
    {
        StartCoroutine(Call()); 
    }

    private IEnumerator Call()
    {
        string jsonString = "{ \"contractAddress\": \"0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48\", \"functionName\": \"totalSupply\", \"params\": [], \"abi\": [ { \"inputs\": [], \"name\": \"totalSupply\", \"outputs\": [ { \"internalType\": \"uint256\", \"name\": \"\", \"type\": \"uint256\" } ], \"stateMutability\": \"view\", \"type\": \"function\" } ], \"chain\": { \"chainId\": \"1\", \"chainMetadata\": { \"chainName\": \"Ethereum\", \"nativeCurrency\": { \"name\": \"ETH\", \"symbol\": \"ETH\", \"decimals\": 18 }, \"rpcUrls\": [\"https://rpc.ankr.com/eth\"] } } }";
        byte[] jsonBytes = System.Text.Encoding.UTF8.GetBytes(jsonString);

        UnityWebRequest request = new UnityWebRequest("localhost:9680/callContract", "POST");
        request.uploadHandler = new UploadHandlerRaw(jsonBytes);
        request.downloadHandler = new DownloadHandlerBuffer();
        request.SetRequestHeader("Content-Type", "application/json");

        yield return request.SendWebRequest();
        Debug.Log(request.error);
        string totalSupply = request.downloadHandler.text;
        Debug.Log(totalSupply);
    }
}

```
{% endtab %}

{% tab title="Unreal Engine C++" %}
```cpp
#include "NovaPlayUtils.h"
#include "Endpoints/SendContract.h"

void OnResponse(FString Response, int32 StatusCode)
{
	const bool bWasSuccessful = NovaPlayUtils::StatusCodeIsSuccess(StatusCode);

	UE_LOG(LogTemp, Display, TEXT("CallContract Success: %s"), bWasSuccessful ? "true" : "false");
	UE_LOG(LogTemp, Display, TEXT("CallContract Response: %s"), *Response);
}

int main(){
  UCallContract* GetAccountsInstance = UCallContract::CallContract(nullptr,
    "0xBA62BCfcAaFc6622853cca2BE6Ac7d845BC0f2Dc",
    "name",
    "",
    {},
    -1,
    "",
    5);
  GetAccountsInstance->GetOnCompletedDelegate().AddRaw(this, &OnResponse);
  GetAccountsInstance->Activate();
}
```
{% endtab %}
{% endtabs %}

## Response

The response value(s) of the smart contract method are mixed. If it returns a single value, it’s returned as is. If it has multiple return values they are returned as an object with properties and indices:&#x20;

{% tabs %}
{% tab title="Response" %}
```
"FaucetToken"
```
{% endtab %}

{% tab title="Error" %}
Errors will have an HTTP response status 500-599

```json
{
  "message": "error description here"
}
```
{% endtab %}
{% endtabs %}
