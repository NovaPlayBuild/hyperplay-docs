# Sign Typed Data v4

## Request

Ask the user to sign typed data

Learn more: [https://docs.metamask.io/wallet/how-to/sign-data/#use-eth\_signtypeddata\_v4](https://docs.metamask.io/wallet/how-to/sign-data/#use-eth\_signtypeddata\_v4)

Replace `0x638105aa1b69406560f6428aeface3db9da83c64` with the connected wallet address. The connected wallet address can be requested from [get-accounts.md](get-accounts.md "mention").

{% tabs %}
{% tab title="curl" %}
```bash
curl --location --request POST 'localhost:9680/rpc' \
--header 'Content-Type: application/json' \
--data-raw '{
  "request": {
    "method": "eth_signTypedData_v4",
    "params": [
      "0x638105aa1b69406560f6428aeface3db9da83c64",
      "{\"domain\":{\"chainId\":1,\"name\":\"Ether Mail\",\"verifyingContract\":\"0xCcCCccccCCCCcCCCCCCcCcCccCcCCCcCcccccccC\",\"version\":\"1\"},\"message\":{\"contents\":\"Hello, Bob!\",\"attachedMoneyInEth\":4.2,\"from\":{\"name\":\"Cow\",\"wallets\":[\"0xCD2a3d9F938E13CD947Ec05AbC7FE734Df8DD826\",\"0xDeaDbeefdEAdbeefdEadbEEFdeadbeEFdEaDbeeF\"]},\"to\":[{\"name\":\"Bob\",\"wallets\":[\"0xbBbBBBBbbBBBbbbBbbBbbbbBBbBbbbbBbBbbBBbB\", \"0xB0BdaBea57B0BDABeA57b0bdABEA57b0BDabEa57\",\"0xB0B0b0b0b0b0B000000000000000000000000000\"]}]},\"primaryType\":\"Mail\",\"types\":{\"EIP712Domain\":[{\"name\":\"name\",\"type\":\"string\"},{\"name\":\"version\",\"type\":\"string\"},{\"name\":\"chainId\",\"type\":\"uint256\"},{\"name\":\"verifyingContract\",\"type\":\"address\"}],\"Group\":[{\"name\":\"name\",\"type\":\"string\"},{\"name\":\"members\",\"type\":\"Person[]\"}],\"Mail\":[{\"name\":\"from\",\"type\":\"Person\"},{\"name\":\"to\",\"type\":\"Person[]\"},{\"name\":\"contents\",\"type\":\"string\"}],\"Person\":[{\"name\":\"name\",\"type\":\"string\"},{\"name\":\"wallets\",\"type\":\"address[]\"}]}}"
    ]
  },
  "chain": {
    "chainId": "1"
  }
}
'
```
{% endtab %}
{% endtabs %}
