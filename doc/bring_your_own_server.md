# Bring Your Own Server (BYOS)

The ultimate goal of Sichat is letting everyone to own and control the neccessary digital assets as a sovereign individual in the digital age. What differentiate Sichat from other similar decentralized systems is its first principle of "Bring Your Own Server (BYOS)". This document discusses why we choose BYOS, its design choices and implementation resources.

## 1 Why BYOS?

Merriam-Webster defines [sovereign](https://www.merriam-webster.com/dictionary/sovereign) as "possessed of supreme power; unlimited in extend; enjoying autonomy". To be a sovereign individual in the gitial age, a person should independently own and fully control his/her digital assets and social activities within a limited sphere. As the first principle, an individual needs to own essential hardware and software resourcces to exist and live digitally. The principle is named as "Bring Your Own Server (BYOS)" to represent the following essentail hardware and software resources:

- Hardware: computer, storage, and network connection.
- Software: identity and access management (IAM) and communication.

The hardware resources include the basic physical equipments for computation, data storage and data communication. An individual must own and has full control of these resources. Technically, the hardware resources can be in one's own places, or more commonly, are leased from a cloud service provider. Because an individual's digital life depends on the hardware resources, these resources must be highly availabe, highly reliable, highly scalable, economically feasible, and easy to use. Bring Your Own Server (BYOS) is the answer to these requirments.,Today, a leased server and storage space from a cloud service provider fulfills most requirements.  The term `Server` represents the computer/storage/network connections and highlights the availability, reliablity and scalability requirements. A home computer or a smart phone is not a server by the above definition. For example, a smart phone is not a qualified server though it combines computer, storage and newtwork components. A smart phone can be offline or turned off frequently. To make it worse, it could be totally lost, forever. Due to its small size and limited expandablity, it is not scalable in computation, storage and bandwidth.

In terms of software functions, BYOS is an necessity for both IAM and communication. An identity is a basic requirment in most social interactions. There are three basic roles in an IAM system to manage identity(ID) or the more general verifiable credential(VC): issuer, holder, and verifier. An independent and autonomous IAM system requires a sovereign individual's server to play all three roles. The IAM system should alwasy work even when an individual is offline. The ID data requires secure and reliable storage.

Similarly, an individual should always be able to receive messages and store messages in a secure and reliable way.

Conversly, without BYOS, an individual's hardware such as a smart phone or a PC will have a limited availability, reliability and scalability:

- availability: the client is often offline.
- reliability: the client, compared with a cloud server, has a high probability of failure or data lose. Identity data and other important must be stored in other safe places.
- scaliability: the client has limited capacity in computation, storage and communication. It keeps only the recent data.

Without BYOS, an individual either has to rely on a third party or occasionally lose identity and communication services. The individual is not a sovereign individual in the first case. In the second case, the individual occasionally loses digital access or, much wrose, totally loses digital identity. Both are unacceptable situations in digital age. Nonetheless, due to their increasing process power and mobility/locality, smart phones, pads, laptops, or PCs provide UI and cached/offline data for an individual's digital life. A smartphone/Pad/laptop/PC used by an individual in the digital world is called a `client`.

Therefore, to live a fully automous life in the digital age, an individual needs to follow the BYOS principle.

## 2 What's a Sovereign Network and Sovereign Individual System(SIS) ?

The Sichat consists of many decentralized P2P overlay networks, called `sovereign network (SN)`, running on top of physical networks such as the Internet or telecom networks. Each Sichat network has one or more `Sovereign Individual System(SIS)`s. An SIS may join mutiple Sichat networks. There is a many-to-many relationship between a Sichat network and an SIS. An SIS consists of a pair of server and client. A server is a combination of computer, storage and network connection running in the cloud. The server provides the IAM and communication services to its owner and other authorized indidviduals. A client is a smart phone, Pad or a PC that let the individual use and manage all services.

There are many detail design decisions to be made in both hardware and software levels.

### 2.1 Hardware Architecture

At the hardware level, does everyone have a server in a sovereign network? There are three possible cases:

- Every individual has a server.
- Some individuals don't have a cloud server.
- Nobody has a cloud server.

Things become complicated because the network status is dynamice: all dividuals in a sovereign network may lose access to their servers because they are all in a location without Internet access. An individual without a server initially may want to creat a server. An individual with a server initially may want to remove the server.

In practice, many individuals don't need the high availibity and reliability. A group of individuals only needs one server to provide the desired quality of service. Some individuals cannot own a server for reasons such as age, knowledge, and accessibility

Additionally, even every individual in a sovereign network has a server, there is no need to run every service or keep all data in all servers.

The design of SN and SIS should handle all hardware configurations and changes. Sichat should provide appropriate services in following cases:

- Basic Settings
  - No server
  - One server
  - Multiple servers
- Add a server in  basic settings
- Remove a server in basic settings

### 2.2 Software Architecture

At the software level, a basic decision is the distribution of funcitons between the server and client. To make the distribution decision, we categorize the functions into three types: client-only, server-only and floating.

- Client-only: client should be able to issue identity, send/receive message and verify digital signature. Other functions include client output (presentation logics), client inputs (including keyboards, voice, camera, sensors, locations etc), local storage for cached/offline data, client networking (including data, text, direct link).
- Server-only: IAM services that must be reliable and better highly available and secure permanent data storage. For example, VCs that need online service are issued by Server IAM service. Other functions include real-time receiving/routing messages, blog and transaction server that provides always-on real-time online services.
- Flexible: most functions can run in either the server or the client. The questions are 1) which is the primary place to run and 2) switch the place or not.

For each flexible service, there are four possibilities: fixed in server, fixed in client, dynamic default in client, dynamic default in server. Together, all flexible services can be distributed in many possible models:

