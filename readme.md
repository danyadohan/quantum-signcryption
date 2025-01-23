# Quantum Signcryption: A Next-Gen Secure Communication Tool

This project was submitted as a graduation project in January 2025 by **Danya Al-Jubouri** in partial fulfillment of the requirements for the degree of **Bachelor of Science in Cybersecurity** at **Jordan University of Science and Technology.**

## Overview

The Quantum Signcryption system is a solution designed to provide secure communication by leveraging principles of quantum computing and post-quantum cryptography. It combines both encryption and signature functionalities to ensure confidentiality, integrity, and authenticity of transmitted quantum messages. The system makes use of **quantum-secure cryptographic algorithms**, ensuring resistance against classical and quantum adversaries.

## Quantum Signcryption System Flow: A High-Level Overview

The signcryption process involves communication between the sender (**Alice**) and the receiver (**Bob**). Classical information is represented as-is, while **quantum information** is denoted using Dirac notation (e.g., `|ψ>`).

The process consists of two main modules:

### **Signcryption Process (Alice):**
1. Alice prepares a quantum message `|ψ>`.
2. Alice generates a random classical message `ՠ`.
3. Alice generates a classical signature `σ` for `ՠ` using her private signing key `skA` and a quantum-secure digital signature algorithm, such as **Dilithium**.
4. Alice encodes `(ՠ,σ)` into a quantum state `|ՠ|σ>`.
5. Alice combines the encoded quantum state with the original quantum message to produce the joint state `|ψ> ⊕ |ՠ|σ>`.
6. A shared secret is generated using a post-quantum key encapsulation mechanism, such as **Kyber**.
7. Alice encapsulates this shared secret.
8. Alice uses the shared secret and an initialization vector (IV) to encrypt the joint state `|ψ> ⊕ |ՠ|σ>` using a symmetric encryption algorithm (e.g., AES).
9. Alice transmits the encrypted circuit, the IV, and the encapsulated shared secret to Bob.

### **Unsigncryption Process (Bob):**
10. Upon receiving the encapsulated shared secret, Bob decapsulates it using his private decryption key `dkB` to recover the shared secret.
11. Bob decrypts the encrypted circuit using the recovered shared secret and the IV.
12. Bob verifies the signature using Alice's public verification key `pkA`, and at the same time, recovers the original quantum message `|ψ>`.

> **Limitation:** While the model ensures confidentiality, integrity, and authenticity, it does not guarantee **non-repudiation**, as a malicious receiver could reuse parts of the signcrypted message to forge future messages.

---

### **System Flow Table**
# Table Representation for Quantum Signcryption System Flow
This table provides deeper insight into the steps mentioned above, explaining the goal, mechanism, and inputs/outputs for each step. Steps 1-4 represent the Signcryption process, while steps 5-7 represent the Unsigncryption process.

