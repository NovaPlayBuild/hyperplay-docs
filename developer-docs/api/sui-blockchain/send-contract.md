# Send Contract

## Request

Similar to [send contract](../erc20-transfer-example.md) on EVM, this is use to [update a smart contract](https://docs.sui.io/guides/developer/sui-101/building-ptb#available-transactions) object.

Parameters

* `chain` - `mainnet` `testnet` `devnet` `localnet`
* target - Target object interact with
* `args` - An array of arguments

{% tabs %}
{% tab title="curl" %}
```bash
curl --location 'localhost:9680/sui/sendContract' \
--header 'Content-Type: application/json' \
--data '{
    "chain": "testnet",
    "target": "0x5f1cbf91020e986d82493bbb8d0efab99c848d5e5fa1eec71faf2db725e2c5f7::counter::increment",
    "args": ["0xa1fc3811720a381e2d55cc620c5514116c5254e2bdc72fda2af341fd0998029a"]
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
        string jsonString = "{ \"chain\": \"testnet\", \"target\": \"0x5f1cbf91020e986d82493bbb8d0efab99c848d5e5fa1eec71faf2db725e2c5f7::counter::increment\", \"args\": [\"0xa1fc3811720a381e2d55cc620c5514116c5254e2bdc72fda2af341fd0998029a\"] }";
        
        byte[] jsonBytes = System.Text.Encoding.UTF8.GetBytes(jsonString);

        UnityWebRequest request = new UnityWebRequest("localhost:9680/sui/sendContract", "POST");
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
{% tab title="Response" %}
```html
GKnKZHuZoR9uvSbwXvu81nAWJ9PKhkaGouR6CCnXMabt
```
{% endtab %}

{% tab title="Error" %}
```
{
  "message": "error description here"
}
```
{% endtab %}
{% endtabs %}
