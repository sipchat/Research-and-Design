# Sovereign Individual Identity: An Autonomous Triad of User, Identify Provideer and Service Provider

## 1 Introduction

The [NIST][1] defines a digital identity as "the unique representation of a subject engaged in an online transaction.". In practice, a digital identity represents the information that uniquely identifies a specific individual, group, or organization in its social context. A digital identity system is called an identity and access management (IAM) because the primary usage of an identity is for access control. There are sevearl IAM models during its evolution:

- Isolated: service provider is also identity provider
- Centralized: separate identity provider such as PKI and CA.
- Federated: signle sign-on enabled by a trusted fedrattion of a set of sevice providers and identity provders.
- User-centric: user can choose identify provider. OAuth and OpenID.
- User-owned identity: PGP and Self Sovereign Identity

Among all the models, the self-owned identity has strong social and technical requirments.

An IAM has three actors: user, identity provider and service provider. A user represents a specific individual, group or organization. An identitiy providere manges a user's idnentity informaiton. A service provider provides services based on the information provided by either a user or an identity provider. This research proposes a new type of IAM based on self-owned identity: sovereign individual identity (SII). SII is a triad of three actors: the user, identity provider and service providers are integrated into a single independent system, fully owned and managed by its user. A network of SII works in a peer-to-peer manner to provide identity and other digital services to each other.

## 2 Literature Review and Motivation

The social and technical motivation for Self-owned identity.
The pros and cons of PGP, SSI, Agent and digital wallet.
SII meets the [10 principles][2]/requirements of a self-owned identity.

## 3 The Design

The description of SII architecture, how different components work together. As a first step, we use a Chat app as its application context. Extension to other applications are covered.

At a high level, it is an autonomous triad of user, identity provider and service provider. SII has all actors of verfiable credentils: issuer, holder, verifier and verifable data registry.

## 4 The Implementation

The decison of implementation details: the address, the API, the storage, the recovery, the admin, the operation etc.

## 5 The Use Cases

Different use cases in the Chat app and other applications.

## 6 Discussions

Pros and cons of SII.

## 7 References

[1]: https://pages.nist.gov/800-63-3/sp800-63-3.html "Digital Identity Guidelines"
[2]: http://www.lifewithalacrity.com/2016/04/the-path-to-self-soverereign-identity.html "The Path to Self-Sovereign Identity"
