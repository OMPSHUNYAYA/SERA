# ⭐ SERA — Quickstart

## Structural Edit Resolution and Admission

**Reference Demo:** `SERA v0.9.2`  
**Reference Surface:** Structural Keyboard  
**Audit Profile:** `SERA-AUDIT-1-D04`  
**Primary Rules:** `SK-RULES-1.1.0`

**Deterministic • Dependency-Aware • Refusal-Explicit • Replay-Oriented**

---

# What SERA Demonstrates

SERA is a deterministic reference architecture for governing the boundary between an edit proposal and actual mutation authority.

Its central authority separation is:

`proposal authority != target authority != mutation authority`

Its core processing relation is:

`proposal -> resolve -> plan -> preview -> revalidate -> admit -> execute OR refuse -> receipt`

The public principle is:

`Anyone may propose. Structure resolves. Admission permits. Evidence records.`

The human-facing Structural Keyboard principle is:

`Edit at the level you think.`

The current browser reference demonstrates:

- structural target resolution
- canonical pre-commit planning
- preview commitment
- commit-time revalidation
- dependency-aware admission
- No Silent Retarget
- Structural Relevance classification
- Structural Admission Survival
- bounded mutation authority
- structural edit permits
- explicit refusal witnesses
- human-readable refusal explanations
- deterministic receipts
- producer-side replay
- verifier-facing evidence fixtures
- grapheme-aware structural scope
- multilingual reference content
- cumulative regression assurance

---

# 30-Second Start

Open:

`demo/SERA_Structural_Keyboard_Reference_Demo_v0_9_2.html`

in a current desktop browser.

No server is required for ordinary local operation.

Then:

1. Click inside the document.
2. Choose a structural **Scope**.
3. Use the **Prev/Next** controls or `Alt + Left / Right` to navigate structural units.
4. Use the structural editing controls to Cut, Copy, Paste, Delete, Duplicate, or Move the current unit.
5. Open **Agent Proposal** to test machine-originated edit proposals.
6. Open **Refusal Challenge** to see stale authority refused without mutation.
7. Open **Two-Agent Structural Admission Races** from the information panel to compare relevant and irrelevant concurrent change.
8. Open the browser developer console and run:

```javascript
await SERA_AUDIT.runAll()
```

Expected principal result:

```text
TOTAL                    329/329 PASS
INTEGRITY REGRESSION     0
UNEXPECTED MUTATION      0
KNOWN REGRESSIONS        27/27 PASS
FEATURE COVERAGE         34/34 PASS
FINAL STATUS: PASS
```

This result is producer-side assurance.

It is not independent verification.

---

# Minimum Requirements

- a current desktop browser
- JavaScript enabled
- local file access sufficient to open the HTML file
- no server required
- no database required
- no external AI model required
- no external runtime library required for ordinary local reference use
- no network connection required for ordinary local reference use

A browser may display a local `file:` origin warning in the developer console.

That warning does not by itself indicate a SERA audit failure.

The release gate is the SERA audit result.

---

# Current Repository Layout

The current public-release repository layout is:

```text
SERA/

├── LICENSE
├── README.md
│
├── demo/
│   └── SERA_Structural_Keyboard_Reference_Demo_v0_9_2.html
│
├── docs/
│   ├── FAQ.md
│   ├── Quickstart.md
│   ├── SERA-Architecture-Diagram.png
│   ├── SERA_Architecture_At_A_Glance_v1_0.md
│   ├── SERA_v0_9_2_Console_Audit_Commands.txt
│   │
│   └── specs/
│       ├── SERA_Audit_and_Assurance_v0_9_2.txt
│       ├── SERA_Conformance_v0_2_0.txt
│       └── SERA_Core_Architecture_v0_9_2.txt
│
├── schema/
│   ├── SERA_Proposal_Schema_v1_0.json
│   ├── SERA_Receipt_Schema_v2_0.json
│   ├── SERA_Refusal_Witness_Schema_v1_0.json
│   └── SERA_Session_Bundle_Schema_v2_0.json
│
└── verify/
    ├── FREEZE_DEMO_SHA256.txt
    └── VERIFY.md
```

All repository paths in this Quickstart are written relative to the repository root.

The JSON schemas provide structural validation support.

They do not replace the SERA Conformance Specification.

---

# The Core Interaction Model

SERA separates three kinds of authority.

## Proposal authority

A human, AI agent, API, assistive system, or another declared source may propose an edit.

The proposal may contain:

- source
- schema
- scope
- locator
- action
- payload
- optional expected document identity
- optional range hint

The proposal does not automatically become the executable target.

---

## Target authority

The resolver determines the supported target under the active schema and frozen rules.

Resolution may return:

