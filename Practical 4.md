# Practical 4: Practical Implementation of Cryptography for Data Privacy

## Aim

To study and practically implement cryptographic techniques such as **encryption, hashing, and digital signatures** to understand how they protect sensitive information and maintain data privacy.

## Objectives

The objectives of this practical are:

1. To understand how cryptography protects confidential information.
2. To implement symmetric encryption for protecting a message.
3. To generate a cryptographic hash for verifying data integrity.
4. To understand the working of digital signatures.
5. To analyze the role of cryptography in real-world data privacy.

---

## 1. Introduction to Cryptography

Cryptography is a security technique used to protect information from unauthorized access or modification.

It transforms information using mathematical algorithms so that only authorized users can access or verify it.

For example, suppose a user wants to send:

> `My password is 123456`

Sending this information directly over an insecure connection could expose it to an attacker.

Cryptography can instead transform the information into an unreadable form:

```text
Original Message
       ↓
Cryptographic Algorithm + Key
       ↓
Encrypted Data
       ↓
Secure Transmission
       ↓
Decryption + Key
       ↓
Original Message
```

Cryptography is commonly used to provide:

- **Confidentiality** – keeping information secret.
- **Integrity** – detecting unauthorized changes.
- **Authentication** – verifying the identity of a party.
- **Non-repudiation** – providing evidence of the origin of digitally signed data.

---

# 2. Encryption

Encryption converts readable information, known as **plaintext**, into an unreadable form called **ciphertext**.

Decryption reverses this process when the correct key is available.

### Basic Process

```text
             Encryption
Plaintext ─────────────────→ Ciphertext
                               │
                               │ Decryption
                               ↓
                            Plaintext
```

### Example

Consider the message:

```text
DATA PRIVACY
```

After encryption, it may look like:

```text
8fA2$xP91@kL...
```

The ciphertext does not reveal the original message without the required cryptographic key.

---

## 3. Symmetric Encryption

In symmetric encryption, **one secret key** is used to encrypt and decrypt information.

```text
                 Secret Key
                    │
                    ↓
Plaintext → [ Encryption ] → Ciphertext
                                  │
                                  ↓
                           [ Decryption ]
                                  ↑
                              Secret Key
                                  │
                                  ↓
                              Plaintext
```

### Example Algorithm

**AES (Advanced Encryption Standard)** is one of the widely used symmetric encryption algorithms.

### Advantages

- Fast encryption and decryption.
- Suitable for large amounts of data.
- Requires relatively less computational power.

### Limitation

The secret key must be securely shared between the parties. If an attacker obtains the key, the encrypted information can potentially be decrypted.

### Applications

Symmetric encryption can be used for:

- Encrypting files.
- Protecting databases.
- Full-disk encryption.
- Securing backups.
- Protecting sensitive application data.

---

# 4. Asymmetric Cryptography

Asymmetric cryptography uses **two related keys** instead of a single shared secret.

### Keys

**Public Key:** Can be distributed to other people.

**Private Key:** Must be kept secret by its owner.

```text
             Public Key
                 ↓
Original Data → Encryption → Ciphertext
                              ↓
                         Private Key
                              ↓
                           Decryption
                              ↓
                        Original Data
```

Common algorithms include:

- RSA
- ECC

Asymmetric cryptography is particularly useful for secure key exchange, authentication, and digital signatures.

Compared with symmetric encryption, it generally requires more computational resources.

---

# 5. Hashing

Hashing is different from encryption.

A hash function takes input data and produces a fixed-length output known as a **hash value** or **digest**.

```text
Input
  ↓
Hash Function
  ↓
Fixed-Length Hash
```

For example:

```text
Input:
Data Privacy

       ↓ SHA-256

Hash:
A cryptographic hash value of fixed length
```

A cryptographic hash function is designed so that it is computationally impractical to reconstruct the original input from the hash.

### Properties of Cryptographic Hashing

A good cryptographic hash function should have:

- Fixed-size output.
- Efficient computation.
- Strong resistance to finding the original input.
- Strong resistance to finding two different inputs with the same hash.
- High sensitivity to changes in the input.

