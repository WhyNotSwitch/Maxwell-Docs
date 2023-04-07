# Switch Electric's Maxwell Smart Meter

Switch Electric's Maxwell Smart Meter is an innovative device designed to harness the power of real-time sensors and web3 technologies, enabling complex metering services in decentralized energy systems such as micro-grids. The smart meter collects and aggregates over 3,600 data points per minute across a variety of parameters including energy usage, voltage, frequency, current, and power factor.

### Hardware Specifications
Maxwell was built using the w3bstream infrastructure and is designed to work with AC inputs with 50-60 Hz / 100-240V, making it compatible with both European and US grid standards. The device firmware runs on two microcontroller variants, the STM32G4A1KE variant and the ATMEGA328 variant, with minor price differences. The meters can also come with AC relays for remotely controlling metered load, a 16MHz quartz crystal oscillator for keeping time, and only runs on about 0.025 W of power. Additionally, there are variants of Maxwell available for single-phase and three-phase systems.

### IoTeX and W3bstream Integration
Maxwell was built on the IoTeX network, using a special infrastructure they developed, called w3bstream. W3bstream is an off-chain compute infrastructure serving as an open, decentralized protocol that sits between the blockchain and smart devices to convert real-world data from devices into verifiable, chain-agnostic, dApp-ready cryptographic proofs. The W3bstream nodes verify the digital signature of the received data, decode the data, check the conditions and generate the corresponding proof based on developer-supplied algorithms. The proof is then fed into a dApp smart contract triggering tokens/NFT incentives.

### Cryptographic Signatures and Zero Knowledge Proofs
To ensure data security, Maxwell communicates via LoRaWAN technology and is capable of sending data across distances of up to 3 km. It can secure its data by cryptographically signing them using the Secp256k1 elliptical curve digital algorithm with SHA256 message digest. Additionally, the device is capable of using zero-knowledge proofs to protect user privacy and prevent data leakage.

### LoRaWAN and Helium Integration
Switch Electric is currently working on integrating Maxwell with Helium's IoT network, which provides LoRaWAN coverage for many IoT devices and enables the use of zero-knowledge proofs via W3bstream. This integration will allow Maxwell to transmit data more securely and efficiently, and will help expand the use of decentralized energy systems.


### About Switch Electric
Switch Electric is a metering service provider that offers multiple technology solutions for pre-paid metering, data management, and communications. Our extensive services include installation, configuration, and customization of your meter hardware and communications system, remote diagnostics/monitoring, and software development for energy management systems. Our vision is to enable cost-effective decentralized energy supply for all of Africa's 1 billion people by 2100.