`RESOLVED`

`AMBIGUOUS`

`UNSUPPORTED`

---

## Mutation authority

Only an admitted canonical plan may execute.

The governing law is:

`write_set(E_c) subseteq admitted_mutation_envelope`

where:

`E_c = canonical classical edit plan`

The complete authority path is:

`proposal -> target resolution -> canonical plan -> preview commitment -> commit-time revalidation -> admission -> bounded execution`

---

# Structural Scope

The current TEXT schema exposes:

`GRAPHEME`

`CODE_POINT`

`WORD`

`SENTENCE`

`PARAGRAPH`

The MARKDOWN schema additionally exposes:

`LIST_ITEM`

`SECTION`

The current reference distinguishes:

`UTF16_CODE_UNIT`

from:

`UNICODE_CODE_POINT`

from:

`EXTENDED_GRAPHEME_CLUSTER`

The browser evidence coordinate unit is:

`UTF16_CODE_UNIT`

The human-facing grapheme scope uses:

`EXTENDED_GRAPHEME_CLUSTER`

under the frozen grapheme profile.

---

# Basic Human Workflow

## 1. Choose a target

Click near the text you want to work with.

Then select a scope such as:

`WORD`

`SENTENCE`

or:

`PARAGRAPH`

The resolver determines the current structural target.

---

## 2. Navigate structurally

Use the **Prev/Next** controls or:

`Alt + Left / Right`

to move between structural units at the selected scope.

Navigation changes the current structural target without changing the document.

---

## 3. Preview an action

Hover or focus an editing action.

The interface displays the pre-commit classical plan.

Conceptually:

`E_c = plan(E_s, D)`

where:

`E_s = structural edit intent`

`D = canonical document state`

---

## 4. Commit the action

A mutating action proceeds through:

`preview -> revalidate -> admit`

Only an admitted plan may execute.

---

## 5. Inspect the evidence

Open the information panel and use the Structural Inspector.

Available areas include:

- Resolution
- Admission
- Plan
- Receipts

---

# Keyboard Shortcuts

The current reference supports keyboard-first workflows.

Useful shortcuts include:

`Alt + Left / Right -> structural navigation`

`Alt + Shift + Left / Right -> structural movement`

`Alt + Up / Down -> change structural scope`

`Alt + 1 / 2 / 3 -> choose an ambiguity candidate`

`Ctrl + S -> save current document`

Use the `?` button in the interface for the complete keymap.

---

# Agent Proposal Quickstart

Open:

**Agent Proposal**

The proposal interface demonstrates that:

`generated edit != admitted edit`

A machine proposal may declare:

- proposal ID
- proposal source
- proposal authority mode
- structural scope
- structural locator
- optional machine range hint
- action

The strict proposal relation is:

`machine-supplied range = locator hint`

not:

`machine-supplied range = mutation authority`

---

## Recommended first agent test

Use:

`Proposal source = AI_AGENT`

`Proposal authority mode = STRICT_STRUCTURAL`

`Scope = SENTENCE`

`Structural locator = current`

Choose a supported action.

Press:

**Evaluate Proposal**

The proposal should be independently resolved and evaluated under the SERA admission contract.

If the proposal becomes admitted, the commit button becomes available.

---

## Test a mismatching range hint

Supply a machine range hint that does not match the independently resolved target.

Under strict mode, the range hint must not silently replace the resolved target.

The expected principle is:

`proposal coordinates != target authority`

---

# Refusal Challenge

Open:

**Refusal Challenge**

The demonstration automatically:

1. prepares a structural edit
2. binds a preview commitment
3. changes the target structure
4. revalidates the old commitment
5. refuses execution

Expected outcome:

`STALE`

with:

`NO MUTATION`

The governing law is:

`preview_target_fingerprint != commit_target_fingerprint -> no execution under old commitment`

The refusal includes:

- deterministic refusal evidence
- a stable reason code
- a human-readable explanation

The explanation is presentation.

The refusal witness is evidence.

---

# Boundary Challenge

Press:

**Boundary Challenge**

Then choose:

`SENTENCE`

The frozen reference rules deliberately expose selected ambiguity conditions.

When the active structure does not support one safe target, the resolver may return:

`AMBIGUOUS`

rather than silently guessing.

---

# Multilingual Demo

Press:

**Multilingual Demo**

The current demonstration includes dedicated Tamil and French content.

The Multilingual Demo is intentionally separate from the Boundary Challenge.

The reference audit also exercises additional Unicode and grapheme vectors.

---

# Compare Current Target

Open:

**Compare Current Target**

The result appears automatically.

The comparison demonstrates the difference between:

`forced target selection`

and:

`SERA structural resolution`

