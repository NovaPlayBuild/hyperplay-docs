# 🖥 Developer Portal

During your onboarding session with our team, we will provide you with a direct link to our Developer Portal where you can publish your game.

{% tabs %}
{% tab title="Creating an Account" %}
Upon navigating to our Developer Portal, you will be greeted by the following Welcome Screen.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-18 at 5.43.45 PM.png" alt=""><figcaption></figcaption></figure>

Follow the on-screen instructions to connect your wallet and create a Developer account.

1. Click on “Connect Wallet”&#x20;
2. Select your desired wallet
   1. MetaMask Browser Extension
   2. E-Mail via Magic Link
   3. WalletConnect
3. If you do not currently have a wallet, you can click on “Get a Wallet” to set one up

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-18 at 5.50.18 PM.png" alt=""><figcaption></figcaption></figure>

You will be prompted with a request to allow the site to add a network (polygon)

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-18 at 5.58.49 PM.png" alt=""><figcaption></figcaption></figure>

You must select **“Approve”** to continue to the next step

After selecting “Approve,” you will receive a request to change the network from Ethereum to Polygon. Select **“Switch network”**

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-18 at 5.58.59 PM (1).png" alt=""><figcaption></figcaption></figure>

You will then be prompted with a message requesting you to verify ownership of the wallet. Click on **“Send message”** to sign the message.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-18 at 5.59.13 PM.png" alt=""><figcaption></figcaption></figure>

Next, you'll encounter a message asking you to sign in and complete the verification process to confirm ownership of your wallet.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-18 at 6.00.02 PM.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
It's essential to note that for security reasons, you ensure that the URI below the **"Sign in with Ethereum to HyperPlay"** prompt shows the Developer Portal URL.
{% endhint %}

#### Setting up your Account

Fill in your account information and add an image.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-18 at 7.52.14 PM.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Please note the **“Display Name”** will be converted to an immutable username that will be saved in the registry smart contract. You can change the Display Name at any time, along with any other metadata.
{% endhint %}

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-18 at 7.52.41 PM.png" alt=""><figcaption></figcaption></figure>

After completing the previous step, select **"Proceed to Add Members"**. This page will allow you to designate administrators who will have complete control over the account and all its games. Administrators have full privileges, such as modifying settings and uploading new releases.

You may use any wallet address or ENS name for adding admins. Your currently connected wallet will be automatically added as an account admin.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-18 at 7.53.00 PM.png" alt=""><figcaption></figcaption></figure>

When you have finished, click **"Complete Create Account"**. You will then receive a prompt to sign a meta-transaction (with no gas fees) to register the account:

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-18 at 7.53.29 PM.png" alt=""><figcaption></figcaption></figure>

If you wish to confirm the forwarder contract responsible for processing the meta-transaction, you may click **"Verify contract details"**. This will reveal the contract's address and a link to its block explorer.\


<figure><img src="../../.gitbook/assets/Screenshot 2023-04-18 at 7.53.40 PM.png" alt=""><figcaption></figcaption></figure>

**The correct address is:**

