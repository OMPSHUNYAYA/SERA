# SERA Verification Guide

## Structural Edit Resolution and Admission

**Reference Demo:** `SERA v0.9.2`  
**Reference Surface:** Structural Keyboard  
**Audit Profile:** `SERA-AUDIT-1-D04`  
**Rules Profile:** `SK-RULES-1.1.0`

---

## 1. Purpose

This guide defines the recommended verification procedure for the current SERA browser reference implementation.

SERA governs the boundary between an edit proposal and actual mutation authority.

Its central authority relation is:

`proposal authority != target authority != mutation authority`

Its core processing relation is:

`proposal -> resolve -> plan -> preview -> revalidate -> admit -> execute OR refuse -> receipt`

The current reference demonstrates, within its declared implementation and audit boundary:

`generated edit != admitted edit`

`document changed != proposal automatically stale`

`preview_target_fingerprint != commit_target_fingerprint -> no execution under old commitment`

`write_set(E_c) subseteq admitted_mutation_envelope`

`valid refusal -> zero mutation + explicit state + stable reason + evidence`

The current verification procedure is primarily producer-side.

Independent verification is not yet claimed.

---

## 2. Reference Files

All repository paths in this guide are written relative to the repository root.

Primary browser reference:

`demo/SERA_Structural_Keyboard_Reference_Demo_v0_9_2.html`

Primary project overview:

`README.md`

Current quickstart:

`docs/Quickstart.md`

Current FAQ:

`docs/FAQ.md`

Architecture overview:

`docs/SERA_Architecture_At_A_Glance_v1_0.md`

Core architecture:

`docs/specs/SERA_Core_Architecture_v0_9_2.txt`

Conformance specification:

`docs/specs/SERA_Conformance_v0_2_0.txt`

Audit and assurance specification:

`docs/specs/SERA_Audit_and_Assurance_v0_9_2.txt`

Console audit commands:

`docs/SERA_v0_9_2_Console_Audit_Commands.txt`

Frozen browser-reference identity:

`verify/FREEZE_DEMO_SHA256.txt`

Current local machine-readable schema package:

`schema/SERA_Proposal_Schema_v1_0.json`

`schema/SERA_Refusal_Witness_Schema_v1_0.json`

`schema/SERA_Receipt_Schema_v2_0.json`

`schema/SERA_Session_Bundle_Schema_v2_0.json`

The JSON schemas support structural validation.

They do not replace the normative SERA conformance rules.

---

## 3. Open the Reference Demo

Open:

`demo/SERA_Structural_Keyboard_Reference_Demo_v0_9_2.html`

in a current desktop browser.

Ordinary local reference operation requires:

- JavaScript enabled
- no server
- no database
- no external AI model
- no external runtime library
- no network connection

A browser may display a local `file:` origin warning in the developer console.

That warning does not by itself indicate a SERA audit failure.

The SERA verification result is determined by the declared audit and evidence checks.

---

## 4. Primary Release Gate

Open the browser developer console and run:

```javascript
await SERA_AUDIT.runAll()
```

Current expected result:

```text
CORE                      26/26  PASS
RESOLUTION                 7/7   PASS
EDITING                    5/5   PASS
ADMISSION                  5/5   PASS
PREVIEW                    5/5   PASS
NO SILENT RETARGET         6/6   PASS
PROPOSALS                 16/16  PASS
REFUSAL WITNESSES         11/11  PASS
COMPARISON                 9/9   PASS
DEMO FLOWS                11/11  PASS
INTERACTION                3/3   PASS
VIEWPORT                   4/4   PASS
STATUS CONTROLS            4/4   PASS
STRUCTURAL POSITION        4/4   PASS
BUTTON AFFORDANCE         21/21  PASS
CONCURRENCY                9/9   PASS
ADMISSION BOUNDARY         9/9   PASS
EVIDENCE                  10/10  PASS
UI                        21/21  PASS
KEYBOARD                  10/10  PASS
UNICODE                   13/13  PASS
BUILT-IN SELF-TEST        54/54  PASS
STATE RESTORATION          1/1   PASS
AUDIT HARNESS              4/4   PASS
KNOWN REGRESSIONS         27/27  PASS
FEATURE COVERAGE          34/34  PASS

TOTAL                    329/329 PASS
INTEGRITY REGRESSION     0
UNEXPECTED MUTATION      0
FEATURE COVERAGE         PASS
FINAL STATUS: PASS
```

