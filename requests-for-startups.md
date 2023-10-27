<!-- omit in toc --> 
# Requests for Startups

List of ideas for startups in the Internet Computer ecosystem.
If you're interested, you can apply for a developer grant at https://dfinity.org/grants to get things rolling.
In addition, we'll be happy to support you with technical guidance, PR, as well as introductions to the community and investors.

If you'd like to add a request for startups, [start a discussion](https://github.com/dfinity/grant-rfps/discussions).

<!-- omit in toc --> 
## Contents

- [xChain Oracle Service](#xchain-oracle-service)
- [xChain Messaging Service](#xchain-messaging-service)
- [Governance Platform for Ethereum DAOs](#governance-platform-for-ethereum-daos)
- [xChain Smart Contract Wallet](#xchain-smart-contract-wallet)
- [xChain Decentralized Exchange](#xchain-decentralized-exchange)
- [xChain Automation and Web3 functions](#xchain-automation-and-web3-functions)
- [Provider for (dynamic) NFT assets](#provider-for-dynamic-nft-assets)
- [ckBTC Mobile Payment App](#ckbtc-mobile-payment-app)
- [Backup and Watchtower Service for Lightning Network Users](#backup-and-watchtower-service-for-lightning-network-users)
- [Bitcoin-backed Stablecoin](#bitcoin-backed-stablecoin)
- [Ordinals Marketplace](#ordinals-marketplace)
- [IC GameKit](#ic-gamekit)
- [Decentralized Certificate Authority](#decentralized-certificate-authority)
- [Decentralized Identifier (DID) Registry](#decentralized-identifier-did-registry)
- [User-owned IoT Platform](#user-owned-iot-platform)
- [Web3-ready App Development Platform](#web3-ready-app-development-platform)
- [Registry](#registry)

## Multichain Oracle Service

Canister smart contracts can call web services using [HTTPS Outcalls](https://internetcomputer.org/https-outcalls) and can sign transactions targeting [various blockchains that support ECDSA (with curve `secp256k1`)](http://ethanfast.com/top-crypto.html) using [Chain-key Signatures](https://internetcomputer.org/docs/current/developer-docs/integrations/t-ecdsa). One major use case of oracles is to bring price information on chain. With the [exchange rate canister](https://github.com/dfinity/exchange-rate-canister) (currently in beta), there’s already an open internet service available on the Internet Computer that allows to fetch various exchange rates. Furthermore, canisters have access to cryptographic randomness which can be provided to other chains.

### Examples

- [Orally](https://github.com/orally-network)
- [Chainsight](https://chainsight.network/)

## xChain Messaging Service

The Internet Computer is well suited to build a cross-chain messaging service, because
- [Chain-key signatures](https://internetcomputer.org/docs/current/developer-docs/integrations/t-ecdsa) allow signing transactions destined for various chains
- Messages from the IC can be verified by 1-2 BLS signatures, instead of following a blockchain, i.e. for chains that support cost-efficient BLS signature verification on-chain, it's simple to verify messages from the IC.
- [HTTPS Outcalls](https://internetcomputer.org/https-outcalls) allow to submit and retrieve messages to and from other chains.
- The capabilities of canister smart contracts make it feasible to implement [on-chain light clients for other chains](https://github.com/dfinity/grant-rfps/issues/25) if available.

### Examples

- [icRouter](https://github.com/iclighthouse/icRouter)
- [Omnic](https://github.com/rocklabs-io/omnic)

## Governance Platform for Ethereum DAOs

Many DAOs, in particular in the Ethereum ecosystem, use [Snapshot](https://snapshot.org) for off-chain governance, because on-chain voting is just too expensive. The Internet Computer, however, provides a perfect platform to implement a cost-effective on-chain voting platform that is able to enforce voting results on the Internet Computer itself (e.g. to enforce a frontend upgrade) as well other target chains using [Chain-key Signatures](https://internetcomputer.org/docs/current/developer-docs/integrations/t-ecdsa).

Furthermore, the xChain capabilities of the IC allow also to execute and sync governance decisions to the deployments of a dapp on multiple EVM chains.

## xChain Smart Contract Wallet

Smart contract wallets are becoming the new default because they can provide a better user experience as well as more security. Among others, smart contract wallets allow:

- The definition of various authentication methods
- Multi-factor authentication
- Rich programmable policies
- [Social recovery](https://vitalik.ca/general/2021/01/11/recovery.html)

The Internet Computer is a perfect platform to build smart contract wallets because:

- It allows targeting multiple chains using [Chain-key signatures](https://internetcomputer.org/how-it-works/threshold-ecdsa-signing/).
- You can build full-stack web wallets since canister smart contracts can serve web browsers directly.
- The Internet Computer itself supports various authentication methods such as [WebAuthn](https://webauthn.io/), and the Internet Computer is efficient enough to allow developers to implement custom authentication methods on application level.

### Examples

- [B3Wallet](https://github.com/B3Pay/b3-wallet)
- [Oisy](https://oisy.com/)
- [AstroX ME](https://astrox.me/)
- [NFID](https://nfid.one/)


## xChain Decentralized Exchange

[Chain-key Signatures](https://internetcomputer.org/how-it-works/threshold-ecdsa-signing/), [HTTPS Outcalls](https://internetcomputer.org/https-outcalls) and cross-chain integrations ([Bitcoin](https://internetcomputer.org/bitcoin-integration), [Ethereum](https://forum.dfinity.org/t/long-term-r-d-integration-with-the-ethereum-network/9382/42)) allow canister smart contracts to hold various currencies in non-custodial escrow. Furthermore, the Internet Computer's computational capabilities and high throughput allow for building not only AMM-based exchanges but also order-book based exchanges. The upcoming feature, [threshold key derivation](https://forum.dfinity.org/t/threshold-key-derivation-privacy-on-the-ic/16560), will also allow building exchanges with MEV-protection.

## xChain Automation and Web3 Functions

Typical smart contracts can't run autonomously but have to be triggered by an incoming transaction. Canister smart contracts on the other hand can employ a heartbeat or timer to trigger periodic execution. In combination with Chain-key Signatures](https://internetcomputer.org/how-it-works/threshold-ecdsa-signing/) and[HTTPS Outcalls](https://internetcomputer.org/https-outcalls), you can build xChain automation and decentralized cloud functions similar to [Gelato Network](https://gelato.network/). 

### Examples

- [Helix Markets](https://www.helixmarkets.io/)
- [ICDex](https://iclight.io/ICDex)

## Provider for (dynamic) NFT assets

Most NFTs in the greater Web3 ecosystem are pointers to off-chain assets. Best practice for these pointers is to use content-addressing with IPFS, and then use a compatible storage network (or a service provider like [Pinata](https://pinata.cloud)) to actually host the assets. However, this is limited to static assets. On the Internet Computer, you can build a service to host assets in canister smart contracts linked to NFTs on the IC itself, but also on other chains. In addition, these assets can be generated in real time according to rules defined in the canister smart contract.

## ckBTC Mobile Payment App

Bitcoin was the first cryptocurrency, it has still by far the largest market capitalization, and the greatest distribution. However, transaction costs and latency make BTC payments unsuitable for most applications. The Lightning Network is being built to tackle these issues but is highly complex and has certain user experience drawbacks. On the other hand, the Internet Computer provides chain-key Bitcoin (ckBTC) a token that is backed 1:1 by bitcoin held in canister smart contracts. With [ckBTC](https://internetcomputer.org/docs/current/developer-docs/integrations/bitcoin/ckbtc) - Bitcoin holders can opt into low fee and low latency payments, and can redeem for native BTC at any time. In addition, ckBTC is the perfect fit for a non-custodial mobile payment app since you can verify payments and transfers by just checking the signature of the Internet Computer. There’s no need to download the chain of block headers or interact with centralized backend infrastructure.

## Backup and Watchtower Service for Lightning Network Users

Lightning has two problems: it requires constant backups of newly generated channel state data or otherwise the lightning node could lose funds. And it requires watching channels (watch towers). For both things, a canister can help. So the setup would be a traditional lightning node and a canister that supports it in the background which benefits from being tamperproof, always online and can’t get destroyed. So the canister can serve as a backup target for channel data and also as a watchtower. The latter means that the canister, via the Bitcoin integration, can watch for the channel getting closed by the counterparty and it can submit the penalty transaction if the counterparty attempts to close it with an old state.

More info in this [forum thread](https://forum.dfinity.org/t/integration-with-btc-lightning/18821/2).

## Bitcoin-backed Stablecoin

The [Bitcoin integration](https://internetcomputer.org/bitcoin-integration) allows canister smart contract to hold and transfer BTC. This enables BTC - the asset-rich programmability without reliance on custodians. Furthermore, [HTTPS Outcalls](https://internetcomputer.org/https-outcalls) and the [exchange rate canister](https://github.com/dfinity/exchange-rate-canister) allow canisters to access trustworthy price information. With these two building blocks, there's a large design space of Bitcoin-backed stable currencies to explore.

### Examples

- [Backed USD](https://forum.dfinity.org/t/backed-usd-a-bitcoin-backed-stablecoin-on-the-ic-a-prototype/18430)

## Ordinals Marketplace

[Ordinals](https://ordinals.com/) have brought a new wave of experimentation and innovation to the Bitcoin ecosystem. Ordinals are a mechanism to associate a serial number to individual Satoshis (the smallest denominator of a Bitcoin) and define different levels of rarity to them. Furthermore, with a mechanism called inscribing, we can attach metadata to an ordinal, similar to NFTs. The Bitcoin protocol allows building non-custodial marketplaces, but they are not user-friendly, and allow no other currency than Bitcoin. With the Bitcoin integration, you can build non-custodial marketplaces for Ordinals on the Internet Computer.

### Examples

- [Bioniq](https://bioniq.io/)

## IC GameKit

Many cloud providers offer SDKs to easily implement cloud-based features in their games. An example is AWS GameKit. It offers the following main features (source: [AWS GameKit docs](https://docs.aws.amazon.com/gamekit/latest/UnrealDevGuide/intro-what-is-gamekit.html)):

- **Identity and authentication** – Protect players with secure registration and robust identity management for your game. Verify player logins to manage access to player sessions, and use authentication for AWS GameKit cloud features.
- **Achievements** – Create goals that players can achieve to earn recognition, win rewards, or initiate game events. Manage players' achievements in the cloud and track their progress toward long-term goals.
- **Game state cloud saving** – Synchronize game saves in the cloud so that players can resume their play from different locations and devices, or recover game progress as needed.
- **User gameplay data** – Maintain gameplay data for each player, such as inventory, statistics, and cross-play persistence, and make it available to players wherever and whenever they log in to the game.

These features can be replicated on the Internet Computer and enhanced by

- Achievements as interoperable NFTs or POAPs
- In-game payments
- Inclusion of NFT collections
- Access to NFT marketplaces

Thereby, an IC GameKit could be (close to) a drop in replacement for AWS GameKit that extends the capabilities with Web3 superpowers.

## Decentralized Certificate Authority

[Chain-key signatures](https://internetcomputer.org/docs/current/developer-docs/integrations/t-ecdsa) allow canisters to issue x.509 certificates used in Public Key Infrastructures (PKIs). Hence, a canister can serve the role of a decentralized certificate authority. An interesting project would be to investigate if a canister using [chain-key signatures](https://internetcomputer.org/docs/current/developer-docs/integrations/t-ecdsa) and [HTTPS Outcalls](https://internetcomputer.org/https-outcalls), potentially using a custom gateway, could serve as an ACME server similar to Let's encrypt. Note however that the `secp256k1` curve is currently not supported by TLS.

## Decentralized Identifier (DID) Registry

[Decentralized Identifiers (DIDs)](https://www.w3.org/TR/did-core/) are a nascent W3C Web standard at the basis of Self-Sovereign Identity (SSI). DIDs are long-lasting, user-controlled identifiers that can be used to authenticate to services, prove ownership of verifiable credentials, and more. There are many different DID methods and many of them are tied to a specific blockchain. The Internet Computer offers a unique opportunity to build a scalable blockchain-based DID method and DID registry, with capabilities such as
- Lightweight verification of DID resolution results due to chain-key technology
- Potential implementation of the right to be forgotten, since blocks are garbage collected and entries can be removed from the state
- Immutable or governed DID registry
- Advanced recovery features for DIDs

## User-owned IoT Platform

There have been many instances of IoT products being bricked because the cloud platform has been turned off. The Internet Computer allows building a decentralized cloud platform for IoT products, where either the backend service can be owned by the respective user or a multi-tenant platform can be owned by the users collectively, e.g. by utilizing the [Service Network System](https://internetcomputer.org/docs/current/developer-docs/integrations/sns/tokenomics/).

The Internet Computer is specifically well suited as the basis of an IoT platform because IoT devices can verify messages from the IC by verifying a single BLS signature instead of keeping track of a blockchain.

## Web3-ready App Development Platform

The Internet Computer's powerful computing and hosting environment allows to build app development platforms with a similar feature set than web2 app development platforms such as Firebase, but without the platform risk and the access to cutting-edge web3 integrations such as payments and NFTs.

### Example

- [Juno](https://juno.build/)

<!-- ## Neutral Enterprise Integration Platform -->

##  Registry

The Internet Computer allows building registries, such as
- Package registries (npm, Docker Hub, ...)
- Code repositories (GitHub, GitLab, ...)
that are not controlled by a single entity.

There is a large design space to explore from completely neutral registries to registries with decentralized governance, as well as tokenomics to incentivize contributions.

### Examples
- [Codebase](https://codebase.org/)
- [MOPS](https://mops.one/)
   
