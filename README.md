<!-- path: README.md -->

# 1seal/verifier

Offline **DSSE + JCS** verifier — **zero deps**, **deterministic**, works in **Node + Browser**.

This repo is the minimal, auditable verification layer for DSSE envelopes whose payloads are canonicalized with JCS (RFC 8785). It’s designed for constrained environments: no network egress, minimal containers, airgapped CI, and “bring-your-own-trust-root” deployments.

## What it verifies

You hand the verifier two things:

- a DSSE envelope (JSON)
- a public key you trust (typically **SPKI PEM**)

It returns a deterministic verification report with **RC.* reason codes** (no “best effort”, no network fallbacks).

## Design constraints (intentional)

- **Offline by default**: verification must not depend on external services.
- **Deterministic**: same inputs → same result.
- **Fail-closed**: parse error / unknown format / invalid signature → fail.
- **Bring-your-own-keys**: explicit key ring, no certificate chains, no external lookups.

## Quick try (no install)

Paste an envelope + public key and verify locally in the browser playground:

https://1seal.org/playground

## Non-goals

This verifier is not trying to be a full Sigstore client:

- no Rekor/Fulcio lookups
- no OIDC “keyless” flows
- no remote time/consistency assumptions

If you need those, use Sigstore tooling. If you need offline, deterministic verification with explicit trust roots — this is the point.

## Security model (honest)

This helps when **bytes drift** or when evidence needs to be verified in locked-down environments. It does **not** protect against compromised private keys or a fully compromised signer.

## Reporting security issues

Please do **not** open public issues for security bugs. See `SECURITY.md`.

## License

Apache-2.0.