A successful current reference release verification requires:

`329/329 PASS`

with:

`INTEGRITY REGRESSION = 0`

`UNEXPECTED MUTATION = 0`

`FEATURE COVERAGE = PASS`

---

## 5. Verify the Archived Full Audit

Run:

```javascript
SERA_AUDIT.lastFull()
```

Expected current full-audit archive:

`PASS`

with:

`329/329`

The full-audit archive must remain available after later quick or focused checks.

A quick or focused audit must not silently replace the latest complete full-audit record.

---

## 6. Verify Known Regressions

Run:

```javascript
SERA_AUDIT.regressions()
```

Current expected result:

`27/27 PASS`

The governing development law is:

`bug found -> fix implemented -> permanent regression test added -> full audit must pass`

A release candidate should not be accepted if any registered permanent regression fails.

---

## 7. Verify Feature Coverage

Run:

```javascript
SERA_AUDIT.coverage()
```

Current expected result:

`34/34 PASS`

with:

`UNCOVERED FEATURES = 0`

Current coverage includes:

- Agent Proposal
- Canonical Proposal Identity
- Strict Agent Proposal Authority
- No Silent Retarget
- Refusal Witnesses
- Human-Readable Refusal Explanations
- Preview Commitment v2
- Compare Current Target
- Refusal Challenge
- Boundary Challenge
- Multilingual Demo
- Reset Demo
- Structural Navigation
- Viewport Following
- Interactive TARGET Status
- Interactive ADMISSION Status
- Structural Position
- Button Affordance
- Concurrency
- Structural Relevance Classification
- Structural Admission Survival
- Admission Boundary Matrix
- Evidence
- Receipt and Bundle v2
- Independent Verifier Fixtures
- Legacy Evidence Read Compatibility
- Unicode
- Grapheme Scope
- Frozen Unicode Grapheme Conformance
- Multilingual and Complex-Script Vectors
- Keyboard-Only Complete Workflow
- Audit State Restoration
- Audit Result Persistence
- Focused Audit Reporting

The current release gate requires:

`UNCOVERED FEATURES = 0`

---

## 8. Verify the Quick Audit

Run:

```javascript
await SERA_AUDIT.quick()
```

Current expected result:

`102/102 PASS`

The quick audit is intended for development iteration and fast deterministic verification.

Its current composition contains no layout-dependent checks, so it can also run in headless DOM environments without a rendering engine.

The complete full release gate includes viewport and focus-behavior checks that require a real rendering browser.

The quick audit does not replace:

```javascript
await SERA_AUDIT.runAll()
```

as the principal release gate.

The current verification roles are:

`quick audit -> fast deterministic and headless-compatible reference checks`

`full release audit -> complete producer-side verification in a rendering browser`

`independent verifier -> future reconstruction of declared evidence outside the producer implementation`

---

## 9. Verify the Current Reference State

Run:

```javascript
SERA_AUDIT.inspect()
```

Expected identity declarations include:

`version = 0.9.2`

`conformance_version = 0.2.0`

`rules_profile = SK-RULES-1.1.0`

`proposal_profile = SERA-PROPOSAL-1-D01`

`strict_agent_profile = SERA-AGENT-STRICT-1-D01`

`receipt_profile = SERA-RECEIPT-2`

`preview_profile = SERA-PREVIEW-COMMIT-2-D01`

`refusal_witness_profile = SERA-REFUSAL-WITNESS-1-D01`

`grapheme_profile = SERA-UNICODE-GRAPHEME-1-D01`

`audit_profile = SERA-AUDIT-1-D04`

`offset_unit = UTF16_CODE_UNIT`

`character_unit = EXTENDED_GRAPHEME_CLUSTER`

The current live target, admission state, viewport state, and receipt count may vary according to the user's current interaction.

Live interface state is not itself a release failure when the complete audit suite passes.

---

## 10. Verify Multilingual Demonstration Behavior

Run:

```javascript
SERADemo.runMultilingualDemoCheck()
```

Current expected result:

`PASS`

Expected checks include:

`multilingual_content_is_separate: true`

`tamil_text_present: true`

`french_text_present: true`

`tamil_sentence_count_is_3: true`

`french_sentence_count_is_3: true`

`tamil_sentences_match: true`

`french_sentences_match: true`

`no_tamil_sentence_ambiguity: true`

`no_french_sentence_ambiguity: true`

`tamil_ki_is_one_grapheme: true`

`tamil_word_spans_match: true`

