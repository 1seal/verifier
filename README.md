# verifier
Offline DSSE+JCS verifier (zero deps, deterministic, Node + Browser)

# 1seal / SealGuard (alpha)

  Offline **pre-transaction security for AI agents and server-side wallet APIs**, plus DSSE+JCS verification.
  SealGuard sits **between policy/simulation and MPC/HSM**, providing deterministic address guardrails.
  TxSeal emits DSSE receipts that can be verified offline with zero runtime dependencies.

  > **Status: private alpha – not a generally available, production-supported product.**
  > Core engine and full rule sets are currently iterated with a small set of design partners.

  ---

  ## What this repository contains

  - **Architecture and design notes** for a stateless pre-sign validator:
    - runs after policy/simulation and before MPC/HSM,
    - designed to protect AI agents and server-side wallet flows from address poisoning–style attacks.
  - **Specs and schemas** for:
    - DSSE receipts and offline verification flows (TxSeal),
    - SealGuard verdicts and evidence (similarity_s thresholds, RC.* reason codes),
    - PoisonAtlas dataset format for address poisoning research.
  - **Example configs / integration sketches** for:
    - AI agent frameworks (ElizaOS, AutoGPT, LangChain, CrewAI),
    - server wallet APIs (pre-sign hook between policy and MPC/HSM).

  This is enough to inspect the **design, data formats and invariants** without exposing all production rule sets.

  ---

  ## What this repository does *not* contain (yet)

  - A **complete, production-hardened** implementation of all planned guards.
  - Full rule sets for:
    - token impersonation / decimals confusion,
    - approvals/permits patterns,
    - chain/network mismatch across L1/L2.
  - Exchange- or custodian-specific integrations.

  Those pieces are being developed and reviewed privately while we:

  - grow the labelled corpus (PoisonAtlas),
  - validate false positive / false negative rates,
  - and formalize drift budgets and rule-diff reporting.

  ---

  ## Intended use (alpha / design partners)

  If you are evaluating 1seal / SealGuard / TxSeal as a potential design partner:

  - Use this repository to understand the **intended architecture**, invariants, and data formats.
  - For latency, recall/FPR, and supply-chain evidence, refer to the separate **Evidence Kit**
    and status artifacts mentioned in the docs.
  - Treat all APIs and flows here as **subject to change** until a 1.x GA release is announced.

  This is **not**:

  - a complete control framework,
  - legal/compliance advice,
  - or a promise of production support.

  ---

  ## High-level components

  - **1seal core** – Offline DSSE+JCS verifier (zero runtime deps, deterministic).
  - **SealGuard (inside txseal)** – Address poisoning / alias confusable guard for AI agents and server wallets.
  - **PoisonAtlas** – MIT-licensed dataset format for address poisoning research and evaluation.
  - **CLI & tools** – Offline verification, status artifacts, and CI/coverage gates.

  See the `/docs` directory for more detailed specifications and status artifacts.

  ---

  ## Security and alpha disclaimer

  This is **research / alpha-stage security infrastructure**.

  - Do not treat it as a drop-in replacement for a full production security program.
  - Do not rely on it as the **only** control for high-value funds without independent review.
  - Expect **breaking changes** in APIs, rule sets, and configuration until 1.0 is tagged.

  Security reports: see `SECURITY.md` for current contact and disclosure policy.
