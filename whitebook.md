# ArQmA (ARQ) Whitepaper

*Privacy-preserving digital cash with CPU-fair mining and a staked service-node layer*

*Date: August 19, 2025*

---

# 1. Abstract

ArQmA (ticker: **ARQ**) is a privacy-first, open-source cryptocurrency derived from the Monero/CryptoNote codebase. It focuses on three pillars: (1) strong on-chain privacy by default, (2) egalitarian, CPU-friendly mining via a RandomX variant called **RandomARQ**, and (3) a utility layer of **Service Nodes** (SNs) that provide network services such as storage and overlay routing for applications built on, or adjacent to, the ArQmA network. ([GitHub][1], [xmrig.com][2], [Bitcoin Talk][3])

---

# 2. Motivation & Vision

Digital payments should be **private, censorship-resistant, and accessible**. ArQmA aims to provide everyday, low-fee settlement with robust privacy, while keeping mining open to commodity hardware and expanding utility through a staked node layer that supports services beyond simple payments (e.g., storage and overlay networking). ([GitHub][1], [Bitcoin Talk][3])

---

# 3. Design Overview

ArQmA inherits CryptoNote’s privacy stack—**stealth addresses**, **ring signatures**, and **RingCT with Bulletproofs**—so sender, receiver, and amounts are concealed by default. The base layer runs a proof-of-work (PoW) blockchain; the service-node layer adds opt-in capabilities (e.g., storage server) funded by staking. All core software is open source. ([GitHub][1])

---

# 4. Consensus & Mining

## 4.1 Algorithm

ArQmA uses **RandomARQ**, a variant of RandomX specifically tuned for the ARQ network, prioritizing CPU-friendliness and ASIC resistance. RandomARQ is supported by mainstream CPU miners (e.g., XMRig), affirming its role as a RandomX family variant. ([GitHub][4], [xmrig.com][2])

## 4.2 Network Timing & Difficulty

The network targets a **\~120-second block time** with **per-block difficulty retargeting**, aligning throughput and confirmation latency for everyday payments while maintaining chain stability. (Parameters reflect commonly published ARQ mining guidance.) ([Medium][5])

## 4.3 Mining Goals

* Keep mining **egalitarian** and accessible to general users.
* Resist specialized hardware and rented hash bursts (ASIC/NiceHash). ([arqma.com][6])

---

# 5. Monetary Policy

## 5.1 Supply

* **Maximum supply:** **50,000,000 ARQ** (hard cap). ([CoinMarketCap][7])
* Emission follows a **smoothly varying** block-reward schedule toward that cap. (Historical materials cite \~20 ARQ initial reward; actual reward declines over time as supply approaches the cap.) ([Medium][5])

## 5.2 Initial Distribution & Transparency

ArQmA launched **without an ICO**. Historical community posts indicate there was an **early premine allocation** earmarked for project purposes; subsequent communications and community artifacts reference **burns** and usage (e.g., listings, bounties). The project highlights open, on-chain verifiability and community oversight for any such funds and changes. ([Medium][5], [YouTube][8], [Reddit][9])

> For the latest real-time supply/market metrics, see reputable trackers (CoinGecko/CoinPaprika) and the official explorer. Figures can differ by methodology; the chain is the ultimate source of truth. ([CoinGecko][10], [CoinPaprika][11])

---

# 6. Privacy

## 6.1 Default Confidentiality

ArQmA transactions are private by default using **stealth addresses** (receiver unlinkability), **ring signatures** (sender ambiguity), and **RingCT with Bulletproofs** (amount confidentiality and reduced size). This preserves fungibility and user financial privacy at the protocol layer. ([GitHub][1], [Medium][5])

## 6.2 Network Security

The project documents **TLS/SSL** across nodes and wallets (CLI, GUI, Android), aiming to protect RPC and P2P communications from interception or tampering. ([GitHub][1])

---

# 7. Node Architecture

## 7.1 Full & Remote Nodes

Full nodes validate the chain independently; remote nodes provide lightweight access for clients that cannot run full validation. Both are part of the peer-to-peer layer that reaches network consensus. ([GitHub][1])

## 7.2 Service Nodes (SNs)

Service Nodes are staked nodes that **commit collateral** and **run additional services** for the network (e.g., the **ArQmA storage server** component). This layer enables chain-adjacent functionality (messaging/storage/overlay routing) while aligning node incentives via staking and periodic rewards. Operational guidance emphasizes that SN operators must run the storage-server component and expose the service for the network. Protocol-enforced staking parameters (total requirement, contributor limits, and minimum contribution) are visible on the chain and in the explorer. ([Bitcoin Talk][3], [GitHub][12], [Arqma Explorer][13])

## 7.3 Arq-Net Overlay

Arq-Net is an **anonymous, decentralized IP-based overlay network** maintained within the ArQmA organization, intended to support privacy-preserving communication and application routing. This aligns with the Service-Node layer to host network utilities that go beyond simple payments. ([GitHub][12])

---

# 8. Fees & Throughput

CryptoNote-style batching and compact confidential transactions (Bulletproofs) help keep **fees low** for everyday use. Target block times and adaptive difficulty balance confirmation latency and throughput. (Concrete fee levels depend on network conditions and wallet policies.) ([GitHub][1])

---

# 9. Wallets & Developer Tooling

