# HBCE-OIS Verification Model
## Deterministic Integrity Verification (v0.1)

This document defines a minimal deterministic verification model for HBCE-OIS IPR objects.

---

# 1. Objective

Ensure that any HBCE-OIS Identity Primary Record (IPR) can be independently verified using deterministic hashing.

Verification must produce identical results across independent nodes.

---

# 2. Canonicalization Rule (Minimal)

Before hashing:

1. Use UTF-8 encoding
2. Preserve key order as written
3. Remove whitespace outside JSON structure
4. Do not include external metadata

---

# 3. Integrity Hash Calculation

Integrity is calculated as:

SHA-256(canonical IPR JSON string)

The resulting 64-hex string becomes the `integrity` field.

---

# 4. Verification Procedure

To verify an IPR:

1. Load IPR JSON
2. Remove integrity field temporarily
3. Canonicalize JSON
4. Compute SHA-256
5. Compare with stored integrity value

If mismatch → invalid IPR.

---

# 5. Fail-Closed Requirement

If integrity verification fails:

Execution MUST NOT proceed.

---

# Status

HBCE-OIS deterministic verification model  
Draft v0.1
