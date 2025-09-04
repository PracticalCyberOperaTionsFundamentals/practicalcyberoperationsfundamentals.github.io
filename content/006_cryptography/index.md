---
title: "Cryptography"
nav_order: 6
has_chidren: true
permalink: /cryptography/
---
# What is Cryptography

# Fundamental Principles
**Oracles**  
When systems reveal different error messages or behaviors during decryption, signing, or verification, attackers can use these responses to recover plaintext or forge data. Examples include padding oracles and signature validation differences.

**Mode misuse**  
Misusing block cipher modes compromises confidentiality. ECB reveals patterns in plaintext, CBC with IV reuse allows block manipulation, and CTR/GCM with nonce reuse exposes keystreams that can decrypt or forge messages.

**Hash misuse**  
Hash functions used incorrectly — especially when secrets are prepended to messages (`hash = SHA256(secret || message)`) — can allow attackers to extend messages or forge valid hashes without knowing the secret.

**Key/IV reuse or weak randomness**  
When cryptographic systems reuse keys or nonces (especially in symmetric ciphers or signature schemes), attackers can recover relationships between ciphertexts or even derive the plaintext or private key. Predictable random values break security guarantees.

**JWT algorithm confusion**  
Improper handling of JWT `alg` fields can allow attackers to switch from asymmetric (`RS256`) to symmetric (`HS256`) algorithms, tricking the server into verifying forged tokens using a public key as a shared secret.

**Cryptographic math flaws**  
Weak implementation of cryptographic math — like small RSA exponents without padding, reused nonces in DSA/ECDSA, or using poor random number generators — can lead to key recovery or full message decryption.

**Timing attacks**  
When systems take varying amounts of time to process correct vs incorrect input (e.g., password or MAC comparison), attackers can measure those differences to leak secrets one bit or byte at a time.