Use:

**Run Again**

to recompute the comparison against the current document state.

---

# Two-Agent Structural Admission Races

Open the information panel and choose:

**Two-Agent Structural Admission Races**

The current demonstrations show that concurrent document change can produce different results depending on structural relevance.

The key principle is:

`document changed != proposal automatically stale`

Representative outcomes include:

## Independent change

`required dependencies unchanged -> prepared authority may survive`

## Relevant interference

`required dependencies changed -> proposal becomes STALE or CONFLICT`

This demonstrates Structural Admission Survival.

---

# Relevant Change Principle

SERA separates:

`document_hash`

from:

`admission_fingerprint`

The document hash identifies the complete canonical document.

The admission fingerprint identifies the declared structure required by one proposal.

Therefore:

`irrelevant change -> authority may survive`

`relevant change -> authority must be re-established`

This is the Relevant Change Principle.

---

# Structural Admission Survival

A prepared proposal may remain admissible after the document changes when:

- the resolved target remains valid
- the required structural dependencies remain valid
- the canonical plan remains valid
- the admitted mutation envelope remains valid

Conceptually:

`concurrent mutation + unchanged required dependencies -> prepared authority may remain valid`

---

# Admission States

The current admission layer returns:

`ADMITTED`

`STALE`

`CONFLICT`

## `ADMITTED`

The committed target, dependencies, plan, and mutation boundary remain valid.

## `STALE`

The earlier structural meaning is no longer current.

## `CONFLICT`

The proposal cannot safely execute under the declared admission contract.

Only:

`RESOLVED + ADMITTED -> execution`

---

# No Silent Retarget

The central commitment law is:

`preview_target_fingerprint != commit_target_fingerprint -> no execution under old commitment`

A valid continuation requires:

`re-resolve -> new preview -> new commitment -> new admission`

The old commitment must not silently transfer authority to a new target.

---

# Mutation Envelope

Every admitted mutating plan is bounded by a declared mutation envelope.

The governing relation is:

`write_set(E_c) subseteq admitted_mutation_envelope`

If the plan attempts to escape its admitted boundary:

`plan escape -> CONFLICT`

---

# Refusal Is a Valid Outcome

SERA treats refusal as a first-class non-mutating result.

A valid refusal preserves:

`zero mutation + explicit state + stable reason + evidence`

Refusal states may include:

`AMBIGUOUS`

`UNSUPPORTED`

`STALE`

`CONFLICT`

The objective is:

`unsafe or unsupported mutation -> explicit refusal`

not:

`unsafe or unsupported mutation -> silent best guess`

---

# Receipts & Replay

Open the information panel and select:

**Receipts**

Available actions include:

- Replay Session
- Verify Chain
- Export Evidence Bundle

The current receipt families include:

`GENESIS`

`EDIT`

`REFUSAL`

`UNDO`

`REDO`

The current browser verification is producer-side.

The exported evidence bundle is intended for separate replay-oriented verification.

---

# Main Release Verification

Open the browser developer console.

Run:

```javascript
await SERA_AUDIT.runAll()
```

Expected:

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

---

# Quick Development Audit

Run:

```javascript
await SERA_AUDIT.quick()
```

Current expected result:

`102/102 PASS`

The quick audit supports development iteration.

It does not replace the complete release gate.

---

# Recommended Release Verification Sequence

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

Expected current results include:

`FULL AUDIT = 329/329 PASS`

`KNOWN REGRESSIONS = 27/27 PASS`

`FEATURE COVERAGE = 34/34 PASS`

`FROZEN GRAPHEME CONFORMANCE = 766/766 PASS`

`UNCOVERED FEATURES = 0`

`INTEGRITY REGRESSION = 0`

`UNEXPECTED MUTATION = 0`

---

# Focused Audit Commands

Useful focused checks include:

```javascript
await SERA_AUDIT.runProposals()
```

Expected:

`16/16 PASS`

```javascript
await SERA_AUDIT.runRefusalWitnesses()
```

Expected:

`11/11 PASS`

```javascript
await SERA_AUDIT.runNoSilentRetarget()
```

Expected:

`6/6 PASS`

```javascript
await SERA_AUDIT.runConcurrency()
```

Expected:

`9/9 PASS`

```javascript
await SERA_AUDIT.runAdmissionBoundary()
```

Expected:

`9/9 PASS`

```javascript
await SERA_AUDIT.runUnicode()
```

Expected:

`13/13 PASS`

---

# Feature Coverage

Run:

```javascript
SERA_AUDIT.coverage()
```

Current expected result:

`34/34 PASS`

with:

`UNCOVERED FEATURES = 0`

Current coverage includes areas such as:

