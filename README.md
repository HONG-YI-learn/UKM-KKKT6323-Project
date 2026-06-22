# 🛡️ Smart Manufacturing Edge Gateway: Hybrid PQC MQTT Architecture

![License](https://img.shields.io/badge/License-MIT-blue.svg)
![Hardware](https://img.shields.io/badge/Hardware-STM32F407%20%7C%20ESP01S-orange)
![Protocol](https://img.shields.io/badge/Protocol-MQTT-green)
![Security](https://img.shields.io/badge/Security-ML_KEM%20%2B%20AES-red)

This repository contains the implementation of an event driven MQTT security gateway tailored for Industry 4.0 predictive maintenance systems. It is designed to neutralize the Harvest Now Decrypt Later quantum security threat while overcoming the severe performance bottlenecks of running heavy post quantum algorithms on resource constrained edge devices.

Through a custom engineered Hybrid Post Quantum Cryptography state machine, this project successfully achieves quantum resistant data transmission at the microcontroller level without disrupting industrial network continuousness.

## ✨ Key Features

* **Innovative Hybrid Scheduling:** Abandons the full payload lattice encryption approach that causes system lockups. Implements a dynamic scheduling strategy utilizing ten percent ML KEM for secure key encapsulation and ninety percent Advanced Encryption Standard for high frequency symmetric encryption.
* **Zero Buffer Shock Optimization:** Solves the physical buffer shock and transmission control protocol fragmentation caused by large ciphertext volumes exceeding one kilobyte. Features low level C optimizations including static memory pool restructuring and timing compensation.
* **Industrial Application Simulation:** Perfectly simulates factory predictive maintenance by securely collecting and publishing long cycle telemetry data such as high frequency vibration differentials and equipment temperatures.

## 🧱 Hardware Architecture

The edge acquisition and transmission loop is executed entirely on local hardware, significantly reducing latency dependence on cloud instructions:
* **Microcontroller Unit:** STM32F407ZG with an ARM Cortex M4 core. Responsible for high frequency data packaging, cryptographic matrix computation, and state machine scheduling.
* **Wireless Transport Module:** ESP01S Wi Fi module. Communicates with the main microcontroller via universal asynchronous receiver transmitter interface and runs a lightweight networking stack.
* **Broker:** Localized Mosquitto MQTT Broker simulating an industrial cloud platform receiving encrypted telemetry.

## 📊 Performance Benchmarks

End to end performance was evaluated under four distinct cryptographic profiles on the identical hardware setup. The empirical data proves that the proposed Hybrid architecture drastically compresses the post quantum latency and achieves a flawless zero percent packet loss rate.

| Cryptographic Profile | Average Latency | Maximum Jitter | Packet Loss Rate | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Baseline Plaintext** | 25.4 ms | 1295.6 ms | 4.8 % | ⚠️ Insecure |
| **Transport Layer Security 1.3** | 84.0 ms | 4525.4 ms | 4.4 % | ⚠️ Vulnerable to quantum attacks |
| **Full ML KEM** | 1807.4 ms | 5050.5 ms | 6.3 % | ❌ Causes system lockups |
| **Hybrid PQC Architecture** | **579.2 ms** | **5651.3 ms** | **0.0 %** | ✅ **Secure and highly reliable** |

## 📂 Directory Structure

```text
├── Core/                  # Initialization routines interrupt handlers and main operational loop
├── Drivers/               # Microcontroller system files and STM32 Hardware Abstraction Layer
├── Hardware/              # Custom drivers including Delay LED UART and ESP01S Wi Fi modules
├── Middlewares/           # Third party libraries and cryptographic protocol implementations
├── STM32F407ZGTX_FLASH.ld # Linker script defining static memory pool allocations
└── README.md              # Project documentation and architectural overview
