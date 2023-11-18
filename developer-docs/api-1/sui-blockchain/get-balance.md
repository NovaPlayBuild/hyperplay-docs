# Get Balance

## Request

Returns the balance of given account address in the smallest unit.

There are two params

* `chain` includes: `mainnet` `testnet` `devnet` `localnet`
* `address` of wallet

{% tabs %}
{% tab title="curl" %}
```bash
curl --location 'localhost:9680/sui/getBalance' \
--header 'Content-Type: application/json' \
--data '{
    "chain": "testnet",
    "address": "0xed272a655dcca880aeab1f89bdc8185d4049ab7f9ea72fd6a04153d0239a15f8"
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
        string jsonString = "{ \"chain\": \"testnet\", \"address\": \"0xed272a655dcca880aeab1f89bdc8185d4049ab7f9ea72fd6a04153d0239a15f8\" }";
        
        byte[] jsonBytes = System.Text.Encoding.UTF8.GetBytes(jsonString);

        UnityWebRequest request = new UnityWebRequest("localhost:9680/sui/getBalance", "POST");
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

Balance will be in mist.

{% tabs %}
{% tab title="First Tab" %}
```
2769926164
```
{% endtab %}

{% tab title="Error" %}
```json
{
    "message": "error description here"
}
```
{% endtab %}
{% endtabs %}