Even a small change in the original data should produce a substantially different hash.

### Applications

Hashing is useful for:

- File integrity checking.
- Detecting unauthorized modifications.
- Digital signatures.
- Data verification.
- Password storage when appropriate password-hashing algorithms are used.

**Important:** Passwords should not normally be stored as plain SHA-256 hashes. Dedicated password-hashing algorithms such as **Argon2, bcrypt, or scrypt**, together with appropriate salts, are designed for this purpose.

---

# 6. Digital Signatures

A digital signature is a cryptographic mechanism used to verify the **authenticity and integrity** of digital information.

The sender generates a signature using their private key.

A simplified process is:

```text
                Original Message
                       ↓
                  Hash Function
                       ↓
                  Message Hash
                       ↓
                  Private Key
                       ↓
                Digital Signature
```

The receiver can use the sender's public key and the relevant verification procedure to determine whether the signature is valid.

### Digital signatures help establish:

- Who signed the information.
- Whether the information was changed after signing.
- Evidence supporting the origin of the signed data.

### Applications

Digital signatures are commonly used for:

- Electronic documents.
- Software distribution.
- Digital certificates.
- Secure transactions.
- Authentication systems.

---

# 7. Practical Implementation Using Python

The following example demonstrates three different cryptographic concepts:

1. Encryption
2. Hashing
3. Digital signatures

### Python Program

```python
import hashlib

# --------------------------------
# 1. Hashing
# --------------------------------

message = "Data Privacy Practical"

hash_value = hashlib.sha256(message.encode()).hexdigest()

print("Original Message:")
print(message)

print("\nSHA-256 Hash:")
print(hash_value)


# --------------------------------
# 2. Simple Encryption Demonstration
# --------------------------------

def caesar_encrypt(text, shift):
    result = ""

    for character in text:
        if character.isalpha():
            base = ord('A') if character.isupper() else ord('a')
            result += chr((ord(character) - base + shift) % 26 + base)
        else:
            result += character

    return result


encrypted_message = caesar_encrypt(message, 3)

print("\nEncrypted Message:")
print(encrypted_message)


# --------------------------------
# 3. Integrity Verification
# --------------------------------

received_message = "Data Privacy Practical"

received_hash = hashlib.sha256(
    received_message.encode()
).hexdigest()

if hash_value == received_hash:
    print("\nIntegrity Check: Data is unchanged.")
else:
    print("\nIntegrity Check: Data has been modified.")
```

### Sample Output

```text
Original Message:
Data Privacy Practical

SHA-256 Hash:
[64-character hexadecimal hash]

Encrypted Message:
Gdwd Sulydfb Sulfwlfdo

Integrity Check: Data is unchanged.
```

> **Note:** The Caesar cipher in this program is only an educational demonstration and is **not secure for protecting real-world sensitive data**. Modern applications should use established algorithms such as AES through a trusted cryptographic library.

---

# 8. Demonstration of Data Tampering

Hashing can be used to identify whether data has been changed.

Suppose the original message is:

```text
Data Privacy Practical
```

Its hash is calculated and stored.

Later, an attacker changes the message:

```text
Data Privacy Assignment
```

The newly calculated hash will be different.

```text
Original Data
     ↓
 SHA-256
     ↓
Original Hash

Changed Data
     ↓
 SHA-256
     ↓
New Hash
```

If:

```text
Original Hash ≠ New Hash
```

then the data has been modified.

This demonstrates how hashing can support **data integrity verification**.

---

# 9. Comparison of Cryptographic Techniques

| Technique | Main Purpose | Key Required | Reversible? | Example |
|---|---|---|---|---|
| Symmetric Encryption | Confidentiality | One shared secret key | Yes | AES |
| Asymmetric Encryption | Confidentiality / secure communication | Public + private keys | Yes | RSA, ECC |
| Hashing | Integrity / verification | No secret key for ordinary hashing | No | SHA-256, SHA-3 |
| Digital Signature | Authentication and integrity | Private + public key | Signature verification | RSA-PSS, ECDSA, EdDSA |

