# Get Object

## Request

Similar to [call contract](../call-contract-example.md) on the EVM, get object is used to read state of the blockchain.

There are two params

* `chain` - `mainnet` `testnet` `devnet` `localnet`
* `id` - A 32-byte globally [unique ID](https://docs.sui.io/concepts/object-model). This is used to query the current state of an object or describing which object was transferred between two addresses.

{% tabs %}
{% tab title="curl" %}
```bash
curl --location 'localhost:9680/sui/getObject' \
--header 'Content-Type: application/json' \
--data '{
    "chain": "testnet",
    "id": "0xa1fc3811720a381e2d55cc620c5514116c5254e2bdc72fda2af341fd0998029a"
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
        string jsonString = "{ \"chain\": \"testnet\", \"id\": \"0xa1fc3811720a381e2d55cc620c5514116c5254e2bdc72fda2af341fd0998029a\" }";
        
        byte[] jsonBytes = System.Text.Encoding.UTF8.GetBytes(jsonString);

        UnityWebRequest request = new UnityWebRequest("localhost:9680/sui/getObject", "POST");
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
{% tab title="First Tab" %}
```json
{
    "dataType": "moveObject",
    "type": "0x5f1cbf91020e986d82493bbb8d0efab99c848d5e5fa1eec71faf2db725e2c5f7::counter::Counter",
    "hasPublicTransfer": false,
    "fields": {
        "id": {
            "id": "0xa1fc3811720a381e2d55cc620c5514116c5254e2bdc72fda2af341fd0998029a"
        },
        "owner": "0x78687cc53c07484da514ca3d024d06274c9d079def21ece23a553a17397014a6",
        "value": "5"
    }
}
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