| #  | Step                          | Goal                                                                 | How It Works                                                                     | Inputs/Outputs                                                |
|----|-------------------------------|----------------------------------------------------------------------|----------------------------------------------------------------------------------|--------------------------------------------------------------|
| 1  | Quantum message preparation   | To prepare the original quantum message `|ψ>` that Alice wants to send to Bob. | Initialize a quantum state for Alice’s message, using properties like superposition and entanglement. | **Output:** the quantum message `|ψ>`, stored in a quantum register. |
| 2  | Classical message preparation | To write the classical message that Alice wants to send.              | Alice writes her message that she wants to send securely.                         | **Output:** Alice’s message `ՠ`.                               |
| 3  | Classical signature generation | To generate a quantum-secure classical signature for Alice’s `ՠ`, which will be sent along with the quantum message. | Use a quantum-secure digital signature scheme (e.g., Dilithium) to sign the message `ՠ`, using Alice’s private signing key `skA`. | **Input:** Alice’s message `ՠ`, Alice’s private key `skA`. <br> **Output:** classical digital signature `σ`. |
| 4  | Quantum encoding               | To encode the classical message and signature pair `(ՠ,σ)` into a quantum state `|ՠ|σ>`. | Map the bits of the message and signature `(ՠ,σ)` to a quantum register to create a quantum representation of the classical data. | **Input:** classical message and classical signature `(ՠ,σ)`. <br> **Output:** quantum-encoded state `|ՠ|σ>`. |
| 5  | State joining                   | To combine the quantum message `|ψ>` with the encoded classical message and signature `|ՠ|σ>`. | Map the joint state to a new circuit.                                             | **Input:** Quantum message `|ψ>`, and encoded state `|ՠ|σ>`. <br> **Output:** Joint state `|ψ> ⊕ |ՠ|σ>`. |
| 6  | Shared secret generation       | To generate a shared secret to be used for symmetric encryption.      | Use a post-quantum key encapsulation mechanism (e.g., Kyber) to generate a shared secret. | **Output:** Shared secret.                                     |
| 7  | Shared secret encapsulation    | To encapsulate the shared secret and transmit it securely.             | Encapsulate the shared secret using the same post-quantum key encapsulation mechanism. | **Input:** Shared secret, Bob’s public encryption key `ekB`. <br> **Output:** Encapsulated shared secret. |
| 8  | Symmetric encryption           | To encrypt the combined quantum state `|ψ> ⊕ |ՠ|σ>`.                        | Use the shared secret and IV to encrypt the joint state using a symmetric encryption algorithm like AES. | **Input:** Combined quantum state `|ψ> ⊕ |ՠ|σ>`, shared secret, and IV. <br> **Output:** Quantum signcrypted state. |
| 9  | Transmission                   | To send the encrypted data to Bob.                                   | Transmit the encrypted circuit, IV, and the encapsulated shared secret to Bob.   | **Output:** Bob receives the encrypted quantum circuit, the IV, and the encapsulated shared secret. |
| 10 | Shared secret decapsulation    | To decapsulate the encapsulated shared secret and recover it for symmetric decryption. | Bob uses his private decryption key to decapsulate the shared secret.              | **Input:** Encapsulated shared secret and Bob’s private key `dkB`. <br> **Output:** Shared secret. |
| 11 | Circuit decryption             | For Bob to decrypt the signcrypted message.                          | Bob decrypts the encrypted quantum circuit using the recovered shared secret and IV, retrieving the original quantum message `|ψ>` and classical pair `(ՠ,σ)`. | **Input:** Signcrypted quantum state, shared secret, and IV. <br> **Output:** Original quantum message `|ψ>` and classical pair `(ՠ,σ)`. |
| 12 | Verification                   | For Bob to verify the signature `σ` on the message `ՠ`, confirming the message came from Alice and was not modified. | Use the public verification key `pkA` to verify the signature.                    | **Input:** Classical pair `(ՠ,σ)`, public verification key `pkA`. <br> **Output:** Verification result for `(ՠ,σ)`. |

---

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
   - [CRYSTALS-Dilithium](https://github.com/GiacomoPope/dilithium-py)
   - [CRYSTALS-Kyber](https://github.com/GiacomoPope/kyber-py)
   
2. **Symmetric Encryption:**
   - AES via the `Crypto.Cipher` module from [PyCryptodome](https://pypi.org/project/pqcrypto/)

3. **Quantum Computing:**
   - [Qiskit](https://github.com/qiskit)

4. **Data Handling:**
   - Python’s built-in `secrets` module for secure random number generation.
   - `BytesIO` from the `io` module for handling data streams.

---

## Pseudocode

For a high-level algorithmic overview of the signcryption and unsigncryption processes, refer to the [Pseudocode](pseudocode.md) file.

---

## References

1. [Tommaso Gagliardoni, “Can You Sign A Quantum State?,” Kudelski Security Research, May 21, 2019.](https://research.kudelskisecurity.com/2019/05/21/can-you-sign-a-quantum-state/)
2. [G. Pope, dilithium-py. GitHub repository.](https://github.com/GiacomoPope/dilithium-py)  
3. [G. Pope, kyber-py. GitHub repository.](https://github.com/GiacomoPope/kyber-py)  
4. [pqcrypto. PyPI repository.](https://pypi.org/project/pqcrypto/)  
5. [Qiskit](https://github.com/qiskit)