`french_accent_is_one_grapheme: true`

The Multilingual Demo must remain separate from the Boundary Challenge.

---

## 11. Verify Frozen Grapheme Conformance

Run:

```javascript
SERADemo.runFrozenGraphemeConformance()
```

Current expected result:

`766/766 PASS`

Current declared grapheme profile:

`SERA-UNICODE-GRAPHEME-1-D01`

Current declared segmentation basis:

`EXTENDED_GRAPHEME_CLUSTER`

Current evidence offset unit:

`UTF16_CODE_UNIT`

The current frozen corpus result is producer-side conformance evidence for the declared reference profile.

It is not a claim of universal linguistic correctness.

---

## 12. Verify Proposal Authority Separation

Run:

```javascript
await SERA_AUDIT.runProposals()
```

Current expected result:

`16/16 PASS`

The strict machine proposal relation is:

`machine-supplied range = locator hint`

not:

`machine-supplied range = mutation authority`

The focused proposal audit should verify that a mismatching machine range does not silently replace the independently resolved structural target.

The governing authority law is:

`proposal authority != target authority != mutation authority`

---

## 13. Verify No Silent Retarget

Run:

```javascript
await SERA_AUDIT.runNoSilentRetarget()
```

Current expected result:

`6/6 PASS`

The governing law is:

`preview_target_fingerprint != commit_target_fingerprint -> no execution under old commitment`

A valid continuation requires:

`re-resolve -> new preview -> new commitment -> new admission`

The old commitment may remain as evidence.

It must not silently transfer authority to a newly resolved target.

---

## 14. Verify Refusal Witnesses

Run:

```javascript
await SERA_AUDIT.runRefusalWitnesses()
```

Current expected result:

`11/11 PASS`

A correct refusal must preserve:

`zero mutation + explicit state + stable reason + evidence`

Current refusal families include:

`AMBIGUOUS`

`UNSUPPORTED`

`STALE`

`CONFLICT`

The audit should also preserve the distinction:

`refusal witness = deterministic evidence`

`refusal explanation = human-readable presentation`

`explanation != evidence authority`

---

## 15. Manually Verify the Refusal Challenge

Open:

**Refusal Challenge**

The result should appear automatically.

The demonstration should show a prepared structural edit whose required target meaning changes before commit.

Expected visible outcome:

`STALE`

and:

`NO MUTATION`

The old commitment must not execute against the changed target.

Use:

**Run Again**

to recompute the demonstration.

---

## 16. Verify Dependency-Aware Concurrency

Run:

```javascript
await SERA_AUDIT.runConcurrency()
```

Current expected result:

`9/9 PASS`

The key relation is:

`document changed != proposal automatically stale`

The concurrency demonstrations should preserve both sides of the admission boundary.

### Unrelated change

`required dependencies unchanged -> prepared authority may survive`

### Relevant change

`required dependencies changed -> proposal becomes STALE or CONFLICT`

This verifies the current Structural Admission Survival direction.

---

## 17. Verify the Admission Boundary Matrix

Run:

```javascript
await SERA_AUDIT.runAdmissionBoundary()
```

Current expected result:

`9/9 PASS`

Open:

**Admission Boundary Matrix**

from the information panel.

Results should appear automatically.

Use:

**Run Again**

to recompute the current matrix.

The matrix demonstrates the distinction between:

`whole-document change`

and:

`proposal-relevant structural change`

---

## 18. Verify Structural Relevance

The current reference classifies proposal-relative change using structural relevance concepts such as:

`IRRELEVANT`

`DEPENDENCY_RELEVANT`

`TARGET_MUTATING`

`RULES_RELEVANT`

`SCHEMA_RELEVANT`

The current demonstrated admission principle is:

`irrelevant change -> authority may survive`

`relevant change -> authority must be re-established`

These classes help explain why authority survives or is lost.

They do not by themselves replace the actual admission decision.

---

## 19. Verify Compare Current Target

Run:

```javascript
await SERA_AUDIT.runComparison()
```

Current expected result:

`9/9 PASS`

Open:

**Compare Current Target**

The result should appear automatically.

Use:

**Run Again**

to recompute against the current document state.

The comparison demonstrates the distinction between:

`forced target choice`

and:

`SERA structural resolution`

---

## 20. Verify Demo Flow Separation

Run:

```javascript
await SERA_AUDIT.runDemoFlows()
```

Current expected result:

`11/11 PASS`

Verify that:

