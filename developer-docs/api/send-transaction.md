# Send Transaction

## Request

Sends coin.

Parameters

- `from` : Account to send from
- `to`: Account to send to
- `value`: Amount in smallest unit such as wei
- `data` : (optional)

{% tabs %}
{% tab title="curl" %}

```bash
curl --location --request POST "localhost:9680/rpc" \
--header 'Content-Type: application/json' \
--data-raw '{
    "request": {
        "method": "eth_sendTransaction",
        "params": [{
            "from": "0x638105AA1B69406560f6428aEFACe3DB9da83c64",
            "to": "0x638105AA1B69406560f6428aEFACe3DB9da83c64",
            "value": "123000000000000",
            "data": ""
        }]
    },
    "chain": {
        "chainId": "1"
    }
}'
```

{% endtab %}

{% tab title="Unity" %}

```csharp
using System.Collections;
using UnityEngine;
using UnityEngine.Networking;

public class SendTransaction: MonoBehaviour
{
    void Start()
    {
        StartCoroutine(Send());
    }

    private IEnumerator Send()
    {
        string jsonString = "{ \"request\": { \"method\": \"eth_sendTransaction\", \"params\": [{ \"from\": \"0x638105AA1B69406560f6428aEFACe3DB9da83c64\", \"to\": \"0x638105AA1B69406560f6428aEFACe3DB9da83c64\", \"value\": \"123000000000000\", \"data\": \"\" }] }, \"chain\": { \"chainId\": \"5\" } }";
        byte[] jsonBytes = System.Text.Encoding.UTF8.GetBytes(jsonString);

        UnityWebRequest request = new UnityWebRequest("localhost:9680/rpc", "POST");
        request.uploadHandler = new UploadHandlerRaw(jsonBytes);
        request.downloadHandler = new DownloadHandlerBuffer();
        request.SetRequestHeader("Content-Type", "application/json");

        yield return request.SendWebRequest();
        Debug.Log(request.error);
        Debug.Log(request.downloadHandler.text);
    }
}

```

{% endtab %}
{% tab title="Unreal Engine C++" %}

```cpp
#include "NovaPlayUtils.h"
#include "Endpoints/RpcCall.h"

void OnRpcResponse(FString Response, int32 StatusCode)
{
	const bool bWasSuccessful = NovaPlayUtils::StatusCodeIsSuccess(StatusCode);

	UE_LOG(LogTemp, Display, TEXT("Rpc eth_sendTransaction Success: %s"), bWasSuccessful ? "true" : "false");
	UE_LOG(LogTemp, Display, TEXT("Rpc eth_sendTransaction Response: %s"), *Response);
}

int main(){
   const FString request("{\"method\": \"eth_sendTransaction\",\"params\": [{\"from\": \"0x638105AA1B69406560f6428aEFACe3DB9da83c64\",\"to\": \"0x638105AA1B69406560f6428aEFACe3DB9da83c64\",\"value\": \"123000000000000\",\"data\": \"\"}]}")

	URpcCall* RpcCallInstance = URpcCall::RpcCall(nullptr,
		request,
		1);
	RpcCallInstance->GetOnCompletedDelegate().AddRaw(this, &OnRpcResponse);
	RpcCallInstance->Activate();
}
```

{% endtab %}
{% endtabs %}

## Response

The transaction hash

{% tabs %}
{% tab title="Response" %}

```
0xa27e68e665f4bafe045dacdf2d0ace14617c02f20325d081e98dd5e3413ecece
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