[0x2abee2e2294556ebe0b15b8eb0ed4891b27ae777](https://polygonscan.com/address/0x2abee2e2294556ebe0b15b8eb0ed4891b27ae777)

{% hint style="success" %}
Navigate to the **"Create a Game"** Tab at the top of this page to continue.&#x20;
{% endhint %}
{% endtab %}

{% tab title="Creating a new Game" %}
Here, you can provide more information about your game by filling out the following metadata fields:

* Game Cover (**16:9 ratio or 1920x1080px**)
* Display Name
* Website
* Type
  * Options include: Browser or Native Desktop
* Genres
* Supported Blockchain Networks

The **"Supported Blockchain Networks"** field is optional, but it helps us to categorize your game accurately and verify the contracts that users will be interacting with.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-19 at 3.36.55 PM.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The **“Display Name”** will be converted into an immutable username in the same way the account username was created. The “Display Name” and all other metadata can be changed at any time in the future.
{% endhint %}

After filling out your game's metadata, proceed by clicking on the **"Continue"** button.

Now it's time to configure your game's system requirements. Provide the minimum requirements your game needs, such as CPU, GPU, Memory, and Disk.&#x20;

You can also check the Compatibility Library Support if your game is playable on Linux and/or macOS using the Proton compatibility support built into the HyperPlay Launcher. If you have tested your game on these systems, select the relevant operating system checkboxes.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-19 at 3.37.19 PM.png" alt=""><figcaption></figcaption></figure>

Click **"Continue"** after you have filled out your game's requirements.

In the **"Media & Descriptions"** tab, provide the following details:

* A link to your YouTube video
* Header image (**recommended size is 1824x816px**)
* Gallery images (**screenshots of gameplay**) - you can upload any number of images
* Short description
* Full/long description\


<figure><img src="../../.gitbook/assets/Screenshot 2023-04-19 at 3.39.43 PM.png" alt=""><figcaption></figcaption></figure>

Don't forget to click **"Continue"** once you have filled out these details.

After configuring your game's metadata, you have the option to add game publishers who will have the ability to publish new releases exclusively.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-19 at 3.38.03 PM.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Please note that Account Admins have the ability to publish under any game within the account, so if your wallet is already an admin, you do not need to add the address to the Game Publishers list.
{% endhint %}

After adding any desired Game Publishers, click **“Create”**. This will trigger another meta-transaction signature request.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-19 at 3.38.17 PM.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
To verify the authenticity of the contract, you can use the same method as in the previous tab.
{% endhint %}

Once you have completed all the necessary steps, you can proceed to upload your game. You will be directed to your developer portal dashboard where you can manage your game's metadata and upload new releases.&#x20;

{% hint style="success" %}
Navigate to the **"Uploading a Release"** Tab at the top of this page to continue.&#x20;
{% endhint %}
{% endtab %}

{% tab title="Uploading a Release" %}
To begin the upload process, simply click the "Submit Release" button located on your game's card.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-19 at 3.38.31 PM.png" alt=""><figcaption></figcaption></figure>

After selecting **"Submit Release"** you will be taken to a landing page where you will need to specify a release version for your game. Please use the SemVer (semantic version) format when entering the version number.

You also have the option to add a release image and release notes, although these are not mandatory.

{% hint style="info" %}
It is worth noting that releases are entirely immutable for security reasons. If you need to make changes to a release, you must create a new release with a different tag and release name.
{% endhint %}

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-19 at 3.38.43 PM.png" alt=""><figcaption></figcaption></figure>

Moving on to the next tab, you can upload the files for your release.

**Supported platforms for game releases include:**

* Browser games & WebGL builds
* Windows 10 and up
* macOS Catalina and up
* Linux & SteamOS
* AMD64 and ARM64 architectures for each platform

**For Windows builds:**

1. Upload a compressed ZIP file of your game folder with the .exe in the root folder.&#x20;

**Example:**&#x20;

* Zipped game folder
  * game.exe

**Wrong Example:**

* Zipped game folder
  * Another game folder
    * game.exe&#x20;

{% hint style="info" %}
Uploading your build incorrectly will make it difficult for users to import your game later on if needed.
{% endhint %}

2. Set the executable path from the build root, including the .exe extension.
3. Add an optional pre-install script for any dependencies.

If there are any external dependencies, include them in a folder named **"redist**" or add a pre-install script.

**For macOS builds:**

1. Upload a compressed ZIP file of your .app or .pkg file.
2. Set either the .app or .pkg name as the executable path, including the .app/.pkg file extension.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-19 at 3.38.59 PM.png" alt=""><figcaption></figcaption></figure>

**You have two options to upload your browser/web builds:**

1. Upload your web build folder.
2. Set an external URL to an already deployed website.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-19 at 3.39.12 PM.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
You will be prompted to sign one final meta-transaction to complete the release.
{% endhint %}

Upon successful upload and submission of your release, you will receive the following confirmation message.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-19 at 3.39.24 PM.png" alt=""><figcaption></figcaption></figure>

Once your release is submitted, it will be received by the HyperPlay team for review and verification. The process generally takes less than **five business days**.

Congratulations on successfully submitting your release to the HyperPlay Store! We are thrilled to work with you in building the next generation of gaming.
{% endtab %}
{% endtabs %}