- Reset Demo is reversible
- Boundary Challenge remains separate
- Multilingual Demo remains separate
- the declared Tamil and French content is preserved
- the demonstrations do not silently overwrite one another's intended content

---

## 21. Verify Unicode Behavior

Run:

```javascript
await SERA_AUDIT.runUnicode()
```

Current expected result:

`13/13 PASS`

The current reference distinguishes:

`UTF16_CODE_UNIT`

`UNICODE_CODE_POINT`

`EXTENDED_GRAPHEME_CLUSTER`

A conforming host adapter using another native coordinate representation must translate at the declared adapter boundary.

---

## 22. Verify Evidence Behavior

Run:

```javascript
await SERA_AUDIT.runEvidence()
```

Current expected result:

`10/10 PASS`

The current evidence direction includes:

- canonical proposal identity
- target fingerprints
- admission fingerprints
- canonical plans
- preview commitments
- mutation envelopes
- structural edit permits
- refusal witnesses
- receipt chains
- session bundles

The browser reference also provides producer-side replay and chain verification.

---

## 23. Verify Receipt Replay

Open the information panel.

Open:

**Receipts**

Use:

**Replay Session**

Expected principle:

`same genesis + same valid receipt chain + same frozen profiles -> same reconstructed final document identity`

The replay function is producer-side.

It is useful assurance but is not independent verification.

---

## 24. Verify the Receipt Chain

In the Receipts panel, use:

**Verify Chain**

The current receipt architecture distinguishes:

`GENESIS`

`EDIT`

`REFUSAL`

`UNDO`

`REDO`

The chain verifier should verify the declared producer-side receipt-chain relationships.

A valid refusal must preserve the semantic non-mutation relation:

`REFUSAL -> post_document_hash = pre_document_hash`

This relation requires semantic verification.

JSON shape alone is insufficient.

---

## 25. Export an Evidence Bundle

In the Receipts panel, choose:

**Export Evidence Bundle**

The exported bundle is intended to contain the declared replay-oriented evidence for the current session.

Depending on the session, this may include:

- profile manifest
- genesis content
- receipt chain
- final document identity
- chain head
- producer-side verification information

Producer-generated PASS fields are assertions.

They are not independent verification.

---

## 26. JSON Schema Verification Boundary

The current local schema package includes:

`SERA_Proposal_Schema_v1_0.json`

`SERA_Refusal_Witness_Schema_v1_0.json`

`SERA_Receipt_Schema_v2_0.json`

`SERA_Session_Bundle_Schema_v2_0.json`

The schema package declares local schema identities so that inter-schema references can be resolved from the local package by compatible JSON Schema Draft 2020-12 validators.

No hosted SERA schema service is required.

The verification separation is:

`JSON Schema -> structural validity`

`SERA Conformance Specification -> semantic validity`

`independent verifier -> reconstructed evidence validity`

JSON Schema alone cannot prove relations such as:

`prev[n] = receipt_hash[n-1]`

`receipt_hash = recomputed canonical receipt hash`

`REFUSAL -> zero mutation`

`write_set(E_c) subseteq admitted_mutation_envelope`

`preview target = commit target`

`replayed final hash = declared final hash`

These require semantic verification.

---

## 27. Verify Mutation-Envelope Enforcement

The governing law is:

`write_set(E_c) subseteq admitted_mutation_envelope`

where:

`E_c = canonical classical edit plan`

The audit should fail if an admitted plan writes outside its declared envelope.

The expected conflict relation is:

`plan escape -> CONFLICT`

The mutation envelope applies a least-authority principle to the admitted edit.

It is not presented as a complete capability-security system.

---

## 28. Verify State Restoration

The complete release audit captures and restores the user's working state.

Current expected result:

`STATE RESTORATION = 1/1 PASS`

The captured boundary includes, where applicable:

- document text
- schema
- scope
- anchor
- clipboard state
- receipts
- undo stack
- redo stack
- proposal state
- preview state
- editor selection
- editor scroll position
- drawer and modal state
- active inspector tab
- current demonstration mode
- relevant focus state

The full audit must not leave the interface in an unintended test state.

---

## 29. Recommended Complete Verification Sequence

Run:

```javascript
await SERA_AUDIT.runAll()
```

Then:

```javascript
SERADemo.runMultilingualDemoCheck()
```

```javascript
SERADemo.runFrozenGraphemeConformance()
```

```javascript
SERA_AUDIT.regressions()
```

