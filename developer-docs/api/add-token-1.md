# RPC Raw

## Request

HyperPlay’s API includes `chainId` in the request body for better UX and security.

rpcRaw

* Does not require `chainId`
* Allows multiple RPC calls

{% tabs %}
{% tab title="curl" %}
```bash
curl --location 'localhost:9680/rpcRaw' \
--header 'Content-Type: application/json' \
--data '[
    {
      "method": "eth_accounts"
    },
    {
      "method": "eth_getBalance",
      "params": ["0x87885AaEEdED51C7e3858a782644F5d89759f245", "latest"]
    }
]
'
```
{% endtab %}

{% tab title="Unity" %}
```csharp
using System.Collections;
using UnityEngine;
using UnityEngine.Networking;

public class RawRpc: MonoBehaviour
{
    void Start()
    {
        StartCoroutine(Send());
    }

    private IEnumerator Send()
    {
        string jsonString = "[ { \"method\": \"eth_accounts\" }, { \"method\": \"eth_getBalance\", \"params\": [\"0x87885AaEEdED51C7e3858a782644F5d89759f245\", \"latest\"] } ]";
        byte[] jsonBytes = System.Text.Encoding.UTF8.GetBytes(jsonString);

        UnityWebRequest request = new UnityWebRequest("localhost:9680/rpcRaw", "POST");
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
{% endtabs %}

## Response

{% tabs %}
{% tab title="Response" %}
```
[
    {
        "result": [
            "0x638105AA1B69406560f6428aEFACe3DB9da83c64"
        ],
        "id": -1,
        "jsonrpc": "2.0"
    },
    {
        "result": "0x5ff309feea9f67c21",
        "id": -1,
        "jsonrpc": "2.0"
    }
]
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
