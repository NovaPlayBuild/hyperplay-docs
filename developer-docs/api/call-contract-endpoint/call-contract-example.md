# Call Contract Example

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
    "params": "",
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
        string jsonString = "{ \"contractAddress\": \"0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48\", \"functionName\": \"totalSupply\", \"params\": \"\", \"abi\": [ { \"inputs\": [], \"name\": \"totalSupply\", \"outputs\": [ { \"internalType\": \"uint256\", \"name\": \"\", \"type\": \"uint256\" } ], \"stateMutability\": \"view\", \"type\": \"function\" } ], \"chain\": { \"chainId\": \"1\", \"chainMetadata\": { \"chainName\": \"Ethereum\", \"nativeCurrency\": { \"name\": \"ETH\", \"symbol\": \"ETH\", \"decimals\": 18 }, \"rpcUrls\": [\"https://rpc.ankr.com/eth\"] } } }";
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
#include "HyperPlayUtils.h"
#include "Endpoints/SendContract.h"

void OnResponse(FString Response, int32 StatusCode)
{
	const bool bWasSuccessful = HyperPlayUtils::StatusCodeIsSuccess(StatusCode);

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

The contract name

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
