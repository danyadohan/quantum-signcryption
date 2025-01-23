# Quantum Signcryption: A Next-Gen Secure Communication Tool

This project was submitted as a graduation project in January 2025 by **Danya Al-Jubouri** in partial fulfillment of the requirements for the degree of **Bachelor of Science in Cybersecurity** at **Jordan University of Science and Technology (JUST).**

## Overview

The **Quantum Signcryption** system is a cutting-edge solution designed to provide secure communication by leveraging principles of quantum computing and post-quantum cryptography. It combines both encryption and signature functionalities to ensure **confidentiality, integrity, and authenticity** of transmitted quantum messages. The system makes use of **quantum-secure cryptographic algorithms**, ensuring resistance against classical and quantum adversaries.

## Quantum Signcryption System Flow: A High-Level Overview

The signcryption process involves communication between the sender (**Alice**) and the receiver (**Bob**). Classical information is represented as-is, while **quantum information** is denoted using Dirac notation (e.g., `|ψ>`).

The process consists of two main modules:

1. **Signcryption at Alice’s end:** Encrypts and signs the message.
2. **Unsigncryption at Bob’s end:** Decrypts and verifies the message.

### **System Flow Table**

| Step | Alice (Sender) - Signcryption Steps  | Bob (Receiver) - Unsigncryption Steps |
|------|-------------------------------------|--------------------------------------|
| 1    | Prepare a quantum message `|ψ>`     | Receive encrypted data               |
| 2    | Generate a random classical message `ՠ` | Decapsulate the shared secret          |
| 3    | Generate a classical signature `σ` using private signing key `skA` with Dilithium | Decrypt the encrypted circuit         |
| 4    | Encode `(ՠ,σ)` into quantum state `|ՠ|σ>` | Verify signature with public key `pkA` |
| 5    | Combine `|ψ>` and `|ՠ|σ>` into joint state | Recover original quantum message      |
| 6    | Generate a shared secret using Kyber |                                      |
| 7    | Encapsulate the shared secret       |                                      |
| 8    | Encrypt the joint state using AES   |                                      |
| 9    | Transmit encrypted circuit, IV, and encapsulated secret |               |

> **Limitation:** While the model ensures confidentiality, integrity, and authenticity, it does not guarantee **non-repudiation**, as a malicious receiver could reuse parts of the signcrypted message to forge future messages.

## Quantum Signcryption System Implementation

### **Development Environment Setup**

The system was developed and tested in a structured environment to ensure smooth functionality. The development tools used include:

1. **Visual Studio Code (VS Code):**  
   - Version: `1.96.2`  
   - Used as the primary code editor for integration and debugging.

2. **Miniconda Virtual Environment:**  
   - Used to manage dependencies and isolate the project environment.
   - Installed cryptographic libraries such as **Qiskit, Kyber, and Dilithium.**

3. **Jupyter Notebook:**  
   - Utilized for iterative development, testing, and visualization of quantum circuits.

---

### **Programming Language**

The system is implemented in **Python 3.9**, chosen for its extensive support for quantum and cryptographic libraries.

### **Libraries Used**

The project relies on the following libraries:

1. **Post-Quantum Cryptography:**
   - [CRYSTALS-Dilithium](https://pq-crystals.org/dilithium/)
   - [CRYSTALS-Kyber](https://pq-crystals.org/kyber/)
   
2. **Symmetric Encryption:**
   - AES via the `Crypto.Cipher` module from [PyCryptodome](https://www.pycryptodome.org/)

3. **Quantum Computing:**
   - [Qiskit](https://qiskit.org/)

4. **Data Handling:**
   - Python’s built-in `secrets` module for secure random number generation.
   - `BytesIO` from the `io` module for handling data streams.

---

## Pseudocode

For a high-level algorithmic overview of the signcryption and unsigncryption processes, refer to the [Pseudocode](pseudocode.md) file.

---

## References

1. [Original Model Reference Paper](#)  
2. [CRYSTALS-Dilithium GitHub Repository](https://github.com/pq-crystals/dilithium)  
3. [CRYSTALS-Kyber GitHub Repository](https://github.com/pq-crystals/kyber)  
4. [PyCryptodome Documentation](https://www.pycryptodome.org/)  
5. [Qiskit Documentation](https://qiskit.org/documentation/)
