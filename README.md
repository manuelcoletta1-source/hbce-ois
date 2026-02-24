# HBCE-OIS

Deterministic Operational Identity Verification Engine (HBCE-OIS v0.1-prestandard).

HBCE-OIS (Hermeticum Blindata Computabile Evolutiva — Operational Identity Standard) is an open European technical pre-standard defining a deterministic operational identity layer for autonomous, human and hybrid systems.

HBCE-OIS defines:
- Identity Primary Record (IPR) structure
- deterministic verification logic
- fail-closed execution gating
- append-only audit continuity
- node interoperability principles
- hash-only / no-custody publication model

Status: Draft v0.1-prestandard (public release)

---

## Live (GitHub Pages)

- Landing: https://manuelcoletta1-source.github.io/hbce-ois/
- Verifier: https://manuelcoletta1-source.github.io/hbce-ois/tools/verifier.html
- Tests runner: https://manuelcoletta1-source.github.io/hbce-ois/tools/tests.html

---

## Repository Map

- Specification: `SPEC/HBCE-OIS-v0.1.md`
- IPR schema (normative): `SCHEMA/ipr.schema.json`
- Compliance requirements: `COMPLIANCE/HBCE-OIS-Compliance-Requirements.md`
- Architecture overview: `ARCHITECTURE/HBCE-OIS-Architecture.md`
- EU positioning note: `EU/HBCE-OIS-EU-Positioning.md`
- Implementation status: `STATUS.md`
- Quickstart: `QUICKSTART.md`
- Verification model: `VERIFICATION.md`
- Examples: `EXAMPLES/`

---

## Deterministic Verification (Core Rule)

Integrity verification is performed as:

1. Load IPR JSON
2. Remove the `integrity` field
3. Canonicalize JSON deterministically (stable sorted keys, no whitespace variance)
4. Compute SHA-256 over the canonical JSON string
5. Compare to stored `integrity`

If mismatch → INVALID (fail-closed)

---

## Official Test Vectors

- VALID vector: `tests/ipr-valid.json`
- INVALID vector: `tests/ipr-invalid.json`

Expected behavior:
- valid vector → `VALID (integrity match)`
- invalid vector → `INVALID (integrity mismatch)`

---

## License

Apache-2.0
