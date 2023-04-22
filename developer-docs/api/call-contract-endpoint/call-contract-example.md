# Call Contract Example

## Request

This request reads the name of a contract.

{% tabs %}
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
