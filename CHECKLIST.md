# PQC Migration Checklist: tick-box version

Copy this into a pull request or review ticket. Tick an item only after you ran its test. The full text, tests, sources and the list of what was not verified are in the [README](README.md). Sections 1 to 3 are the foundation. Sections 4 to 6 build on them.


## 1. Inventory

- [ ] **1.1** A cryptographic inventory exists as a CycloneDX CBOM (version 1.6 or later) with `cryptographic-asset` components.
- [ ] **1.2** Each inventory record carries the M-23-02 fields: algorithm, service provided, key length, vendor, operating system, hosting, and data time to live.
- [ ] **1.3** The inventory is refreshed on a schedule and covers embedded and third-party cryptography.

## 2. Prioritisation and timelines

- [ ] **2.1** Every use of RSA, ECDSA, EdDSA, finite-field DH and elliptic-curve DH is listed with a planned replacement.
- [ ] **2.2** Each data class has a recorded secrecy lifetime and an estimated migration time.
- [ ] **2.3** (US federal) For high value assets and high-impact systems, the plan has dated milestones for PQC key establishment by 31 December 2030 and PQC digital signatures by 31 December 2031.
- [ ] **2.4** All endpoints support TLS 1.3 by 2 January 2030.
- [ ] **2.5** (UK) The plan has dated checkpoints for 2028 (discovery and initial plan), 2031 (highest-priority migration) and 2035 (complete).
- [ ] **2.6** (EU) The plan starts by the end of 2026 and covers critical infrastructure by the end of 2030.

## 3. Algorithm choices

- [ ] **3.1** New PQC deployments specify only FIPS 203, 204 or 205 algorithms.
- [ ] **3.2** FN-DSA (FALCON-derived) and HQC are marked "not yet approved" and absent from production.
- [ ] **3.3** ML-KEM-768 is the default parameter set unless an exception is recorded.
- [ ] **3.4** KEM use follows NIST SP 800-227 (final, 18 September 2025).
- [ ] **3.5** The hybrid-versus-pure decision is recorded per jurisdiction, not as one global yes or no.

## 4. Protocol deployment

- [ ] **4.1** External TLS endpoints negotiate `X25519MLKEM768` where the stack supports it.
- [ ] **4.2** SSH servers on OpenSSH 10.0 or later keep `mlkem768x25519-sha256` enabled.
- [ ] **4.3** Certificate and CMS profiles use the published RFCs: RFC 9881 (ML-DSA in X.509), RFC 9935 (ML-KEM in X.509) and RFC 9936 (ML-KEM in CMS).
- [ ] **4.4** Certificate chain size is measured before any ML-DSA rollout.

## 5. Crypto agility

- [ ] **5.1** Algorithm names and parameter sets are configuration values, not hardcoded.
- [ ] **5.2** A swap of one algorithm in one service has been rehearsed in a test environment.

## 6. Governance and evidence

- [ ] **6.1** A named owner and a dated migration plan exist.
- [ ] **6.2** The inventory and the plan are reviewed at least once a year, and when a standard changes.

Result: ____ of 22 items ticked. Reviewer: ________  Date: ________
