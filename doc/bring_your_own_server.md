# Bring Your Own Server (BYOS)

The ultimate goal of Sichat is letting everyone to own and control the neccessary digital assets as a sovereign individual in the digital age. What differentiate Sichat from other similar decentralized systems is its first principle of "Bring Your Own Server (BYOS)".

## Why BYOS?

Merriam-Webster defines [sovereign](https://www.merriam-webster.com/dictionary/sovereign) as "possessed of supreme power; unlimited in extend; enjoying autonomy". To be a sovereign individual in the gitial age, a person should independently own and fully control his/her digital assets and social activities within a limited sphere. As the first principle, an individual needs to own essential hardware and software resourcces to exist and live digitally. It is named as "Bring Your Own Server (BYOS)" to represent the following essentail hardware and software resources:

- Hardware: computer, storage, and network.
- Software: identity and access management (IAM) and communication.

The hardware resources include the basic physical equipments for computation, data storage and data communication. An individual should own and has full control of these resources. Technically, the equipments can be in one's own places, or more commonly, are leased from a cloud service provider. Because an individual's digital life depends on the hardware resources, these resources must be highly availabe, highly reliable, highly scalable, economically feasible, and easy to use. The term `Server` highlights these non-functional requirements. Today, a leased server and storage space from a cloud service provider fulfills most requirements. However, a home computer or a smart phone is not a server by the above definition. For example, a smart phone is not a qualified server though it combines computer, storage and newtwork components. A smart phone can be offline or turned off frequently. To make it worse, it could be lost forever. Due to its small size and limited expandablity, it is not scalable in computation, storage and bandwidth. However, due to its mobility and rich functions, it is the UI to the server operations.

BYOS is an necessity for both IAM and communication. An identity is a basic requirment in most social interactions. There are three basic roles in an IAM system to manage identity(ID) or the more general verifiable credential(VC): issuer, holder, and verifier. An independent and autonomous IAM system requires a sovereign individual's server to play all three roles. The IAM system should alwasy work even when an individual is offline. The ID data requires secure and reliable storage.

Similarly, an individual should always be able to receive messages and store messages in a secure and reliable way.

Conversly, without BYOS, an individual either has to rely on a third party or occasionally lose identity and communication services. The individual is not a sovereign individual in both cases.

## What's It?

The Sichat consists of many decentralized P2P overlay networks running on top of physical networks such as the Internet or telecom networks. Each Sichat network has one or more Sovereign Individual System(SIS)s. An SIS may join mutiple Sichat networks. There is a many-to-many relationship between a Sichat network and an SIS. An SIS consists of a pair of server and client. A server is a combination of computer, storage and network connection running in the cloud. The server provides the IAM and communication services to its owner and other authorized indidviduals. A client is a smart phone, Pad or a PC that let the individual use and manage all services. A client provides the UI and local storage for cached/offline data.

In practice, many individuals don't need the high availibity and reliability or a group of individuals only needs one server to provide the desired quality of service. In this case, they can use a weak individual system (WIS). A WIS runs in a smart phone or a personal computer thus it is not always online. A WIS has all functions of an SIS. It is weak in the sense that it may go offline anytime or is offline most of the time. A WIS may optionally setup a backup storage in case an individual losts the device. A WIS can upgrade to an SIS when the individual setup a server.

For different networks or different services, a client may work in one of two modes:

- Full client (FC): an FC has a corresponding server. Its SIIIs are stored both locally and in its server. It is up to each individual FC to define and implement its key recovery mechanism. An FC only communicates with its server.
- Weak client (WC): a WC doesn't have a server. We use the term "weak" to highlight that the WMC is not reliable and is not recommended for a soverign individual. A WC's SIIIs are stored only in simple mode clients. When a WC is lost, the group server may bind a chat name with a new public key. The new binding will generate a public name binding event. A WC communicates with one or more servers of other FCs.

Evey client has a device-related key pair used to identify each device. An FC stores all SIII key pairs and its device key pairs in its server.

## How Does It Work?