- The client performs minimum functions. It is called `light client (LC)` model. If the server is down or not accessible, most services are unavailable.
- Both the client and the server perform a set of pre-assigned non-overlapping functions. It is called `fixed services (FS)` model.
- The client performs most functions. The server works as a hot standby of its client. It is called `active client (AC)` model.
- The servicess can run either in client and server. The services dynamically change running platform based on a set of pre-define rules or the client/server availability. It is called `dynamic services (DS)` model.

### 2.3 Model Evaluation

We use a scale of 0 (not working or hard to implement) to 4 (working very well or easy to implement). The number is relative to other models for the same criterion.

#### 2.3.1 Light Client (LC)

The LC model has a simple client software (4) and a relatively simple server software (4).

- Basic Settings
  - No server (0): not working.
  - One server (3): it works well in small to medium scale (the server is assumed highly available, scalable and reliable).
  - Multiple servers (4): it works well.
- Add a server
  - No server to one server (4): it is simple to set a server.  
  - One server to multiple servers (4): it adds server-to-server protocol.
- Remove a server
  - One server to no server (0): not working
  - Multiple servers to one server (3): it is simple.

#### 2.3.2 Static Service (SS)

In SS model, the client and server have a balanced software functions but a key decision is that client doesn't support P2P communication. Software are simple as they have fixed running platform. Client software (4), server software (4).

- Basic Settings
  - No server (0): it doesn't have P2P communication.
  - One server (4): it works in small scale because all server functions are running in one server.
  - Multiple servers (4): it works well.
- Add a server
  - No server to one server (4): it is simple to do.  
  - One server to multiple servers (4): it works well.
- Remove a server
  - One server to no server (0): not working
  - Multiple servers to one server (4): it works in a limited scale.

#### 2.3.3  Active Client (AC)

In AC model, the client runs most functions and share many software code with the server. There are two cons: the software is more complicated and the service switching is hard to do correctly because the client goes offline frequently. Client software (2), server software (2).

- Basic Settings
  - No server (4): it works in p2p mode in small scale. It needs to buffer messages if peers are offline. It has limited use scenarios.
  - One server (3): it works well in small to medium scale (the server is assumed highly available, scalable and reliable). The server is not fully utilized.
  - Multiple servers (3): It work well in small and large scale. Servers are not fully utilized.
- Add a server
  - No server to one server (4): it just adds a standby server.  
  - One server to multiple servers (4): it adds one more standby server.
- Remove a server
  - One server to no server (4): it loses the standby server.
  - Multiple servers to one server (4): it loses one standby server.

#### 2.3.4 Dynamic Service (DS)

The DS model is similar to AC model that they both support service switching. But DS model has an important difference: the services are distributed in both server and client by default and the migration rules are flexible. In DS model, both client and server softare are complext to support smooth service migration. Client software (2), server software (2).

- Basic Settings
  - No server (3): it works in p2p mode in small scale. It needs to buffer messages if peers are offline. It has limited use scenarios.
  - One server (4): it works well.
  - Multiple servers (4): It works well in small and large scale.
- Add a server
  - No server to one server (4): it migrates services.  
  - One server to multiple servers (4): it migrates more services.
- Remove a server
  - One server to no server (3): it needs service migration.
  - Multiple servers to one server (4): it migrates some services.

#### 2.3.6 Score Summary

| HW/SW | LC| SS | AC | DS |
| --- | --- | --- | --- | --- |
| Client SW | 4 | 4 | 2 | 2 |
| Server SW | 4 | 4 | 2 | 2 |
| 0 server | 0 | 0 | 4 | 3 |
| 1 Server | 3 | 4 | 3 | 4 |
| Many Servers | 4 | 3 | 4 | 4|
| 0 to 1 | 4 | 4 | 4 | 4 |
| 1 to many | 4| 4 | 4 | 4 |
| 1 to 0 | 0 | 0 | 4 | 4|
| many to 1 | 4| 4 | 4 | 4 |
| Summary | 27 | 28 | 30 | 31 |

The dynamic service model might be the best because it is the most flexible one. However, it might be the most difficult one in term of design and implementation.

## How to Implement?

The dynamic service deisgn model requires careful analysis of each service. We can start with the following resources:

- [Conduit](https://gitlab.com/famedly/conduit): a Rust Matrix server that uses Light Client (LC) model.
- [Matrix Rust SDK](https://github.com/matrix-org/matrix-rust-sdk): a Rust client SDK.
- [Are we P2P yet?](https://arewep2pyet.com/): Matrix P2P progress.
- [Are we OIDC yet?](https://areweoidcyet.com/): Matrix OpenID Connect (OIDC) authentication progross.

For client software, there are two choices:

- [FluffyChat](https://gitlab.com/famedly/fluffychat): a Flutter-based Matrix client.
- [Element X iOS](https://github.com/vector-im/element-x-ios): a new SwfitUI client based on Matrix Rust SDK. There is a Kotlin-based Androd client based on the same Matrix Rust SDK.

The choice between the native (SwiftUI) vs cross-platform (Flutter) is not easy, especially considering that the client will use Matrix Rust SDK and implment most server side functions in Rust. This makes the UI/presentation layer pretty thin. SwiftUI has better native platform support and easier integration with Rust (?) than Flutter. Because the UI layer is thin, Flutter wins for the following reasons:

- A single code repository for Rust and Flutter
- Cross-platform
- A single IDE (VSCode) for Rust and Flutter
- Both Flutter and FluttyChat are more mature than the SwiftUI conterparts

From here, it is so much fun to figure our how to implement SiChat: sovereign networks based on sovereign individual systems.
