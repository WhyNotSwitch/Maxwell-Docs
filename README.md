![image](https://github.com/user-attachments/assets/467064c5-5532-416e-bd5c-063fba8885cb)

# Maxwell: A Smart Metering Solution for Decentralized Energy Systems
The Maxwell is a specialized electricity meter developed by Switch Electric for accurately tracking and cryptographically verifing electricity production / exports of distributed energy resources, such as rooftop solar plants. It is capable of aggregating over 3000 voltage and current data points every minute from its real-time sensors. It is well sutited to bridge the gap between distributed energy resources (such as rooftop solar assets) and the web3.0 economy in use cases such as DePIN, asset tokenziation, onchain energy attributions (such as RECs). 

#### Maxwell Gen-2
Isometric view | Front View
:-------------:|:-----------:
![image](https://github.com/user-attachments/assets/664f7feb-33b0-4f76-9ef8-71eac200eabb) | ![image](https://github.com/user-attachments/assets/d25d2a4d-27b3-4a6a-8131-30c59820e64b)

## Hardware Specifications
Maxwell was designed to work with AC inputs ranging from 50-60 Hz and including voltages between 100–240 volts, making it compatible with both European and US grid standards. If remote control switching is required, AC relays are available and a 16MHz quartz crystal oscillator is used to keeps time. Maxwell is available in variants that can accommodate both single-phase and three-phase systems, each drawing about 0.025 W of power on average. The meter is rated for a maximum ambient temperature of 35°C, and its operating temperature range is -25°C to + 55°C. The circuit board itself measures 93.345x 69.977 in size. The public/private key pair are stored on a tamper-resistant crypto chip (a secure element) and cannot be accessed externally without destroying it. The Maxwell is designed to communicate wirelessly via LoRaWAN, a type of long-range, low-power wireless communication protocol that is designed to be used in the internet of things.Our current designs make use of Semtech’s SX1276 modules, which communicate via the LoRaWAN protocol (a long range, low-power communications protocol that is designed for IoT applications).
![image](https://github.com/user-attachments/assets/15e58ebd-cb4a-4ddb-a33c-568149cf2b4b)
#### Feature Summary
- ED25519 digital signature authentication
- -10°C to + 55°C operating temperature
- Instantaneous current measurement
- Programmable data publishing rate
  - default: every 60 seconds
- True RMS voltage measurement
- Real-time clock synchronization
- 120A maximum current rating
- Remote controllable relay
- Active energy calculation

## Cryptographic Features
![image](https://user-images.githubusercontent.com/52095470/230639899-837d0c97-c09b-419e-ad87-3e07f236675d.png)
The STM32WL55CC microcontroller onboard the device offers robust hardware security features such as secure boot, secure memory, and tamper detection mechanisms. It also incorporates a true random number generator (TRNG) for generating high-quality cryptographic keys and a secure hardware-based key storage mechanism to protect these keys from unauthorized access. The Maxwell employs the ED25519 elliptical curve digital signature algorithm to cryptograhically sign messages and ensure data integrity. These all work together to protect against unauthorized access, tampering, or forgery, ensuring that the data received from Maxwell is both accurate and trustworthy.

## LoRaWAN Integration
![image](https://github.com/user-attachments/assets/aca56f2c-5052-460d-bc92-8497b7eff999)
Maxwell communicates via LoRaWAN (LongFi) technology and can send data across distances up to 3 km. It currently has integration with Dropwireless's LoRa gateways and can also be programmed to work Helium IoT network or alternative LoRaWAN coverage which can provide reliable and cost-effective long-range communication capabilities. This can be particularly useful in scenarios where the Maxwell device is located in remote or hard-to-reach areas, or where traditional wireless communication methods may be limited or costly.

## About Switch Electric
Switch Electric is building a web3 metering infrastructure and a platform for tokenizing rooftop solar assets. We aim to create the technological infrastructure needed for a decentralized energy internet and peer-to-peer marketplace, where producers can sell excess energy directly at wholesale prices. We envision a cost-effective decentralized energy internet for all of Africa's 1 billion people by the year 2100. We believe that the future of energy is decentralized, because it is sustainable and resilient, thus the best way to achieve universal access to energy. 
![image](https://github.com/user-attachments/assets/77bb8a74-caaa-4869-9dc2-ddfa3caa80dd)



