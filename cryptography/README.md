# Cryptography Fundamentals

**Focus:** Applied cryptography, encryption protocols, security analysis

## Overview
Implementation and analysis of cryptographic protocols including symmetric encryption, hash functions, and secure communication methods.

## Projects

### 1. AES & Blowfish Encryption
**Objective:** Implement medical device data protection for FDA compliance

**Implementation:**
```python
from Crypto.Cipher import AES, Blowfish
from Crypto.Random import get_random_bytes

# AES-256 encryption for patient data
def encrypt_patient_data(data, key):
    cipher = AES.new(key, AES.MODE_GCM)
    ciphertext, tag = cipher.encrypt_and_digest(data.encode())
    return cipher.nonce, ciphertext, tag

# Blowfish for legacy system compatibility
def encrypt_legacy(data, key):
    cipher = Blowfish.new(key, Blowfish.MODE_CBC)
    return cipher.encrypt(pad_data(data))
```

**Real-World Application:** Used in Medtronic internship for safeguarding patient data under new FDA regulations.

**Key Learning:** Choosing appropriate encryption algorithms based on security requirements and system constraints

---

### 2. Hash Functions & Collision Resistance
**Topics Covered:**
- SHA-256 and SHA-512 hash generation
- Collision resistance properties
- Rainbow table attacks and salting
- HMAC for message authentication

**Security Analysis:**
```python
import hashlib

# Secure password hashing with salt
def hash_password(password, salt=None):
    if salt is None:
        salt = get_random_bytes(32)
    
    # Use PBKDF2 for key derivation
    key = hashlib.pbkdf2_hmac('sha256', 
                               password.encode(), 
                               salt, 
                               100000)  # iterations
    return salt, key
```

**Key Learning:** Never store passwords in plaintext; always use salted hashes with key derivation functions

---

### 3. Digital Signatures
**Objective:** Implement authentication and non-repudiation

**Concepts:**
- RSA signature generation and verification
- Public key infrastructure (PKI)
- Certificate chains and trust
- Code signing

**Use Cases:**
- Software integrity verification
- Document authentication
- Secure communications

**Key Learning:** Digital signatures provide authenticity, integrity, and non-repudiation

---

### 4. Secure Key Exchange
**Protocols Studied:**
- Diffie-Hellman key exchange
- RSA key transport
- Perfect forward secrecy
- Key derivation functions

**Security Considerations:**
- Man-in-the-middle attack prevention
- Key strength and entropy
- Secure key storage
- Key rotation policies

**Key Learning:** Secure key exchange is fundamental to all encrypted communications

---

## Cryptographic Principles

### 1. Confidentiality
Ensuring data is accessible only to authorized parties
- **Technique:** Symmetric/asymmetric encryption
- **Algorithms:** AES, RSA

### 2. Integrity
Detecting unauthorized modifications
- **Technique:** Hash functions, MACs
- **Algorithms:** SHA-256, HMAC

### 3. Authentication
Verifying identity of parties
- **Technique:** Digital signatures, certificates
- **Algorithms:** RSA, ECDSA

### 4. Non-Repudiation
Preventing denial of actions
- **Technique:** Digital signatures with timestamps
- **Algorithms:** RSA signatures

---

## Security Best Practices

### Key Management
Use strong, random keys  
Implement key rotation  
Secure key storage (HSM, key vaults)  
Separate encryption and signing keys  

### Algorithm Selection
Use industry-standard algorithms (AES, RSA)  
Avoid deprecated algorithms (DES, MD5)  
Keep up with cryptographic research  
Follow NIST recommendations  

### Implementation
Never implement custom crypto  
Use well-tested libraries  
Handle errors securely  
Validate all inputs  

---

## Real-World Applications

### Medtronic Internship
- Implemented AES/Blowfish encryption for medical device software
- Ensured FDA compliance for patient data protection
- Designed secure update mechanisms for embedded systems

### CTF Competitions
- Applied cryptanalysis to break weak implementations
- Identified common crypto vulnerabilities
- Practiced secure coding techniques

---

## Skills Demonstrated
- Applied cryptography implementation
- Security protocol analysis
- Python programming for security
- Understanding of encryption standards
- Secure coding practices
- Risk assessment and mitigation

---

**Technologies:** Python, PyCrypto, OpenSSL, cryptographic libraries  
**Concepts:** Symmetric/asymmetric encryption, hashing, digital signatures, key exchange