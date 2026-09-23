# 1seal/verifier

draft documentation for an offline DSSE/JCS evidence verifier.

## current public status

as of 2026-09-23, this repository's public `main` contains documentation,
security guidance and a license. it does not contain an executable verifier,
an installable package, or a Node/browser implementation.

the semantic LMV implementation remains private/pre-release. this repository
is not a published reference implementation of the full semantic LMV model.
see the [current project status](https://1seal.org/status/).

## browser field-check demo

the [playground](https://1seal.org/playground/) checks required fields only.
it does not verify signatures, perform JCS canonicalization, establish signer
trust, or evaluate semantic LMV invariants. a successful field check is not
cryptographic verification.

## proposed design, not shipped behavior

the proposed evidence verifier would check DSSE envelopes with JCS
(RFC 8785) payloads against explicitly configured trusted public keys.
intended constraints are offline operation, deterministic results and explicit
failure on unsupported input or invalid signatures, without network fallbacks.

these are design goals, not capabilities demonstrated by the current public
repository. no implementation release date or completed validation is claimed.

## scope boundary

cryptographic evidence verification and semantic intent/payload checks are
different tasks. a valid signature alone does not establish that a payload
matches declared intent, is safe, lawful, approved or generally trustworthy.
it also does not rule out a compromised signing key or signer.

the proposed evidence verifier is not a full Sigstore client: Rekor/Fulcio
lookups, OIDC keyless flows and remote consistency checks are outside its
described scope.

## reporting security issues

please do not open public issues for security reports. see [SECURITY.md](SECURITY.md).

## license

Apache-2.0; see [LICENSE](LICENSE).