- Agent Proposal
- Canonical Proposal Identity
- Strict Agent Proposal Authority
- No Silent Retarget
- Refusal Witnesses
- Human-Readable Refusal Explanations
- Preview Commitment
- Compare Current Target
- Refusal Challenge
- Boundary Challenge
- Multilingual Demo
- Reset Demo
- Structural Navigation
- Viewport Following
- Interactive Status Controls
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

---

# Known Regressions

Run:

```javascript
SERA_AUDIT.regressions()
```

Current expected result:

`27/27 PASS`

The governing development law is:

`bug found -> fix implemented -> permanent regression test added -> runAll() must pass`

---

# JSON Schemas

The current local schema files are:

`schema/SERA_Proposal_Schema_v1_0.json`

`schema/SERA_Refusal_Witness_Schema_v1_0.json`

`schema/SERA_Receipt_Schema_v2_0.json`

`schema/SERA_Session_Bundle_Schema_v2_0.json`

Their role is:

`JSON Schema -> structural validation`

The semantic authority remains:

`SERA Conformance Specification -> normative semantics`

A future independent verifier is responsible for:

`reconstructed evidence validity`

No hosted SERA schema service is required.

---

# Verification Boundaries

The current browser reference provides:

- producer-side regression audit
- producer-side replay
- receipt-chain verification
- evidence-bundle export
- verifier-facing fixtures

It does not currently provide:

- independent verification
- third-party certification
- production certification
- universal linguistic correctness
- universal edit safety
- implemented commutativity certification

The correct current interpretation is:

`reference implementation passed its declared producer-side assurance suite`

not:

`all SERA semantics have been independently verified`

---

# What SERA Demonstrates

Within the current declared reference boundary:

- proposal source does not automatically become target authority
- target resolution is explicit
- ambiguity and unsupported structure may refuse mutation
- canonical plans are inspectable before execution
- preview commitments bind exact edit intent
- changed targets cannot inherit old authority
- unrelated document change does not automatically invalidate a proposal
- relevant structural change may invalidate prepared authority
- admitted mutation is bounded
- refusal is explicit and evidence-bearing
- human-readable explanations remain separate from canonical refusal evidence
- deterministic receipts support replay-oriented evidence
- grapheme-aware and code-point scopes remain distinct
- producer-side regression coverage is cumulative

---

# What SERA Does Not Claim

The current reference does not establish:

- universal edit correctness
- universal linguistic correctness
- semantic correctness of proposed content
- legal authorization
- organizational authorization
- complete cybersecurity protection
- production readiness
- independent verification
- third-party certification
- universal concurrency safety
- universal performance superiority
- universal accessibility outcomes

SERA is a reference architecture and research implementation.

---

# Recommended Reading Order

For a complete review:

1. `README.md`
2. `docs/Quickstart.md`
3. `docs/SERA_Architecture_At_A_Glance_v1_0.md`
4. `docs/specs/SERA_Core_Architecture_v0_9_2.txt`
5. `docs/specs/SERA_Conformance_v0_2_0.txt`
6. `docs/specs/SERA_Audit_and_Assurance_v0_9_2.txt`
7. `docs/FAQ.md`
8. `docs/SERA_v0_9_2_Console_Audit_Commands.txt`
9. `verify/VERIFY.md`

The primary executable reference is:

`demo/SERA_Structural_Keyboard_Reference_Demo_v0_9_2.html`

The architecture diagram is:

`docs/SERA-Architecture-Diagram.png`

---

# Final Summary

SERA separates:

`proposal authority`

from:

`target authority`

from:

`mutation authority`

The core pipeline is:

`proposal -> resolve -> plan -> preview -> revalidate -> admit -> execute OR refuse -> receipt`

The main concurrency principle is:

`document changed != proposal automatically stale`

The dependency principle is:

`required dependencies unchanged -> authority may survive`

`required dependencies changed -> old authority must not silently survive`

The No Silent Retarget law is:

`preview_target_fingerprint != commit_target_fingerprint -> no execution under old commitment`

The mutation-boundary law is:

`write_set(E_c) subseteq admitted_mutation_envelope`

The refusal law is:

`valid refusal -> zero mutation + explicit state + stable reason + evidence`

To begin:

1. Open `demo/SERA_Structural_Keyboard_Reference_Demo_v0_9_2.html`.
2. Explore structural scopes and edit actions.
3. Open Agent Proposal and Refusal Challenge.
4. Run:

```javascript
await SERA_AUDIT.runAll()
```

Confirm:

`329/329 PASS`

Then inspect:

```javascript
SERA_AUDIT.coverage()
```

and:

```javascript
SERA_AUDIT.regressions()
```

This is the SERA Quickstart.
