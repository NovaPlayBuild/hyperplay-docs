---
description: Suggestions for how to integrate HyperPlay with your Unity Project
---

# Unity Integration

## Integration pathes

Unity games seeking to leverage HyperPlay's wallet features may do so through direct HTTP API calls, or through no-code SDKs provided through HyperPlay's partners.

## SDKs

Our recommended SDK for Unity developers is [ThirdWeb](https://thirdweb.com/), which has a [deep integration](https://portal.thirdweb.com/unity/wallets/actions/connect) with HyperPlay's wallet features out of the box.

Developers using other SDKs can still integrate directly using our [Wallet API](../api/).

## C\#

You can use our Unity API examples to write your own transaction requests with the `UnityEngine.Networking` module.
