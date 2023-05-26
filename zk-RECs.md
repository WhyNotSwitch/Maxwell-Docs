# Energy Metering and Verification For on-chain RECs
##### The Renewable Energy Certificate 
![image](https://user-images.githubusercontent.com/52095470/233071669-b34b36f7-332e-43f0-acb9-fd8d1aa99a49.png)

While tokenizing Renewable Energy Certificates on the blockchain has the potential to enhance transparency, accountability, and efficiency; The process for is still somewhat manual. The data sources are varied across projects and not always trustworthy, and sometimes, the project developers would have to manually enter the information on-chain to get it all done. This is especially true for small-scale renewable energy developers such as microgrids and rooftop solar companies, which tend not to have in place the kind of SCADA systems used by major power utilities.

Switch Electric has been able to develop an energy meter (codenamed Maxwell) that allows for trustless monitoring, reporting and verification of energy outputs. The technology utilizes hardware-based cryptography, zero-knowledge proofs, along with a decentralized infrastructure network "w3bstream", developed by the IoTeX devs. We developed our proof of concepts and commercial prototypes with [grant funding from the IoTeX foundation](https://community.iotex.io/t/accepted-iotex-enabled-energy-service-by-switch-electric/9247). We will also be working closely with a number of other energy projects on web3—including Arkreen Network, Solarpunk DAO, Solar Foundation (Helios DAO + Spark Eco)—to utilize the technology in issuing RECs (or carbon credits). We are seeking to raise *$56,000* in grant funding so we can expand the use of this technology, develop standards for its implementation and scale up it's existing use-case.
##### Maxwell Gen-2
![image](https://user-images.githubusercontent.com/52095470/233105188-3ff655d7-8567-43f9-9715-90c23a991770.png)

### Expected Impact:
This technology can be used to make the quality of on-chain renewable energy certificates more consistent, which will increase demand for these RECs and help speed up the transition to a sustainable energy system. Also, by enabling small scale rooftop solar projects in the global south to participate in the renewable energy market and mint RECs on the blockchain, this project can ensure that the RECs represent real and measurable renewable energy, and provide a new source of revenue for small scale project owners. In addition, the project will create jobs and economic opportunities in the manufacturing, deployment, and maintenance of the IoT devices, and contribute to the development of local renewable energy markets.


## Behind the circuits 
So you are willing to learn the nitty-gritty of how things work. Let's get started!

### The hardware component
It all starts with the secure chip on the meter which generates and securely stores a private key. Maxwell uses the Secp256k1 elliptical curve algorithm and SHA256 hash functions to sign its data. This protects against unauthorized access or tampering, ensuring that all of Maxwell's information is accurate and trustworthy. The chip itself is used to sign messages using the private key, while we use the hash of its public key as the unique identifier or DID for that device. A DID is a decentralized identifier that can be used to represent an entity on a blockchain. They are similar to email addresses, but unlike email addresses, they cannot be taken down or censored. For every message, we affix a digital signature along with some metadata—about the signature scheme, elliptical curve and hash function—to let the receiver's software know how to verify our signature.
##### Elliptical Curve Cryptography On Secure Hardware Element 
![image](https://user-images.githubusercontent.com/52095470/230639899-837d0c97-c09b-419e-ad87-3e07f236675d.png)
Maxwell runs on the open source ATMEGA328 microcontroller, or the more advanced STM32G4A1KE control unit. It includes a 16MHz quartz crystal oscillator for accurate time-keeping and AC relays used for remote switching—and only draws about 0.025 W of power on average. Maxwell was created to work with alternating current inputs ranging from 50-60 hertz and voltages between 100–240 volts—making it compatible with both European and US standards.

The meter is rated for a maximum ambient temperature of 35°C, and its operating temperature range is -25°C to + 55°C. The circuit board itself measures 153.57mm x 103.91mm in size. Our current designs make use of Semtech’s SX1276 modules for LoRaWAN, a type of long-range, low-power wireless communication protocol that is designed for IoT.
##### Maxwell PCB Electronics
![image](https://user-images.githubusercontent.com/52095470/230644299-5a05c2d1-e8bd-4a68-b1dd-60f7d8b1db75.png)
##### Maxwell PCB (In-Real-Life)
![image](https://user-images.githubusercontent.com/52095470/233090967-af2c7cdd-2764-412b-b4fb-1e6e900d67cd.png)


### The w3bstream component
Maxwell is utilizes a special infrastructure; W3bstream, that is developed by the IoTeX network. W3bstream provides an open, decentralized protocol that sits between blockchain and smart devices. it consists of a number of component parts 

- WebAssembly virtual machine & execution engine
- Virtual file system and an SQL database system
- SSI wallet implementation for w3bstreams DID
- Service endpoints for MQTT, HTTPS, RPC communication between blockchain nodes and smart devices.

##### W3bstream Node Architecture
![image](https://user-images.githubusercontent.com/52095470/230633247-6cc34b15-f86a-49e0-92b5-18f7aa9e7fe1.png)
    
The W3bstream nodes contain a WebAssembly runtime environment for executing application logic that verifies the digital signature of the received data, decodes it, checks its conditions and generates proof-based outputs based on application-specific algorithms. The proof is then fed into our dApp smart contract where it can trigger REC issuance. Read more about w3bstream from the official [whitepaper](https://docsend.com/view/twtxhbzvisdye2xj)
    
On the W3bstream network, we have implemented our meters backend logic as a WASM module (also known as an applet). This applet contains the application logic that verifies digital signatures on received data and decodes it before passing it as input to the WebAssembly runtime environment for computation and storage. This approach allows us to keep user data private and secure, while also ensuring that it is available for the necessary computations without having to rely on a centralized server. It also offloads a lot of this computation from the blockchain and as a result reduces the gas cost of our dApps. W3bstream can also be set up to monitor blockchain logs and listen for events emitted by our dApp's smart contracts. However, this feature and other blockchain functionalities only work with EVM compatible blockchains for now.
    
### The Smart contract component
##### Multi-facet contract (aka Diamond contract)
![image](https://user-images.githubusercontent.com/52095470/233072933-58c8045e-e23c-4443-92b3-47a2ff83630e.png)

The smart contract component consists of a number of different contracts that execute various facets of the dApp. The most significant one are:
- A registry contract where new smart meters are whitelisted and bound to there decentralized identities (DIDs). This ensures that only registered devices can be integrated into the dApp. Each meter is also mapped to an energy pool, which essentially is a pointer to a smart contract, where it contributes towards the issuance of RECs.
- An NFT contract that tokenizes these devices and allow on-chain ownership, creates a digital twin of each smart meters and tracks it's real world attributes and states; such as device provider, switch mode, activity status etc.
- The last, but certainly not least important contract is the energy pool which implements minting and retirement functionalities of our RECs. It is also based on the ERC721 NFT standard 
These contracts form the interface through which device manufacturers, device owners, project developers, other contracts and members of the public are able to interact with our decentralized application.

### Summarizing all this in a scenario
Suppose you are a solar energy provider with 167 rooftop installations in Bangladesh or Uganda. You can start to benefit from the renewable energy certificate (REC) subsidy by issuing these certificates as part of your existing business, but this is currently difficult if not impossible via conventional means. Our smart meters are able to break this convention by accurately tracking the energy yields from each of your installations. This data is collected on the meters, signed and transmitted over LoRaWAN—then you can deploy your tokenization contract (aka energy pool) in order to pool all these yields together into single RECs and register your meters to it.
##### In zk-proofs we trust
![image](https://user-images.githubusercontent.com/52095470/233069705-045b3fad-bf26-4703-92ef-89cb277ca68d.png)

To issue a new Renewable energy certificate, you would call the mint function in your energy pool contract. This contract call would result in the emission of an event on the blockchain, which is picked up by w3bstream and triggers a computation based on zkSNARK to generate proofs. In response to this event, w3bstream sends the generated proof back to your energy pool contract—allowing it to verify that your meters have indeed produced sufficient renewable energy in the given time period. Then, it stores this proof on-chain and mints a new REC to your account.

We appreciate your time and consideration of our project, which we believe has the potential to significantly improve the quality and reputation of on-line RECs while simultaneously onboarding a lot of small projects into this market.
