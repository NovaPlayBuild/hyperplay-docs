---
description: Suggestions for how to integrate NovaPlay with your Unreal Engine Project
---

# Unreal Engine Integration

## HTTP Requests

There are several options in Unreal Engine for making HTTP requests depending on your needs.

### [web3.unreal](https://github.com/G7DAO/web3.unreal) (Recommended)

We have built a free and open source plugin specifically for Unreal devs that wraps the UE HTTP runtime.&#x20;

This plugin exposes async nodes globally that parse input and output parameters into NovaPlay calls. This way you can work in an Unreal context without having to worry about formatting or syntax errors.&#x20;

See our API docs for examples you can easily copy and paste into your Blueprint graphs.

### C++&#x20;

You can use the [Unreal Engine HTTP runtime](https://docs.unrealengine.com/4.27/en-US/API/Runtime/HTTP/) directly. See our API docs for examples.

### Fetch Plugin

This plugin makes generic HTTP calls at the blueprint level easy.

A license can be [purchased in the Unreal Marketplace](https://www.unrealengine.com/marketplace/en-US/product/fetch-a-simple-http-client?sessionInvalidated=true) for commercial projects.

Or [downloaded from the Github repo ](https://github.com/GDi4K/unreal-fetch)for non-commercial projects.&#x20;

## Architecture

### Blueprint Library

If you intend on using the UE HTTP runtime directly, it is recommended that you expose these functions in a Blueprint Function Library.

### Game instance

Common NovaPlay API calls can be defined in your Game Instance class. This is a good place since it is available globally, only exists on the client side, and persists despite level changes and other changes to game state.
