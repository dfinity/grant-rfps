<!-- omit in toc -->

# Requests for Startups

List of ideas for startups in the Internet Computer ecosystem.
If you're interested, you can apply for a developer grant at https://dfinity.org/grants to get things rolling.
In addition, we'll be happy to support you with technical guidance, PR, as well as introductions to the community and investors.

<!-- omit in toc -->

## Contents

- [Requests for Startups](#requests-for-startups)
  - [Contents](#contents)
  - [Multi-chain Oracle Service](#multi-chain-oracle-service)
  - [Multi-chain Messaging Service](#multi-chain-messaging-service)
  - [Multi-chain Governance](#multi-chain-governance)
  - [Multi-chain Smart Contract Wallet](#multi-chain-smart-contract-wallet)
  - [Multi-chain Decentralized Exchange](#multi-chain-decentralized-exchange)
  - [Multi-chain Token Baskets](#multi-chain-token-baskets)
  - [Multi-chain Automation and Web3 Functions](#multi-chain-automation-and-web3-functions)
  - [Web3 Zapier/IFTTT](#web3-zapierifttt)
  - [Provider for (dynamic) NFT assets](#provider-for-dynamic-nft-assets)
  - [BtcFi](#btcfi)
  - [Document sharing and collaboration](#document-sharing-and-collaboration)
  - [Decentralized Certificate Authority](#decentralized-certificate-authority)
  - [Decentralized Identifier (DID) Registry](#decentralized-identifier-did-registry)
  - [User-owned IoT Platform](#user-owned-iot-platform)
  - [Web3-ready App Development Platform](#web3-ready-app-development-platform)
  - [Registry](#registry)

## Multi-chain Oracle Service

Canister smart contracts can call web services using [HTTPS Outcalls](https://internetcomputer.org/https-outcalls) and can sign transactions targeting [various blockchains that support ECDSA (with curve `secp256k1`)](http://ethanfast.com/top-crypto.html) using [Chain-key Signatures](https://internetcomputer.org/docs/current/developer-docs/integrations/t-ecdsa). One major use case of oracles is to bring price information on chain. With the [exchange rate canister](https://github.com/dfinity/exchange-rate-canister) (currently in beta), there’s already an open internet service available on the Internet Computer that allows to fetch various exchange rates. Furthermore, canisters have access to cryptographic randomness which can be provided to other chains.

### Examples

- [Orally](https://github.com/orally-network)
- [Chainsight](https://chainsight.network/)

## Multi-chain Messaging Service

The Internet Computer is well suited to build a cross-chain messaging service, because

- [Chain-key signatures](https://internetcomputer.org/docs/current/developer-docs/integrations/t-ecdsa) allow signing transactions destined for various chains
- Messages from the IC can be verified by 1-2 BLS signatures, instead of following a blockchain, i.e. for chains that support cost-efficient BLS signature verification on-chain, it's simple to verify messages from the IC.
- [HTTPS Outcalls](https://internetcomputer.org/https-outcalls) allow to submit and retrieve messages to and from other chains.
- The capabilities of canister smart contracts make it feasible to implement [on-chain light clients for other chains](https://github.com/dfinity/grant-rfps/issues/25) if available.

### Examples

- [icRouter](https://github.com/iclighthouse/icRouter)
- [Omnic](https://github.com/rocklabs-io/omnic)

## Multi-chain Governance

Many DAOs, in particular in the Ethereum ecosystem, use [Snapshot](https://snapshot.org) for off-chain governance, because on-chain voting is just too expensive. The Internet Computer, however, provides a perfect platform to implement a cost-effective on-chain voting platform that is able to enforce voting results on the Internet Computer itself (e.g. to enforce a frontend upgrade) as well other target chains using [Chain-key Signatures](https://internetcomputer.org/docs/current/developer-docs/integrations/t-ecdsa).

Furthermore, the Multi-chain capabilities of the IC allow also to execute and sync governance decisions to the deployments of a dapp on multiple chains.

### Resouces

- [Prototype from DFINITY](https://github.com/bjoernek/multi_chain_voting)

## Multi-chain Smart Contract Wallet

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

## Multi-chain Decentralized Exchange

[Chain-key Signatures](https://internetcomputer.org/how-it-works/threshold-ecdsa-signing/), [HTTPS Outcalls](https://internetcomputer.org/https-outcalls) and cross-chain integrations ([Bitcoin](https://internetcomputer.org/bitcoin-integration), [Ethereum](https://forum.dfinity.org/t/long-term-r-d-integration-with-the-ethereum-network/9382/42)) allow canister smart contracts to hold various currencies in non-custodial escrow. Furthermore, the Internet Computer's computational capabilities and high throughput allow for building not only AMM-based exchanges but also order-book based exchanges. The upcoming feature, [threshold key derivation](https://forum.dfinity.org/t/threshold-key-derivation-privacy-on-the-ic/16560), will also allow building exchanges with MEV-protection.

### Examples

- [Helix Markets](https://www.helixmarkets.io/)
- [ICDex](https://iclight.io/ICDex)


## Multi-chain Token Baskets

Exchange Traded Index Funds (ETFs) are a popular investment vehicle in the traditional finance world. ICP's Chain Fusion Technology allows to build a decentralized version for crypto assets accross multiple chains. You can build token baskets that track the most liquid assets on certain CEXes and DEXes, track certain narratives. 


## Multi-chain Automation and Web3 Functions

Typical smart contracts can't run autonomously but have to be triggered by an incoming transaction. Canister smart contracts on the other hand can employ a heartbeat or timer to trigger periodic execution. In combination with [Chain-key Signatures](https://internetcomputer.org/how-it-works/threshold-ecdsa-signing/) and [HTTPS Outcalls](https://internetcomputer.org/https-outcalls), you can build Multi-chain automation and decentralized cloud functions similar to [Gelato Network](https://gelato.network/).

### Resources

- [Chain Fusion Starter](https://github.com/letmejustputthishere/chain-fusion-starter)

## Web3 Zapier/IFTTT

ICP's Chain Fusion Technology allows to build composable Multi-chain workflows. This means you can build a Zapier/IFTTT-like service that can listen to events on a source chain and trigger events on a target chain.

### Resources

- [Chain Fusion Starter](https://github.com/letmejustputthishere/chain-fusion-starter)

## Provider for (dynamic) NFT assets

Most NFTs in the greater Web3 ecosystem are pointers to off-chain assets. Best practice for these pointers is to use content-addressing with IPFS, and then use a compatible storage network (or a service provider like [Pinata](https://pinata.cloud)) to actually host the assets. However, this is limited to static assets. On the Internet Computer, you can build a service to host assets in canister smart contracts linked to NFTs on the IC itself, but also on other chains. In addition, these assets can be generated in real time according to rules defined in the canister smart contract.

## BtcFi

The [Bitcoin integration](https://internetcomputer.org/bitcoin-integration) allows canister smart contract to hold and transfer BTC. This enables BTC - the asset - rich programmability without reliance on custodians. Since ICP employs the reverse gas model and native account abstraction, you can create a user experience similar to a centralized service. No need for a user to have an ICP native wallet or to hold ICP, just BTC.

For BtcFi ideas, see the [Buidl on Bitcoin RFP](https://github.com/dfinity/grant-rfps/issues/58)


## Document sharing and collaboration

The Internet Computer is well suited to build a credibly neutral decentralized document sharing and collaboration platform for personal use, but also for collaboration between organizations. DFINITY has built an open source prototype called DocuTrack which can be used as a basis.

### Resources

- [DocuTrack Code](https://github.com/dfinity/ic-docutrack?tab=readme-ov-file)
- [Blog Post](https://medium.com/@dfinity/the-dfinity-foundation-announces-the-open-alpha-release-of-docutrack-1dfdf7ea192f)

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

## Registry

The Internet Computer allows building registries, such as

- Package registries (npm, Docker Hub, ...)
- Code repositories (GitHub, GitLab, ...)
  that are not controlled by a single entity.

There is a large design space to explore from completely neutral registries to registries with decentralized governance, as well as tokenomics to incentivize contributions.

### Examples

- [Codebase](https://codebase.org/)
- [MOPS](https://mops.one/)
