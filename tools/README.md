# HBCE-OIS Tools

## verifier.html

Local deterministic IPR integrity verifier.

- No network calls
- SHA-256 (browser crypto)
- Canonical JSON via stable sorted keys
- Integrity computed over the IPR JSON *without* the `integrity` field
- Fail-closed: mismatch => invalid
