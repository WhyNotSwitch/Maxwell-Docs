# Maxwell: A Smart Metering Solution for Decentralized Energy Systems

Maxwell Smart Meter is a game-changing new technology developed by Switch Electric, built on the power of real-time sensors and web3 technologies to enable complex metering services in decentralized energy systems such as microgrids. In the span of just one minute, a smart meter can collect and analyzes over 3,600 data points from several different sensors, including voltage, current, frequency and power factor. Using this data, the meter is able to calculate a very accurate reading of the energy being produced or consumed by any resource connected to it. 
#### Maxwell Gen-2
![image](https://user-images.githubusercontent.com/52095470/230645076-e479f0d7-fa5d-482b-9ab6-a9cff2a46b32.png)

## Hardware Specifications
Maxwell was designed to work with AC inputs ranging from 50-60 Hz and including voltages between 100–240 volts, making it compatible with both European and US grid standards. The utility meter can have one of two types of circuit boards: the first runs on `STM32G4A1KE` and another uses `ATMEGA328`. If remote control switching is required, AC relays are available and a 16MHz quartz crystal oscillator is used to keeps time. Maxwell is available in variants that can accommodate both single-phase and three-phase systems, each drawing about 0.025 W of power on average. The meter is rated for a maximum ambient temperature of 35°C, and its operating temperature range is -25°C to + 55°C. The circuit board itself measures 153.57mm x 103.91mm in size. The public/private key pair are stored on a tamper-resistant chip and cannot be accessed externally without destroying it. The Maxwell is designed to communicate wirelessly via LoRaWAN, a type of long-range, low-power wireless communication protocol that is designed to be used in the internet of things.Our current designs make use of Semtech’s SX1276 modules, which communicate via the LoRaWAN protocol (a long range, low-power communications protocol that is designed for IoT applications).
#### Maxwell PCB Electronics
![image](https://user-images.githubusercontent.com/52095470/230644299-5a05c2d1-e8bd-4a68-b1dd-60f7d8b1db75.png)<br>
#### Feature Summary
- 100A maximum current
- Active energy calculation
- Remote controllable relay
- Programmable sampling rate
- Communication authentication
- True RMS voltage measurement
- Real-time clock synchronization
- Instantaneous current measurement
- -10°C to + 55°C operating temperature

## EVM & W3bstream Integration

Maxwell is built on a special infrastructure; W3bstream, that is developed by the IoTeX network. W3bstream provides an open, decentralized protocol that sits between blockchain and smart devices. it offloads computation so data remains secure. It converts real-world data into verifiable cryptographic proofs dApp can use, without spending a lot on gas fees or having control over the user's data. The W3bstream nodes contain a WebAssembly runtime environment for executing application logic that verifies the digital signature of the received data, decodes it, checks its conditions and generates proof-based outputs based on application-specific algorithms. The proof is then fed into our dApp smart contract where it can trigger tokens/NFT incentives. Read more about w3bstream from the official [whitepaper](https://docsend.com/view/twtxhbzvisdye2xj)
#### W3bstream Node Architecture
![image](https://user-images.githubusercontent.com/52095470/230633247-6cc34b15-f86a-49e0-92b5-18f7aa9e7fe1.png)
The blockchain side consists of a family of EVM smart contracts, which are compatible with any of the many EVM-compatible blockchains such as Ethereum, IoTeX, Polygon. These contracts include 
- A registry contract where new smart meters are whitelisted and bound to there decentralized identities (DIDs)
- An NFT contract that tokenizes these devices and allow on-chain ownership, creates a digital twin of each smart meters and tracks it's real world attributes and states
- A carbon offset tokenization contracts that implements methodologies for generating carbon offset credits from renewable energy generation
- A governance contract use by community members to enact changes to the state of the protocol 

## Cryptographic Signatures and Zero Knowledge Proofs
To ensure data security, the device can secure its data by digitally signing them with the Secp256k1 elliptical curve algorithm and using SHA256 hash functions. This protects against unauthorized access, tampering, or forgery, ensuring that the data received from Maxwell is both accurate and trustworthy. This scheme can also be used to create decentralized identities (DIDs) for every smart meter. A DID is a decentralized identifier that can be used to represent an entity on a blockchain. They are similar to email addresses, but unlike email addresses, they cannot be taken down or censored. Additionally, zero-knowledge proofs are implemented in the w3bstream node to ensure data privacy. They are based on the zk-SNARKS algorithm, which allows for the creation of a proof that does not reveal any information about what it is proving. This ensures that no one can link your data with other users’ data, nor can they learn any personal information about meter users.
#### Elliptical Curve Cryptography On Secure Hardware Element 
![image](https://user-images.githubusercontent.com/52095470/230639899-837d0c97-c09b-419e-ad87-3e07f236675d.png).

## LoRaWAN and Helium Integration
Switch Electric is in the process of bringing Maxwell to Helium's IoT network, which provides LoRaWAN coverage for many devices. Maxwell communicates via this technology and can send data across distances up to 3 km. Integrating Maxwell with Helium's IoT network can enable it to leverage the network's LoRaWAN coverage, which can provide reliable and cost-effective long-range communication capabilities. This can be particularly useful in scenarios where the Maxwell device is located in remote or hard-to-reach areas, or where traditional wireless communication methods may be limited or costly.

## About Switch Electric
Switch Electric is building a web3 metering infrastructure and a platform for tokenizing rooftop solar assets. We aim to create the technological infrastructure needed for a decentralized energy internet and peer-to-peer marketplace, where producers can sell excess energy directly at wholesale prices. We envision a cost-effective decentralized energy internet for all of Africa's 1 billion people by the year 2100.
#### Switch Product Banner
![image](https://user-images.githubusercontent.com/52095470/230646235-3934bc25-aed1-4534-9d89-efcf2097e539.png)

