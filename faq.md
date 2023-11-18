---
description: An overview of common questions about HyperPlay
---

# ❓ FAQ

**Q: What is HyperPlay?**

A: HyperPlay is a desktop application that provides both a web3-native game launcher and an aggregator of game stores. HyperPlay allows players to install games from the Epic Store, GOG, or our own HyperPlay store. Players can connect their MetaMask or WalletConnect wallet to our native desktop application, and then use their wallet inside of every game launched from within HyperPlay, even in native desktop games. HyperPlay was developed in partnership with [**MetaMask**](https://metamask.io) and was incubated by [**Game7**](https://game7.io/), a DAO focused on accelerating the adoption of sustainable web3-native gaming. In June of 2023, we closed a capital raise and became an independent company.



**Q: Does HyperPlay have a token?**

A: Not at this time, but we’ll see.\


**Q: Is HyperPlay open source?**&#x20;

A: Yes. HyperPlay is open source, mainly under a GPL license. A small number of our products like the HyperPlay developer portal and the wallet overlay are issued under a proprietary license, although we are working to progressively be more open source over time.\


**Q: How do games get included in HyperPlay?**

A: HyperPlay is an aggregator of game stores, so the answer varies per store. Developers seeking to list in the HyperPlay Store should get in contact with us through [**this form**](https://forms.gle/A3mQ8A7CTWrDo8LD6). Once your application is processed, we'll schedule an onboarding call and grant you access to the HyperPlay developer portal where you can manage your game builds. Games listed through the Epic Games Store or GOG will automatically become available to players inside of HyperPlay. We recommend reaching out to those stores directly.



**Q: What does HyperPlay charge developers to be included? Steam and Apple are charging 30% fees. Will HyperPlay charge similar fees?**

A: HyperPlay takes no cut from game purchases or in-game transactions. For developers releasing through Epic or GOG, the fees of those stores still apply, but we add no additional fees.&#x20;



**Q: Are both native games and browser games supported?**

A: Yes, both are supported! For browser games, we work some UX magic to give these a better user experience than playing a in traditional browser. We also provide graphics card acceleration of browser based games through WebGPU.



**Q: Which wallets are supported?**

A: Players can use MetaMask Mobile, the MetaMask browser extension, or any WalletConnect based wallet like Sequence, TrustWallet, or others. MetaMask Mobile and WalletConnect are connected by scanning a simple QR code, and the MetaMask browser extension can even be imported from your existing browser install.



**Q: How will HyperPlay keep players safe from scams, malware, and other attack vectors?**

A: There are four critical components to HyperPlay’s security strategy. \


1. **Store review:** all stores included in our app (HyperPlay, Epic, GOG) do extensive malware testing and diligence on the development teams for any software submitted through our store, including both static analysis and dynamic analysis. We never allow any title to be published without security review.
2. **Game sandboxes:** Because it is impossible to ensure that no malware will ever slip through a store review process, we’re introducing game sandboxes that prevent a malicious game that slipped through a store review process from acting outside of its own context. We aim to launch this feature soon.
3. **Key segregation:** HyperPlay never exposes a user’s keys to games. The wallet lives within our desktop application or on an external mobile device. Games can submit transaction requests to HyperPlay, which we show to the user. The game cannot access the user’s keys or sign on behalf of the user without user consent.
4. **External signer:** It isn’t a coincidence that we support MetaMask Mobile and WalletConnect. Keeping the keys off of one’s device, and having transactions pop up on an external mobile device is an inherently more secure pattern. For security conscious users, we strongly recommend the MetaMask Mobile integration as the most secure connection method. Even in the event that a user's computer becomes compromised, this pattern should keep the malware from being able to access the keys.

A word of warning here: other "web3 game launchers" have often marketed themselves as a safer solution to download games. At the time of writing, we are aware of extremely alarming poor security practices in some of these products. We urge those teams to look to our example and take user safety and protection of user funds more seriously.

\


**Q: What is the process of bringing an existing MetaMask wallet to HyperPlay?**

A: For MetaMask Mobile or WalletConnect users, players will scan a QR code within the HyperPlay app from MetaMask Mobile to link their wallet. For browser extension users, HyperPlay makes it super simple to import any MetaMask wallet (including custom networks, tokens, and settings) already found on the local device by importing the install from their browser extension folder. We only import your existing install with explicit user consent, however.



**Q: Which networks are supported?**

A: All EVM networks are supported, including Ethereum, zkSync, Polygon, Mantle, Linea, Avalanche, Arbitrum, Optimism, BSC, and Harmony. Non-EVM networks like Sui, Starkware, Solana and Cosmos are supported through MetaMask’s Snaps plugin system, but will require the user to use a MetaMask browser extension wallet for compatibility.\


**Q: What operating systems are supported?**

A: HyperPlay supports Windows, SteamDeck, MacOS, and Linux. We are integrated with Wine-Crossover, improving game compatibility on Mac. For SteamDeck and Linux players, HyperPlay integrate with the [Proton compatibility library](https://www.protondb.com/), allowing Windows games to run natively.



**Q: What kinds of interactions between games and the integrated wallets are possible?**

A: All major web3 APIs can be passed through to the game, and back to the wallet. This is accomplished using a combination of the MetaMask Mobile SDK, the MetaMask browser extension, and the HyperPlay client-side API. This includes transaction requests, signature requests, propose custom networks, and propose custom tokens.&#x20;



**Q: Is HyperPlay related to the Heroic Games Launcher?**

A: Yes! HyperPlay's co-founder Flavio Lima is also the founder of the Heroic Games Launcher. Heroic was created to allow people to play Epic Games Store games on Steam Deck and Linux, but isn’t necessarily a web3 product. We are developing both products, and share a great deal of the same tech.



**Q: What are some of the benefits for developers launching their games through this platform?**

A: We solve many developer experience problems (ie. the wallet-to-game interaction problem) to make it easier to build great web3 game experiences. Additionally, our model of aggregating many stores provides a safe haven for web3 game developers who have been constantly de-platformed and taxed by monopolistic web2 companies. We are a developer loyal platform that aims to promote freedom and permissionless innovation.\


**Q: How does HyperPlay make money?**

A: We are not monetized at this time. We plan to introduce optional monetized features to our users at a later date.



\
