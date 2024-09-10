# 🕹 API for Native Games

## Overview

NovaPlay is a web3-native game launcher with wallet integration. The launcher acts as a proxy between the desktop game and wallet. Any game on NovaPlay can trigger a wallet interaction with a simple HTTP request.

* Game triggers a HTTP request
* NovaPlay launcher receives the request and forwards it to the player's wallet
* If the player connected via MetaMask Mobile or WalletConnect, there will be a mobile popup
* If the player connected via MetaMask Extension, there will be an in game overlay
* The player can decide to approve or reject the transaction

<figure><img src="../../.gitbook/assets/overlay.png" alt=""><figcaption></figcaption></figure>

## All JSON RPC Endpoints

The NovaPlay API references many of the calls found in MetaMask's and geth's JSON RPC endpoints. The next sections will provide some examples.

{% embed url="https://metamask.github.io/api-playground/api-documentation" %}

{% embed url="https://ethereumbuilders.gitbooks.io/guide/content/en/ethereum_json_rpc.html" %}

## Quick Start

{% embed url="https://youtu.be/EpdoYwEm8qE" %}
