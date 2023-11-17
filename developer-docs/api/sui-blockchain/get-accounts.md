# Get Accounts

## Request

Get the user's currently selected address

Note that HyperPlay currently supports a single globally selected account during its connection flow. In the future, multiple account addresses will be supported.

{% tabs %}
{% tab title="curl" %}
```bash
curl --location --request POST 'localhost:9680/sui/getAccounts'
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
        string jsonString = "{}";
        byte[] jsonBytes = System.Text.Encoding.UTF8.GetBytes(jsonString);

        UnityWebRequest request = new UnityWebRequest("localhost:9680/sui/getAccounts", "POST");
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
["0xed272a655dcca880aeab1f89bdc8185d4049ab7f9ea72fd6a04153d0239a15f8"]
```
{% endtab %}

{% tab title="Error" %}

{% endtab %}
{% endtabs %}
