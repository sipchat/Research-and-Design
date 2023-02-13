# Bring Your Own Server (BYOS)

The ultimate goal of Sichat is letting everyone to own and control the neccessary digital assets as a sovereign individual in the digital age. What differentiate Sichat from other similar decentralized systems is its first principle of "Bring Your Own Server (BYOS)".

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

The design of SN and SIS should handle all hardware configurations and changes. Sichat should provide appropriate services in all cases.

### 2.2 Software Architecture

At the software level, a basic decision is the distribution of funcitons between the server and client. To make the distribution decision, we categorize the functions into three types: client-only, server-only and floating.

- Client-only: client output (presentation logics), client inputs (including keyboards, voice, camera, sensors, locations etc), local storage for cached/offline data, client networking (including data, text, direct link).
- Server-only: IAM (must be reliable and better highly available), real-time receiving/routing messages, blog and transaction server that provides real-time online services.
- Cleint or Server: most functions can run in either the server or the client. The question is which is the primary.

For client or server services, there are many possible models:

- The server performs most functions. It is called `light client (LC)` model. If the server is down or not accessible, the floating services are unavailable.
- The client performs most functions. The server works as a hot standby of its client. It is called `active client (FC)` model.
- Both the client and the server perform a set of pre-assigned non-overlapping functions. It is called `pre-assigned service` model.
- The servicess can run either in client and server. The services dynamically float based on a set of pre-define rules or the client/server availability. It is called `floating service` model.

### 2.3 Model Evaluation

We use a scale of 0 (not working) to 4 (good by most criterias).

| Hardware | Light Client | Full Client | Distributed Function|
| --- | --- | --- | --- |
| Everyone has a server | 4 | 2 (full redundancy) | 3 (some redundancy) |
| Some don't have a server | 1 (Some lose access) | 3 (some redundancy) | 2 (limited services) |
| None has a server | 0 (all lose access) | 3 (limited size) | 2 (limited services) |
| Server is unaccessible | 0 (no service) | 4 | 3 (limited services |
| Add a server | 1 (big change) | 4 | 3 (small change) |
| Remove a server | 1 (big change) | 4 | 3 (small change) |
| Total | 7 | 20 | 19 |

We might want to support all three models and switch models based on hardware status and software service properties.

## How Does It Work?
