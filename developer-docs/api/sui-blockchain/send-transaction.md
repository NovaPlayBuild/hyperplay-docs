# Send Transaction

## Request

Sends coin.

Parameters

* `chain` - `mainnet` `testnet` `devnet` `localnet`
* to - Account to send to
* `amount` - Amount in the smallest unit (mist)

{% tabs %}
{% tab title="curl" %}
```bash
curl --location 'localhost:9680/sui/sendTransaction' \
--header 'Content-Type: application/json' \
--data '{
    "chain": "testnet",
    "to": "0x78687cc53c07484da514ca3d024d06274c9d079def21ece23a553a17397014a6",
    "amount": "12345678"
}'
```
{% endtab %}

{% tab title="Unity" %}
```csharp
using System.Collections;
using UnityEngine;
using UnityEngine.Networking;

public class GetAccounts: MonoBehaviour
{
    void Start()
    {
        StartCoroutine(Accounts());
    }

    private IEnumerator Accounts()
    {
        string jsonString = "{ \"chain\": \"testnet\", \"to\": \"0x78687cc53c07484da514ca3d024d06274c9d079def21ece23a553a17397014a6\", \"amount\": \"12345678\" }";
        
        byte[] jsonBytes = System.Text.Encoding.UTF8.GetBytes(jsonString);

        UnityWebRequest request = new UnityWebRequest("localhost:9680/sui/sendTransaction", "POST");
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

The transaction hash

{% tabs %}
{% tab title="First Tab" %}
```html
f7FWpm3vJd8XHu3iRZQ4BF1uuRP6Y7ZAkAvJ8XnUiV3
```
{% endtab %}

{% tab title="Second Tab" %}
```json
{
  "message": "error description here"
}
```
{% endtab %}
{% endtabs %}
