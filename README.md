# Motohiro Suzuki | Quantum Security Verification

**From PQC Claims to Verifiable Evidence.**

I'm building QSP / QSV, an independent research effort focused on making quantum-security claims inspectable, reproducible, and open to technical scrutiny.

My central question is:

> When someone claims a system is "PQC-ready" or "quantum-safe," what can another person actually verify from the available evidence?

Supporting a post-quantum algorithm is not the same as demonstrating that a particular implementation, input, and execution produced a specific verified result.

My current work focuses on **ML-DSA interoperability, test evidence, source provenance, reproducibility, and explicit verification boundaries**.

## Current Public Research

### QSV ML-DSA Interoperability Corpus

**[Explore the public QSV evidence repository](https://github.com/mokkunsuzuki-code/qsv-mldsa-interoperability-corpus)**

The published research includes:

- **6 selected NIST ACVP ML-DSA signature-verification (`sigVer`) cases**, covering selected examples from ML-DSA-44, ML-DSA-65, and ML-DSA-87.
- **12 implementation-level records**: 6 OpenSSL invocations and 6 Cloudflare CIRCL invocations over the same selected cases.
- Recorded runtime invocation evidence, including execution metadata and artifact commitments.
- Deterministic, metadata-only normalization of the published F7 evidence.
- Canonical neutral-fixture examples with pinned upstream source references.
- Distinct SHA-256 commitments for source files, canonical source-case descriptors, and neutral fixtures.
- Public verification code and explicitly defined rejection conditions.
- Historical first-party source-to-runtime build-event provenance evidence, subject to documented limitations.

The published normalized result derives `observed_acceptance` from pinned harness semantics, recorded command arguments, actual process exit status, and a stdout SHA-256 commitment. This value was not directly captured as a separate observation.

Normalization does **not** perform new ML-DSA cryptographic execution.

The neutral-fixture examples are metadata-only. They do not, by themselves, prove complete end-to-end binding to an actual implementation.

### What This Evidence Does Not Prove

The current published corpus does **not** establish:

- NIST validation or FIPS 204 certification.
- Complete ML-DSA conformance or exhaustive test coverage.
- Universal cryptographic correctness or absence of vulnerabilities.
- Completed third-party independent cryptographic reproduction.
- Independently reproducible builds or complete execution-environment provenance.
- System-wide quantum safety.

A published hash, test result, or provenance record must not be interpreted as proof of a stronger claim than its documented evidence supports.

## Start Here: Inspect the Evidence

If you are reviewing QSV for the first time, these are useful starting points.

**1. Examine the published runtime-result metadata**

[QSV F7 normalized-result evidence](https://github.com/mokkunsuzuki-code/qsv-mldsa-interoperability-corpus/blob/main/results/qsv_mldsa_f7_normalized_result_evidence_v0_1/qsv_mldsa_f7_normalized_result_evidence_v0_1.json)

Inspect the selected cases, implementation identities, execution metadata, and derived result fields.

**2. Compare positive and negative source cases**

- [NIST ACVP positive neutral-fixture example](https://github.com/mokkunsuzuki-code/qsv-mldsa-interoperability-corpus/blob/main/examples/qsv-mldsa-acvp-positive-canonical-v0.3.json)
- [NIST ACVP negative neutral-fixture example](https://github.com/mokkunsuzuki-code/qsv-mldsa-interoperability-corpus/blob/main/examples/qsv-mldsa-acvp-negative-canonical-v0.3.json)

These files describe source-defined expected outcomes. They are not evidence of newly executed cryptographic tests.

**3. Examine source identity and canonicalization**

[Neutral-fixture canonicalization contract](https://github.com/mokkunsuzuki-code/qsv-mldsa-interoperability-corpus/blob/main/contracts/qsv-mldsa-neutral-fixture-canonicalization-contract-v0.1.json)

The contract distinguishes source-file byte hashes from domain-separated source-case and neutral-fixture commitments.

**4. Inspect the published verification implementation**

[Neutral-fixture verification code](https://github.com/mokkunsuzuki-code/qsv-mldsa-interoperability-corpus/blob/main/runtime/verify_qsv_mldsa_neutral_fixture_gap_closure_v0_1.py)

The verifier and its documented checks should be assessed within their stated scope and Python execution assumptions. Source inspection is not equivalent to an independently completed verification run.

**5. Examine historical source-to-runtime provenance**

[Historical provenance manifest](https://github.com/mokkunsuzuki-code/qsv-mldsa-interoperability-corpus/blob/main/manifest/qsv-mldsa-f7-consumer-source-to-runtime-provenance-v0.1-manifest.json)

This records first-party historical build-event provenance for the selected F7 scope. It does not establish independently reproducible builds, complete environment provenance, or completed successor adapter wiring.

**The invitation is to inspect the evidence, challenge the assumptions, and report what can or cannot be reproduced.**

## QSP and QSV

**QSP** is the broader public research project exploring evidence-based verification of post-quantum and quantum-security claims.

**QSV (Quantum Security Verification)** is the verification approach and reference-model work developed within that broader effort.

The research also explores:

- PQC migration evidence and cryptographic agility.
- Cross-implementation verification.
- Cross-platform reproducibility.
- Cryptographic binding and evidence portability.
- QKD evidence classification.
- Evidence preservation and external timestamps.
- Independent reproduction and assessment readiness.

**[QSP Public Research Portal](https://github.com/mokkunsuzuki-code/qsp)**

**[QSV Reference Model](https://github.com/mokkunsuzuki-code/qsv-reference-model)**

## Core Principle

> A quantum-security claim should never be stronger than the evidence supporting that exact claim.

QSV distinguishes between different stages of assurance:

**Claim → Evidence → Binding → Verification → Independent Reproduction → Adjudication**

These are distinct stages, not interchangeable labels.

A successful test is not proof of universal correctness.

Agreement between implementations is not automatically proof of independent correctness.

A hash identifies bytes; it does not, by itself, prove how those bytes were produced.

A timestamp can provide evidence about existence or ordering, but it does not establish cryptographic conformance.

Unknown, pending, unsupported, or unexecuted states must not be silently promoted to verified.

## Independent Technical Review Welcome

I welcome technical criticism, reproducibility findings, interoperability questions, and challenges to evidence provenance and verification boundaries.

In particular, I am interested in this question:

> What minimum evidence would you require before trusting a cryptographic test result marked "PASS"?

Both successful and unsuccessful independent reproduction attempts can produce useful findings when their inputs, conditions, and observations are documented.

The objective is not to make QSV difficult to criticize. It is to make its claims possible to examine and challenge.

## Technical Writing

I also publish Japanese-language articles explaining the engineering problems behind verifiable PQC evidence:

- [Why "PQC support" is different from "PQC verified"](https://zenn.dev/qspprotocol/articles/9303af7d40f022)
- [Why a cryptographic test "PASS" needs supporting evidence](https://zenn.dev/qspprotocol/articles/105bea46ba71ab)

## Connect

- **GitHub:** https://github.com/mokkunsuzuki-code
- **X:** https://x.com/QSPprotocol
- **Zenn:** https://zenn.dev/qspprotocol

---

*QSP / QSV is ongoing independent research. References to NIST, OpenSSL, Cloudflare CIRCL, and other projects identify technical standards, evidence sources, or implementation targets. They do not imply endorsement, affiliation, formal certification, or completed third-party assessment.*
