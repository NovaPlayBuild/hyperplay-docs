# Personal Sign

## Request

Signs message with wallet

There are two params

- The string to sign
- The address of the signer

{% tabs %}
{% tab title="curl" %}

```bash
curl --location --request POST "localhost:9680/rpc" \
--header 'Content-Type: application/json' \
--data-raw '{
    "request": {
        "method": "personal_sign",
        "params": ["helloo!", "0x638105aa1b69406560f6428aeface3db9da83c64"]
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

public class PersonalSign : MonoBehaviour
{
    void Start()
    {
        StartCoroutine(Sign());
    }

    private IEnumerator Sign()
    {
        string jsonString = "{ \"request\": { \"method\": \"personal_sign\", \"params\": [\"helloo!\", \"0x638105aa1b69406560f6428aeface3db9da83c64\"] }, \"chain\": { \"chainId\": \"5\" } }";
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
#include "HyperPlayUtils.h"
#include "Endpoints/RpcCall.h"

void OnRpcResponse(FString Response, int32 StatusCode)
{
	const bool bWasSuccessful = HyperPlayUtils::StatusCodeIsSuccess(StatusCode);

	UE_LOG(LogTemp, Display, TEXT("Rpc Personal Sign Success: %s"), bWasSuccessful ? "true" : "false");
	UE_LOG(LogTemp, Display, TEXT("Rpc Personal Sign Response: %s"), *Response);
}

int main(){
   const FString request("{\"method\": \"personal_sign\",\"params\": [\"helloo!\", \"0x638105aa1b69406560f6428aeface3db9da83c64\"]}")

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

{% tabs %}
{% tab title="Response" %}

```
0x248664217cb1dfb3fa5fad290c053c9aaab8812d0fe9d7ad493b5857b4bc43e93efa51c1fdedff937d0b0919f8f6326c511e688a3fce631cd309b524f518bd081c
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