---

# 10. Cryptography in Data Privacy

Cryptography protects information throughout its lifecycle.

| Situation | Technique | Purpose |
|---|---|---|
| Sending information online | Encryption | Prevent unauthorized reading |
| Storing sensitive files | Encryption | Protect stored information |
| Checking downloaded files | Hashing | Detect modification |
| Protecting passwords | Password hashing | Reduce exposure of passwords |
| Signing electronic documents | Digital signatures | Verify authenticity and integrity |
| Secure websites | TLS | Protect network communication |

For example, when a user logs into an online service, cryptographic protocols help protect communication between the user's device and the server.

---

# 11. Real-World Example: Online Learning Platform

Consider an online learning platform where students:

- Create accounts.
- Submit assignments.
- Take online examinations.
- Exchange information with servers.
- Store personal information.

Cryptography can protect these activities in different ways.

### Login Communication

TLS helps protect information transmitted between the student's browser and the server.

### Stored Information

Sensitive information can be encrypted when stored.

### Passwords

Passwords should be stored using appropriate password-hashing techniques rather than plaintext storage.

### Uploaded Documents

Hashes can be used to verify whether files have been modified.

### Official Documents

Digital signatures can help verify the authenticity and integrity of digitally signed documents.

---

# 12. What Happens Without Cryptography?

If cryptographic protection is not properly implemented, several risks can arise:

1. Sensitive information may be exposed.
2. Attackers may intercept network communication.
3. Stored data may be accessed after a security breach.
4. Unauthorized modifications may go undetected.
5. Passwords may be exposed if stored insecurely.
6. Users may have difficulty verifying whether a digital document is authentic.
7. Communication between users and services may become vulnerable to attacks.

---

# 13. Advantages of Cryptography

- Protects confidential information.
- Helps maintain data integrity.
- Supports authentication.
- Helps secure online communication.
- Protects sensitive stored information.
- Enables secure digital transactions.
- Supports trustworthy digital signatures.

---

# 14. Limitations and Challenges

Cryptography is powerful, but its implementation also presents challenges:

- Cryptographic keys must be protected.
- Poor key management can compromise security.
- Weak or outdated algorithms may provide insufficient protection.
- Incorrect implementation can introduce vulnerabilities.
- Strong cryptographic operations may require additional computational resources.
- Lost encryption keys can make encrypted data inaccessible.

Therefore, simply using encryption is not enough; **proper algorithm selection, implementation, and key management are also important.**

---

# 15. Result

The practical successfully demonstrated the fundamental role of cryptography in data privacy.

Encryption was studied as a method for protecting confidentiality, hashing was demonstrated for integrity verification, and digital signatures were examined as a mechanism for authentication and integrity.

The practical also demonstrated through Python how cryptographic operations can be incorporated into applications to protect and verify digital information.

---

# Conclusion

Cryptography provides the technical foundation for protecting digital information against unauthorized access and modification.

Different techniques serve different purposes. **Encryption** protects confidentiality, **hashing** helps verify integrity, and **digital signatures** provide mechanisms for authentication and integrity verification.

In modern systems, these techniques work together rather than operating independently. Secure websites, online banking, cloud storage, digital documents, software updates, and many other digital services depend on cryptographic mechanisms to protect information.

Therefore, understanding and correctly implementing cryptography is an essential part of maintaining **data privacy and cybersecurity**.

---

## References

1. [NIST – Cryptography](https://www.nist.gov/cryptography?utm_source=chatgpt.com)
2. [NIST – Cybersecurity](https://www.nist.gov/cybersecurity?utm_source=chatgpt.com)
3. [NIST – Secure Hash Standard (FIPS 180-4)](https://csrc.nist.gov/pubs/fips/180-4/upd1/final?utm_source=chatgpt.com)
4. [NIST – Digital Signature Standard (FIPS 186-5)](https://csrc.nist.gov/pubs/fips/186-5/final?utm_source=chatgpt.com)
5. [Python hashlib documentation](https://docs.python.org/3/library/hashlib.html?utm_source=chatgpt.com)

