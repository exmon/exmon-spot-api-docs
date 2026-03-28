# API Key Types

EXMON Spot API supports multiple API key authentication methods for signing requests to protected endpoints such as trading, account data, and withdrawals.

API keys are used together with request signatures to verify identity and ensure integrity of API calls.

EXMON supports the following API key types:

- Ed25519 (recommended)
- HMAC-SHA256
- RSA

---

## Ed25519 (Recommended)

Ed25519 is an asymmetric cryptographic system based on modern elliptic curve signatures.

In this model:
- The user generates a private/public key pair
- The public key is registered with EXMON
- The private key remains fully local and is used to sign requests
- EXMON verifies signatures using the stored public key

### Advantages
- High performance signing and verification
- Small key and signature size
- Strong security comparable to large RSA keys
- Designed for modern high-throughput API systems

### Key format example
<pre>-----BEGIN PUBLIC KEY-----
MCowBQYDK2VwAyEAn9d3kQk8pR0mZl7x9vQmJt7c3rW8x2QwE8aV0nL2cYk=
-----END PUBLIC KEY-----</pre>

### Signature example
<pre>b2Fz9mQv7pK0cR1eT6yU8nV3mX0lQ9wE4rT7yU1iO2pA3sD5fG6hJ8kL9z==</pre>

## HMAC-SHA256

HMAC uses a shared secret key for both request signing and verification.

Model:
- EXMON generates a secret key
- Client uses it to generate request signatures
- Server verifies signatures using the same secret

### Properties
- Fast and simple
- Requires secure secret storage
- Less secure than asymmetric methods

### Secret key example
<pre>exm_hmac_sk_9f3a7c1d5b8e4f2a6c0d1e3f7a9b2c4d</pre>

### Signature example
<pre>a91c3f7b9d2e4a6c8f0b1d3e5f7a9c2d4e6f8b0a1c3d5e7f9b2c4d6e8f0a1b3</pre>

## RSA

RSA uses asymmetric cryptography based on large integer factorization.

Model:
- User generates RSA key pair (2048 or 4096 bit)
- Public key is registered in EXMON
- Private key signs requests locally
- Server verifies using public key

### Properties
- High security
- Larger signatures
- Slower than Ed25519
- Enterprise compatibility

### Public key example
<pre>-----BEGIN PUBLIC KEY-----
MIIBCgKCAQEAu1r8k9m3pQ7xvL2cR8nT5yU0iO9pA1sD3fG6hJ8kL4zXcVbN2mQ
8aP0lK7dR9yT3uI5oP6mN1bV4cX7zQ2wE8rT9yU1iO3pA5sD7fG9hJ2kL4zXcVb
-----END PUBLIC KEY-----</pre>

### Signature example
<pre>d7f3a9c2e4b6d8f0a1c3e5f7b9d2a4c6e8f0b1d3c5e7f9a2b4d6c8e0f1a3b5c7</pre>


---

## Security Requirements

- Private keys must never be exposed or logged
- API keys must be stored securely
- Keys should be rotated periodically
- Compromised keys must be revoked immediately
- All requests must be signed and validated server-side

---

## Recommendation

EXMON recommends Ed25519 for all new integrations due to performance, security, and modern cryptographic design.
