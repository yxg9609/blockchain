# PSI password checkup
## 1.Google
Protecting accounts from credential stuffing with password breach alerting （USENIX Security 2019）[https://www.usenix.org/conference/usenixsecurity19/presentation/thomas](https://)

## 2.Apple
white book (Password Monitoring -> Services security -> Password security overview) https://help.apple.com/pdf/security/en_US/apple-platform-security-guide.pdf

1. Two-part matching process

**Local List.** Apple stores a global list of the most frequently leaked passwords directly on users' iPhones and Macs. If a user's password matches an entry in this local list, the device immediately issues a warning without any network communication, ensuring zero privacy leakage.

**Cloud-Based Low-Frequency Database Query.** Only when a password is absent from the local high-frequency list does the system invoke a cryptographic protocol to compare it against a cloud database of less common leaked passwords.



2. Batching and Padding：

Querying passwords one by one would allow Apple to infer how many passwords a user has stored based on the number of requests. To prevent this side-channel leakage, iOS performs periodic round-robin queries independent of user activity. Moreover, each query always contains a fixed number of password candidates. If the user has fewer real passwords, the system automatically inserts randomly generated dummy passwords to pad the batch, making it impossible for the server to distinguish genuine queries from fake ones.

3. Cryptographic Process / OPRF

Passwords sent for cloud verification are processed using a privacy-preserving cryptographic protocol based on an OPRF-enabled PSI scheme. This allows leaked-password detection without revealing the user's actual passwords to Apple. 

However, while OPRF protects query privacy, it cannot generate publicly verifiable, unforgeable compliance proofs for third-party identity providers; the protocol is designed solely for private verification.

## 3. Efficient Unbalanced Quorum PSI from Homomorphic Encryption   CCS 24

https://dl.acm.org/doi/pdf/10.1145/3634737.3657001

## 4. Is PSI Really Faster Than PSU? Achieving Efficient PSU with Invertible Bloom Filters   EUROCRYPT 2026 

https://link.springer.com/chapter/10.1007/978-3-032-25317-0_15

## 5. Protecting accounts from credential stuffing with password breach alerting    USENIX 21

https://www.usenix.org/system/files/sec21-kogan.pdf

## 6. Scaling Private Set Intersection to Billion-Element Sets    FC 2014

https://link.springer.com/chapter/10.1007/978-3-662-45472-5_13

## 7. Faster Private Set Intersection based on OT extension, USENIX Security 2014

https://eprint.iacr.org/2014/447

## 8. Protocols for Checking Compromised Credentials, ACM CCS 2019

https://dl.acm.org/doi/10.1145/3319535.3354229

## 9. Detecting Stuffing of a User's Credentials at Her Own Accounts, USENIX Security 2020

https://www.usenix.org/conference/usenixsecurity20/presentation/wang

## 10. Private Blocklist Lookups with Checklist, USENIX Security 2021

https://www.usenix.org/conference/usenixsecurity21/presentation/kogan

## 11. Actively Secure Private Set Intersection in the Client-Server Setting, ACM CCS 2024

https://par.nsf.gov/servlets/purl/10567168

https://csrc.nist.gov/csrc/media/presentations/2024/wpec2024-1a3/images-media/wpec2024-1a3-slides-yunqing--PSI-active.pdf  slides