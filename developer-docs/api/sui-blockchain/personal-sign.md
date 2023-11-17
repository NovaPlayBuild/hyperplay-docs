# Personal Sign

## Request

Signs message with wallet

Params

* The string to sign

{% tabs %}
{% tab title="curl" %}
```bash
curl --location 'localhost:9680/sui/personalSign' \
--header 'Content-Type: application/json' \
--data '{
    "message": "test"
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
        string jsonString = "{ \"message\": \"test\"}";
        
        byte[] jsonBytes = System.Text.Encoding.UTF8.GetBytes(jsonString);

        UnityWebRequest request = new UnityWebRequest("localhost:9680/sui/personalSign", "POST");
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
AKo3pNTj/jobYt1rWw03ZRY170boh6NzM/wPvVfD+FOrTbnLEDwUpejtnq4um3LHK1rR86w47ZFe4gfJNC9pUwscrlJddixEJXiCXQuZyjoZNw2uOGrjnafvrFeqC3WoGg==
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