* **Desktop & Electron wallets**; **Android wallet** for mobile usage.
* **RPC & SDKs:** an official **JavaScript RPC library** is available for interacting with the daemon and wallet RPCs (HTTP/HTTPS, digest auth, async calls).
* **Explorer & Tooling:** open-source block explorer and auxiliary infrastructure. ([GitHub][14], [arqma.com][15])

---

# 10. Governance & Upgrades

ArQmA development is **open source** and community-driven on GitHub, with contributions, reviews, and releases coordinated publicly. Network-wide upgrades (hard forks) are announced in advance with code shipped and tested in repositories before activation. Community channels (Discord/Telegram/Matrix/X) are used for coordination. ([GitHub][1])

---

# 11. Security Considerations

* **Consensus risks:** PoW remains robust but subject to hashrate concentration and short-term rental threats—mitigated by RandomARQ’s CPU bias and NiceHash resistance goals. ([arqma.com][6])
* **Privacy pitfalls:** Users must keep wallets updated and follow good hygiene (fresh subaddresses, avoiding metadata leaks).
* **Operational risk for SNs:** Misconfiguration (e.g., not running the storage server) can lead to missed rewards or penalties; operators should follow current documentation and explorer guidance. ([Bitcoin Talk][3])

---

# 12. Compliance & Responsible Use

ArQmA’s default privacy protects users against undue surveillance, but users remain responsible for **lawful** use within their jurisdictions. Businesses integrating ARQ should implement appropriate KYC/AML procedures at their interfaces where required by law. (ArQmA is a decentralized protocol; compliance occurs at endpoints.)

---

# 13. Roadmap: Focus Areas (non-binding)

* **Service-node ecosystem:** expand storage/overlay capabilities; developer APIs and monitoring. ([Bitcoin Talk][3], [GitHub][12])
* **Wallet UX:** cross-platform reliability, faster sync, hardware-wallet integrations.
* **Audits & research:** continuous review of RandomARQ parameters and privacy proofs.
* **Ecosystem tooling:** more libraries, docs, and sample apps using the RPC JS SDK. ([arqma.com][15])

---

# 14. Conclusion

ArQmA combines **default privacy**, **egalitarian mining**, and a **staked service-node layer** to create a practical, extensible digital-cash system. By keeping mining fair, privacy strong, and utility growing through Service Nodes and Arq-Net, ARQ aims to serve as a durable foundation for everyday private payments and privacy-preserving applications. ([GitHub][1], [xmrig.com][2], [Bitcoin Talk][3])

---

## References

* Project site & docs: arqma.com; GitHub organization and core repo. ([arqma.com][6], [GitHub][1])
* Mining algorithm (RandomARQ): XMRig algorithms documentation; RandomARQ repo. ([xmrig.com][2], [GitHub][4])
* Network parameters (community mining guide): HeroMiners guide (block time, retarget, reward). ([Medium][5])
* Supply cap / market trackers: CoinMarketCap, CoinGecko, CoinPaprika. ([CoinMarketCap][7], [CoinGecko][10], [CoinPaprika][11])
* Service Nodes & storage server requirement: Bitcointalk announcement/update. ([Bitcoin Talk][3])
* Explorer examples for SN contributions/params. ([Arqma Explorer][13])

---

*Note:* Some historical details (e.g., early premine/burn amounts, live staking thresholds, and contributor limits) have evolved. Always rely on **current on-chain data and the latest project communications** for authoritative values. If you want, I can package this into a branded PDF and add a one-page “Quick Facts” appendix (supply, block time, emission progress, explorer links).

[1]: https://github.com/arqma/arqma "GitHub - arqma/arqma: ArQmA: secure, fast and anonymous Currency of the Future  // Dev-Pool: https://supportcryptonight.com/arq"
[2]: https://xmrig.com/docs/algorithms "Algorithms"
[3]: https://bitcointalk.org/index.php?topic=4474605.300 "[ANN][ARQMA] ArQmA RandomARQ coin"
[4]: https://github.com/arqma/RandomARQ "arqma/RandomARQ: Proof of work algorithm based on ..."
[5]: https://herominers.medium.com/how-to-mine-arqma-arq-complete-beginners-guide-552cc27be068 "How to Mine ArQmA (ARQ): Complete Beginner's Guide"
[6]: https://arqma.com/ "Arqma"
[7]: https://coinmarketcap.com/currencies/arqma/ "Arqma price ARQ"
[8]: https://www.youtube.com/watch?v=i5kjN5qu-Pc "Premine Burn 2019 08 09 00 20 18"
[9]: https://www.reddit.com/r/arqma/comments/9h06vz/a_list_of_100_changes_to_the_next_fork_upcoming/ "A list of 100 changes to the next fork upcoming. - arqma"
[10]: https://www.coingecko.com/en/coins/arqma "ArQmA Price: ARQ Live Price Chart, Market Cap & News ..."
[11]: https://coinpaprika.com/coin/arq-arqma/ "Arqma (ARQ) Price - Live Chart, Index, Market Cap"
[12]: https://github.com/arqma/ "Arqma Network"
[13]: https://www.explorer.arqma.com/ "Explorer"
[14]: https://github.com/arqma/arqma-android-wallet/ "Arqma Arq-Net Android Mobile Wallet"
[15]: https://arqma.com/arqma-rpc-js/ "ArQmA Javascript RPC Library - Documentation"
