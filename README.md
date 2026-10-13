# Motohiro Suzuki | Quantum Security Verification

**From PQC Claims to Verifiable Evidence.**

I'm building QSP / QSV, an independent research effort focused on making quantum-security claims inspectable, reproducible, and open to technical scrutiny.

My central question is:

> When someone claims a system is "PQC-ready" or "quantum-safe," what can another person actually verify from the available evidence?

Supporting a post-quantum algorithm is not the same as demonstrating that a particular implementation, input, and execution produced a specific result.

My current work focuses on **ML-DSA interoperability, cryptographic test evidence, source provenance, reproducibility, and explicit verification boundaries**.

---

## Current Public Research

### QSV ML-DSA Interoperability Corpus

**[Explore the public QSV evidence repository](https://github.com/mokkunsuzuki-code/qsv-mldsa-interoperability-corpus)**

The published corpus includes:

- **6 selected NIST ACVP ML-DSA `sigVer` cases**, covering selected cases from ML-DSA-44, ML-DSA-65, and ML-DSA-87.
- **12 implementation-level records:** 6 OpenSSL invocations and 6 Cloudflare CIRCL invocations.
- Recorded runtime invocation evidence and deterministic metadata-only normalization.
- Canonical neutral-fixture examples with pinned upstream source references.
- Separate SHA-256 commitments for upstream source files, canonical source-case descriptors, and neutral fixtures.
- Public verification code and explicitly defined rejection conditions.
- First-party historical source-to-runtime build-event provenance evidence, subject to documented limitations.

In the normalized results, `observed_acceptance` is derived from pinned harness semantics, exact recorded command arguments, process exit status, and stdout SHA-256 commitments. It is not a separately captured direct observation.

Normalization performs **no new ML-DSA cryptographic execution**.

The neutral-fixture examples are metadata-only. Their `consumer: null` values do not establish complete end-to-end binding to an actual implementation.

### What This Evidence Does Not Prove

The published corpus does not establish:

- NIST validation or FIPS 204 certification.
- Complete ML-DSA conformance or exhaustive test coverage.
- Universal cryptographic correctness or absence of vulnerabilities.
- Completed third-party independent cryptographic reproduction.
- Independently reproducible builds or complete execution-environment provenance.
- System-wide quantum safety.

These boundaries are part of the research record.

---

## Start Here: Inspect the Evidence

**1. Examine the published runtime results**

[QSV F7 normalized-result evidence](https://github.com/mokkunsuzuki-code/qsv-mldsa-interoperability-corpus/blob/main/results/qsv_mldsa_f7_normalized_result_evidence_v0_1/qsv_mldsa_f7_normalized_result_evidence_v0_1.json)

Inspect the twelve records, selected cases, implementation identities, execution metadata, and derived acceptance results.

**2. Compare positive and negative test cases**

- [NIST ACVP positive neutral fixture](https://github.com/mokkunsuzuki-code/qsv-mldsa-interoperability-corpus/blob/main/examples/qsv-mldsa-acvp-positive-canonical-v0.3.json)
- [NIST ACVP negative neutral fixture](https://github.com/mokkunsuzuki-code/qsv-mldsa-interoperability-corpus/blob/main/examples/qsv-mldsa-acvp-negative-canonical-v0.3.json)

These are metadata-only examples, not new cryptographic execution results.

**3. Review source provenance and canonicalization**

[Neutral-fixture canonicalization contract](https://github.com/mokkunsuzuki-code/qsv-mldsa-interoperability-corpus/blob/main/contracts/qsv-mldsa-neutral-fixture-canonicalization-contract-v0.1.json)

The contract distinguishes upstream file hashes from domain-separated source-case and fixture commitments.

**4. Inspect the verification code**

[Neutral-fixture verification implementation](https://github.com/mokkunsuzuki-code/qsv-mldsa-interoperability-corpus/blob/main/runtime/verify_qsv_mldsa_neutral_fixture_gap_closure_v0_1.py)

The published verification code should be evaluated within its documented scope and execution assumptions. Inspecting source code is not equivalent to completing independent verification.

**5. Examine historical source-to-runtime provenance**

[Historical provenance manifest](https://github.com/mokkunsuzuki-code/qsv-mldsa-interoperability-corpus/blob/main/manifest/qsv-mldsa-f7-consumer-source-to-runtime-provenance-v0.1-manifest.json)

This records first-party historical build-event evidence for the selected F7 scope. It does not establish complete environment provenance, independently reproducible builds, or completed successor adapter wiring.

---

## QSP and QSV

**QSP** is the broader public research project exploring evidence-based verification of post-quantum and quantum-security claims.

**QSV (Quantum Security Verification)** is the evidence-oriented verification approach and reference-model work developed within that effort.

Related research areas include:

- PQC migration evidence and cryptographic agility.
- Cross-implementation interoperability.
- Cross-platform reproducibility.
- Cryptographic binding and evidence portability.
- QKD evidence classification.
- Software supply-chain integrity.
- Evidence preservation and external timestamps.
- Independent reproduction and assessment readiness.

**[QSP Public Research Portal](https://github.com/mokkunsuzuki-code/qsp)**

**[QSV Reference Model](https://github.com/mokkunsuzuki-code/qsv-reference-model)**

---

## Core Principle

> A quantum-security claim should never be stronger than the evidence supporting that exact claim.

The QSV reference model distinguishes:

**Claim → Evidence → Binding → Verification → Independent Reproduction → Adjudication**

These are different stages, not interchangeable labels.

A successful test is not proof of universal correctness.

Agreement between implementations does not automatically prove independent correctness.

A hash identifies bytes; it does not, by itself, prove how those bytes were produced.

A timestamp does not establish cryptographic conformance.

Unknown, pending, unsupported, or unexecuted results must not be silently promoted to verified.

---

## Independent Technical Review Welcome

I welcome technical criticism, reproducibility findings, interoperability questions, and challenges to evidence provenance and verification boundaries.

One question I am particularly interested in:

> What minimum evidence would you require before trusting a cryptographic test result marked "PASS"?

Both successful and unsuccessful independent reproduction attempts are valuable when their inputs, conditions, and observations are documented.

The objective is not to make QSV difficult to criticize. It is to make its claims possible to inspect, reproduce, and challenge.

---

## Technical Writing

Japanese-language articles about verifiable PQC evidence:

- [Why "PQC support" and "PQC verified" are different](https://zenn.dev/qspprotocol/articles/9303af7d40f022)
- [Why a cryptographic test "PASS" needs supporting evidence](https://zenn.dev/qspprotocol/articles/105bea46ba71ab)

## Connect

- **GitHub:** https://github.com/mokkunsuzuki-code
- **X:** https://x.com/QSPprotocol
- **Zenn:** https://zenn.dev/qspprotocol

---

*QSP / QSV is ongoing independent research. References to NIST, OpenSSL, Cloudflare CIRCL, and other projects identify standards, evidence sources, or implementation targets. They do not imply endorsement, formal affiliation, certification, or completed third-party assessment.*
