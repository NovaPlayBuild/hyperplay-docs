---
description: >-
  This page covers important design considerations for game devs looking to
  integrate HyperPlay
---

# Design Considerations

## Security

### Requesting a Transaction from the Player

We highly recommend making it clear to the player that the game will be requesting a transaction from them prior to requesting it. HyperPlay also helps with this by overlaying notifications if a transaction is pending on mobile.

All requests must be made from client side code in your game.

### Reading Blockchain State

If your game is multiplayer, we highly recommend reading blockchain state from your server side code. Otherwise the player might be able to fake a transaction to obtain an in-game item.

## Game Engine Integrations

There are several methods of integrating HyperPlay into your game depending on which engine you using.

{% content-ref url="unreal-engine-integration.md" %}
[unreal-engine-integration.md](unreal-engine-integration.md)
{% endcontent-ref %}

{% content-ref url="unity-integration.md" %}
[unity-integration.md](unity-integration.md)
{% endcontent-ref %}