```javascript
SERA_AUDIT.coverage()
```

```javascript
SERA_AUDIT.lastFull()
```

```javascript
SERA_AUDIT.inspect()
```

Current expected headline results:

`FULL AUDIT = 329/329 PASS`

`KNOWN REGRESSIONS = 27/27 PASS`

`FEATURE COVERAGE = 34/34 PASS`

`FROZEN GRAPHEME CONFORMANCE = 766/766 PASS`

`UNCOVERED FEATURES = 0`

`INTEGRITY REGRESSION = 0`

`UNEXPECTED MUTATION = 0`

---

## 30. Verify Browser File Identity

The current repository includes:

`verify/FREEZE_DEMO_SHA256.txt`

Compare the committed browser HTML against the exact SHA-256 recorded in that file.

Run the hash command from the repository root.

### Windows

From the repository root:

```text
certutil -hashfile demo\SERA_Structural_Keyboard_Reference_Demo_v0_9_2.html SHA256
```

### Linux / macOS

```bash
sha256sum demo/SERA_Structural_Keyboard_Reference_Demo_v0_9_2.html
```

The computed SHA-256 must exactly match:

`verify/FREEZE_DEMO_SHA256.txt`

File identity is separate from semantic verification.

The distinction is:

`file hash -> identity of exact browser artifact bytes`

`full audit -> producer-side implementation assurance`

`receipt replay -> producer-side transition reconstruction`

`independent verifier -> separately reconstructed evidence validity`

A file hash alone does not prove SERA semantic correctness.

---

## 31. Assurance Boundary

The current SERA release demonstrates, within the declared browser reference boundary:

- deterministic target resolution for the tested cases
- explicit `AMBIGUOUS` and `UNSUPPORTED` non-resolution
- canonical proposal identity
- strict agent range-hint handling
- canonical planning
- Preview Commitment v2
- No Silent Retarget
- dependency-aware admission
- Structural Relevance classification
- Structural Admission Survival
- mutation-envelope enforcement
- structural edit permits
- deterministic refusal witnesses
- human-readable refusal explanations
- deterministic receipt chaining
- producer-side replay
- verifier-facing fixtures
- grapheme-aware structural scope
- multilingual reference demonstrations
- cumulative permanent regression coverage

The current release does not establish:

- universal linguistic correctness
- universal structural resolution
- semantic correctness of proposed content
- legal authorization
- organizational authorization
- complete cybersecurity protection
- production certification
- third-party certification
- independent verification
- universal concurrency safety
- universal performance superiority
- universal accessibility outcomes
- implemented commutativity certification

---

## 32. Independent Verification Boundary

The current browser may generate:

- receipts
- bundles
- replay results
- verifier fixtures
- producer-side PASS labels

These are not independent verification.

The correct separation is:

`producer audit PASS != independent verifier PASS`

Independent verification requires a separate implementation path that reconstructs declared evidence rather than trusting producer-generated results.

A future independent verifier should recompute, as applicable:

- canonical proposal hashes
- target identities
- plan hashes
- mutation-envelope hashes
- refusal witness hashes
- receipt hashes
- chain continuity
- refusal non-mutation
- replayed final document identity

The intended future relation is:

`producer result == independently reconstructed result`

Independent verification is not currently claimed.

---

## 33. Final Verification Result

A successful current SERA reference verification should establish:

`FULL AUDIT = 329/329 PASS`

`KNOWN REGRESSIONS = 27/27 PASS`

`FEATURE COVERAGE = 34/34 PASS`

`FROZEN GRAPHEME CONFORMANCE = 766/766 PASS`

`INTEGRITY REGRESSION = 0`

`UNEXPECTED MUTATION = 0`

The central authority relation remains:

`proposal authority != target authority != mutation authority`

The central pipeline remains:

`proposal -> resolve -> plan -> preview -> revalidate -> admit -> execute OR refuse -> receipt`

The central concurrency principle remains:

`document changed != proposal automatically stale`

The central commitment law remains:

`preview_target_fingerprint != commit_target_fingerprint -> no execution under old commitment`

The central mutation-boundary law remains:

`write_set(E_c) subseteq admitted_mutation_envelope`

The central refusal law remains:

`valid refusal -> zero mutation + explicit state + stable reason + evidence`

A passing producer-side audit demonstrates that the current reference implementation satisfies its declared browser assurance suite.

It does not constitute independent verification.

This is the SERA verification procedure for the current external reference release.
