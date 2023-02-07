# Sovereign Individual Identity

This document is a high level design of Sovereign Individual Identity . We use the term "Sovereign Individual Identity (SII)" to differentiate it from the "Self Sovereign Identity (SSI)" because most SSI implementations are associated with block chain. A true soverign identity should not depend on any thir party service, regardless the service is centrilized or decentralized. An SII system must allow one to issue and manage one's identifier in an independent, secure and reliable way. An identifier is a label representing an SII. An SII may have many identifiers in different use contexts. In the following sections, the term `identifer` refers to an SII identifier (SIII).

## 1 Introduction

Essentailly, an identifier is a pair of public key and private key. For evolution and flexibility, an identifier includes the alogrithm name used to create the key pair. It has two optonal parts:

- a list of names: they are human-friendly names used in different contexts. Most identity has one or more names. It is optional because a public key or, as we see in many block chain implementations, a hash of a publich key can be used as one's identifier.
- an identity service URI: it is an address of the identity service.

All private keys (and algorithm name ?) should be protected from unauhtorized access. There should be some recovery mechanisms to restore the data when the authorized access is lost/damaged.

A Sichat client works in one of two modes:

- Full client (FC): an FC has a corresponding server. Its SIIIs are stored both locally and in its server. It is up to each individual FC to define and implement its key recovery mechanism. An FC only communicates with its server.
- Weak client (WC): a WC doesn't have a server. We use the term "weak" to highlight that the WMC is not reliable and is not recommended for a soverign individual. A WC's SIIIs are stored only in simple mode clients. When a WC is lost, the group server may bind a chat name with a new public key. The new binding will generate a public name binding event. A WC communicates with one or more servers of other FCs.

Evey client has a device-related key pair used to identify each device. An FC stores all SIII key pairs and its device key pairs in its server.

## 2 Sichat

### 2.1 FC Initialization

The life of an SII starts with an FC initialization. During Sichat client installation, when one selects full client,the client will ask the user to set the following parameters:

- a cloud service provider that hosts the Sichat server
- a registered domain name
- a username for chat

The client will initialize both the server and client

- Server
  - create the Sichat server
  - bind the domain name
  - bind the domain name with an auto-renew certificate for HTTPS
-Client
  - create an identifier for an `admin` identifier -- all administration tasks are performed with the `admin` id. All other ids except this one can be deleted. When an id is deleted, all its assoicated data is deledted.
  - create an identifier for the chat username.

### 2.2 WC Initialization

When a user selects weak client, the WC generate an identifier and ask for a chat username. The public key and the user name is used to join a chat room.

### 2.3 Join a Chatroom

If the username exists already in a chatroom, the user is promoted to change the username or create a new username for the chatroom. A client can always create a new identifier and assoicate it with a username in any context as long as the username is unique in the context.

## 3 Verifiable Credentials (future)

An FC's server play three roles in SII: as the issuer, as the holder and as the verifier. It can provide services for verfiable credentials for other servers (working as verifiers). All servers create a web of trust. It is fully decentralized. P2P communication protocol and routing algorithms are to be developed to make it scalable at the web scale.
