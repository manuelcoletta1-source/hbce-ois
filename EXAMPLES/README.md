# HBCE-OIS Examples

## ipr.example.json

This is a structural example of an HBCE-OIS Identity Primary Record (IPR).

Fields `anchor_hash`, `integrity`, and `previous_hash` are placeholders (64-hex) and must be recomputed for real IPR issuance.

Recommended practice:
- Use deterministic JSON canonicalization (stable key order, no whitespace variance).
- Compute `anchor_hash` as SHA-256 of the canonical payload to be anchored.
- Compute `integrity` as SHA-256 of the canonical IPR representation according to the implementation rule.
- Use `previous_hash` to chain append-only evolution.
