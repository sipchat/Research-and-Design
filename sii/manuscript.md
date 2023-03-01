# Sovereign Individual Identity: An Autonomous Triad of User, Identify Provider and Service Provider

## Abstract

Sovereign Individual Identity (SII) is a new identity management (IDM) model that provides independent existence and full control of a subject's identity. What differentiate SII from other user-owned identity is that it is an autonomous triad of user, identity provider, and service provider. A typical SII-based IDM system has a subject owned server that provides fundamental functions of computation, storage and communication used by identity management. The server and its clients of mobile phones/PCs form an identity management closure that provides the independency, full control and many other desired properties required by a sovereign individual in one's digital life. The proposed SSI is discussed in the context of communication and expression, arguably two basic activities in one's digital life.

## 1 Introduction

The [NIST][1] defines a digital identity as "the unique representation of a subject engaged in an online transaction.". In practice, a digital identity represents the information that uniquely identifies a specific individual, group, or organization in its social context. There are several Identity Management (IDM) models during its evolution:

- Isolated: service provider is also identity provider
- Centralized: separate identity provider such as PKI and CA.
- Federated: single sign-on enabled by a trusted federation of a set of service providers and identity providers.
- User-centric: user can choose identify provider. OAuth and OpenID.
- User-owned identity: PGP, Bitcoin/Ethereum and Self Sovereign Identity

Among all the models, the self-owned identity has strong social and technical requirements.

An IAM has three actors: user, identity provider and service provider. A user represents a specific individual, group or organization. An identity provider manages a user's identity information. A service provider provides services based on the information provided by either a user or an identity provider. This research proposes a new type of IAM based on self-owned identity: sovereign individual identity (SII). SII is a triad of three actors: the user, identity provider and service providers are integrated into a single independent system, fully owned and managed by its user. A network of SII works in a peer-to-peer manner to provide identity and other digital services to each other.

## 2 Literature Review and Motivation

The social and technical motivation for user-owned identity.
The pros and cons of PGP, SSI, Agent and digital wallet.

[Allen][2] proposed 10 principles of a SSI. Existence and control are two essential principles that truly define a user-owned identity.

[Neuman][3] identified the need for closure in distributed system.

## 3 The Design

The description of SII architecture, how different components work together. As a first step, we use a Chat app as its application context. Extension to other applications are covered.

At a high level, it is an autonomous triad of user, identity provider and service provider. SII has all actors of verifiable credentials: issuer, holder, verifier and verifiable data registry.

## 4 The Implementation

The decision of implementation details: the address, the API, the storage, the recovery, the admin, the operation etc.

## 5 The Use Cases

Different use cases in the Chat app and other applications.

## 6 Discussions

Pros and cons of SII.

## 7 References

[1]: https://pages.nist.gov/800-63-3/sp800-63-3.html 'Digital Identity Guidelines'
[2]: http://www.lifewithalacrity.com/2016/04/the-path-to-self-soverereign-identity.html 'The Path to Self-Sovereign Identity'
[3]: https://dl.acm.org/doi/abs/10.1145/70730.70735 'The need for closure in large distributed systems'
