# ⭐ FAQ — SERA

## Structural Edit Resolution and Admission

**Deterministic • Dependency-Aware • Refusal-Explicit • Replay-Oriented**

---

## SECTION A — Purpose & Positioning

### A1. What is SERA?

SERA stands for:

`Structural Edit Resolution and Admission`

It is a deterministic reference architecture for governing the boundary between an edit proposal and actual mutation authority.

Its central authority separation is:

`proposal authority != target authority != mutation authority`

A human, AI agent, API, assistive system, or other declared source may propose an edit.

The proposal does not automatically determine the exact target.

A resolved target does not automatically authorize mutation.

A canonical plan does not automatically receive authority to write outside its admitted mutation envelope.

The core processing relation is:

`proposal -> resolve -> plan -> preview -> revalidate -> admit -> execute OR refuse -> receipt`

---

### A2. What is Structural Keyboard?

Structural Keyboard is the reference human interaction surface for SERA.

Its human-facing principle is:

`Edit at the level you think.`

Structural Keyboard demonstrates how a human can work with structural units such as:

- `GRAPHEME`
- `CODE_POINT`
- `WORD`
- `SENTENCE`
- `PARAGRAPH`
- `LIST_ITEM`
- `SECTION`

SERA is the architecture.

Structural Keyboard is one reference interaction surface.

---

### A3. What problem does SERA explore?

SERA explores how an edit proposal can remain separate from the authority to mutate a document.

This is especially relevant to machine and agent editing, where systems may produce:

- patches
- ranges
- replacements
- workspace edits
- raw coordinates
- structural locators

If such output is applied directly, the proposal artifact may become practical mutation authority.

SERA inserts a structural admission boundary between:

`what was proposed`

and:

`what is actually permitted to change`

---

### A4. What is the core idea in one line?

`Anyone may propose. Structure resolves. Admission permits. Evidence records.`

---

### A5. What is the major architectural shift?

The major shift is that proposal information is not treated as self-authorizing mutation authority.

Instead:

`proposal -> independently resolved target -> canonical plan -> revalidation -> admitted write authority`

This keeps three responsibilities separate:

`proposal authority`

`target authority`

`mutation authority`

---

### A6. Is SERA a keyboard technology?

No.

Structural Keyboard is the reference human interaction surface.

SERA itself is the broader edit-resolution and admission architecture.

The same contract may be used with:

- AI-agent proposal adapters
- APIs
- assistive systems
- code editors
- document editors
- workspace services
- other host environments

---

### A7. Is SERA mainly intended for AI agents?

Machine and agent editing is the strongest near-term application direction.

However, the architecture is actor-independent.

Current declared proposal sources include:

`HUMAN`

`AI_AGENT`

`API`

`ASSISTIVE_TECHNOLOGY`

The proposal source is evidence.

It does not become structural authority.

---

### A8. Does SERA replace normal editing mechanisms?

No.

SERA may continue to use:

- ranges
- offsets
- patches
- replacements
- editor transactions
- host mutation APIs

The difference is their authority role.

`execution mechanism may remain`

while:

`execution mechanism != structural admission authority`

---

### A9. Does SERA replace collaborative editing systems?

No.

Collaborative reconciliation and SERA answer different questions.

A collaborative system may ask:

`how are concurrent states or operations combined?`

SERA asks:

`may this particular proposed mutation still execute against the structure that now exists?`

The relationship is:

`state reconciliation != edit admission`

The two may coexist.

---

### A10. Is SERA a security system?

SERA applies ideas similar to least-authority mutation and check/use protection within its declared edit-admission boundary.

However, it is not presented as a complete security architecture, access-control system, capability-security system, or authorization framework.

Its scope is narrower:

`structural edit resolution + admission + bounded mutation + evidence`

---

## SECTION B — Core Authority Model

### B1. What is proposal authority?

Proposal authority is the ability to express edit intent.

A proposal may declare information such as:

- source
- schema
- scope
- locator
- action
- payload
- expected profile
- optional document identity
- optional range hint

A proposal does not automatically determine the final executable target.

---

### B2. What is target authority?

Target authority belongs to the declared resolver under the active schema and frozen rules.

Resolution may return:

- `RESOLVED`
- `AMBIGUOUS`
- `UNSUPPORTED`

A proposal proceeds to planning only when one supported target is resolved or when a declared profile permits explicit candidate selection.

---

### B3. What is mutation authority?

Mutation authority is the bounded authority to execute an admitted canonical plan.

The governing law is:

`write_set(E_c) subseteq admitted_mutation_envelope`

where:

`E_c = canonical classical edit plan`

A plan that exceeds its admitted mutation envelope must not execute as admitted.

---

### B4. Why separate proposal authority, target authority, and mutation authority?

Because the source that proposes an edit may be wrong about:

- the target
- the current document state
- the required context
- the exact executable range
- the amount of structure that may be safely changed

SERA therefore preserves:

`proposal authority != target authority != mutation authority`

---

### B5. Can the proposal source override the resolver?

Not under the strict proposal model.

A machine-supplied range may be recorded as a locator hint.

It does not silently become the target if independent structural resolution disagrees with it.

---

### B6. Does actor identity create structural authority?

No.

The relation is:

`actor identity = proposal evidence`

`actor identity != structural authority`

The same admission contract applies regardless of whether the proposal comes from a human, agent, API, or assistive system.

---

## SECTION C — Resolution & Structural Scope

### C1. What are the resolution states?

The current top-level resolution states are:

- `RESOLVED`
- `AMBIGUOUS`
- `UNSUPPORTED`

---

### C2. What does `RESOLVED` mean?

`RESOLVED` means the declared resolver identifies one supported target under the active schema and rules.

The resolved result may include:

- span
- structural path
- scope
- target fingerprint
- resolution mode

---

### C3. What does `AMBIGUOUS` mean?

`AMBIGUOUS` means more than one target remains valid under the declared rules, or the resolver intentionally refuses to force one interpretation.

The correct behavior is not to guess silently.

A permitted explicit candidate choice may create new committed evidence.

---

### C4. What does `UNSUPPORTED` mean?

`UNSUPPORTED` means the requested structural interpretation is not supported under the active schema or profile.

The governing principle is:

`unsupported target -> no fabricated precision`

---

### C5. Why does SERA treat non-resolution as a valid result?

Because deterministic behavior includes deterministic refusal to invent unsupported certainty.

The governing principle is:

`deterministic resolution includes deterministic non-resolution`

---

### C6. What structural scopes are currently demonstrated?

The current reference supports TEXT scopes including:

- `GRAPHEME`
- `CODE_POINT`
- `WORD`
- `SENTENCE`
- `PARAGRAPH`

The MARKDOWN schema additionally supports:

- `LIST_ITEM`
- `SECTION`

---

### C7. What is the difference between `GRAPHEME` and `CODE_POINT`?

A Unicode code point is not always a complete user-perceived character.

A grapheme cluster may contain multiple code points.

The current reference therefore distinguishes:

`UTF16_CODE_UNIT != UNICODE_CODE_POINT`

and:

`UNICODE_CODE_POINT != EXTENDED_GRAPHEME_CLUSTER`

`CODE_POINT` is a technical structural scope.

`GRAPHEME` follows the frozen extended-grapheme-cluster profile.

---

### C8. What coordinate unit does the browser reference use?

The current canonical evidence offset unit is:

`UTF16_CODE_UNIT`

This is separate from the human-facing structural unit.

For example:

`evidence offsets -> UTF16_CODE_UNIT`

while:

`GRAPHEME scope -> EXTENDED_GRAPHEME_CLUSTER`

---

### C9. Can another host use UTF-8 byte offsets or another coordinate system?

Yes, but the host adapter must perform an explicit deterministic conversion at the adapter boundary.

The governing distinction is:

`canonical structural identity != host-native coordinate representation`

A host must not silently reinterpret incompatible offset units.

---

## SECTION D — Planning, Preview & Admission

### D1. What is canonical planning?

Let:

`E_s = structural edit intent`

`D = canonical document state`

Then:

`E_c = plan(E_s, D)`

where:

`E_c = canonical classical edit plan`

The canonical plan is the exact operational representation of the structural action.

---

### D2. What operations may appear in a canonical plan?

Current plan forms include operations such as:

`DELETE_RANGE(start, end)`

`INSERT_AT(position, content)`

`REPLACE_RANGE(start, end, content)`

and ordered combinations required by supported structural actions.

---

### D3. Does planning authorize execution?

No.

Planning constructs the exact proposed operation.

Admission determines whether that exact committed plan may execute.

`plan != permission`

---

### D4. What is Preview Commitment?

Preview Commitment binds the exact target, admission subject, action, canonical plan, and mutation envelope presented before commitment.

Conceptually:

`preview_commitment = H(profile + target + admission subject + action + plan + envelope)`

The governing relation is:

`executed admitted plan = previewed committed plan`

---

### D5. What is the No Silent Retarget Law?

The governing law is:

`preview_target_fingerprint != commit_target_fingerprint -> no execution under old commitment`

A changed target requires:

`re-resolve -> new preview -> new commitment -> new admission`

The old commitment may remain as evidence.

It must not transfer authority to a newly resolved target.

---

### D6. What are the admission states?

The current admission states are:

- `ADMITTED`
- `STALE`
- `CONFLICT`

---

### D7. What does `ADMITTED` mean?

`ADMITTED` means the committed target, required dependencies, canonical plan, preview commitment, and mutation envelope remain valid under the active profile.

Only:

`RESOLVED + ADMITTED -> execution`

---

### D8. What does `STALE` mean?

`STALE` means the earlier committed structural meaning is no longer current.

Examples include:

- target content changed
- target boundary changed
- required context changed
- destination relation changed
- canonical plan changed

A stale proposal must not silently execute under the old commitment.

---

### D9. What does `CONFLICT` mean?

`CONFLICT` means the proposal cannot be safely admitted under the declared profile.

Examples may include:

- mutation-envelope violation
- incompatible destination structure
- incompatible concurrent mutation
- invalid structural dependency state

---

### D10. Is a current-state admission check the same as final admission?

No.

A non-mutating check may report that a proposal is currently valid, stale, or conflicting.

But:

`CURRENTLY VALID != ADMITTED`

Final admission remains a commit-time decision.

---

## SECTION E — Dependency-Aware Admission & Concurrency

### E1. What is dependency-aware admission?

SERA separates:

`document_hash`

from:

`admission_fingerprint`

The document hash identifies the complete canonical document.

The admission fingerprint identifies the declared structure on which one proposal actually depends.

This allows SERA to distinguish:

`document changed`

from:

`required structure changed`

---

### E2. Does every document change invalidate every proposal?

No.

The key principle is:

`document changed != proposal automatically stale`

Instead:

`required dependencies unchanged -> authority may survive`

`required dependencies changed -> old authority must not silently survive`

---

### E3. What is the Relevant Change Principle?

The Relevant Change Principle states:

`irrelevant change -> authority may survive`

`relevant change -> authority must be re-established`

The purpose is to avoid both extremes:

`accept everything`

and:

`invalidate everything`

---

### E4. What is Structural Admission Survival?

Structural Admission Survival means a prepared proposal may remain admissible after the document changes when its required structural basis remains valid.

Conceptually:

`concurrent mutation + unchanged required dependencies -> prepared authority may remain valid`

---

### E5. What structural relevance classes are demonstrated?

The reference direction distinguishes classes such as:

- `IRRELEVANT`
- `DEPENDENCY_RELEVANT`
- `TARGET_MUTATING`
- `RULES_RELEVANT`
- `SCHEMA_RELEVANT`

These help explain why authority may survive, require revalidation, or be lost.

---

### E6. Does SERA guarantee that unrelated changes always commute?

No.

Admission survival and commutativity are different properties.

A proposal may remain admissible because its required dependencies are unchanged.

A future commutativity profile may separately test whether:

`A(B(D)) == B(A(D))`

Current commutativity certification remains future work.

---

### E7. What is the difference between whole-document optimistic locking and SERA admission?

Whole-document locking commonly treats any document identity change as grounds for invalidation.

SERA may preserve a prepared proposal when:

`document changed AND required dependencies unchanged`

The difference is:

`global change detection`

versus:

`declared dependency-aware admission`

---

### E8. Does dependency-aware admission eliminate conflicts?

No.

It aims to distinguish relevant and irrelevant change more precisely.

Relevant interference may still produce:

`STALE`

or:

`CONFLICT`

---

## SECTION F — Mutation Envelope & Edit Permits

### F1. What is a mutation envelope?

A mutation envelope defines the admitted write boundary for a canonical plan.

The governing law is:

`write_set(E_c) subseteq admitted_mutation_envelope`

---

### F2. Why is the mutation envelope important?

It applies a least-authority principle to editing.

The proposal receives no more mutation authority than the admitted plan requires.

The relation is:

`resolved action -> minimum declared mutation authority required for that action`

---

### F3. What happens if a plan attempts to write outside its envelope?

The plan must not execute as admitted.

The expected result is a conflict.

`plan escape -> CONFLICT`

---

### F4. What is a structural edit permit?

A structural edit permit is a deterministic admission artifact bound to the admitted transition.

It is associated with the resolved target, required dependencies, canonical plan, and mutation envelope under the declared profile.

A permit is evidence of admitted authority for that transition.

It is not a general-purpose security credential.

---

## SECTION G — Refusal & Evidence

### G1. Why is refusal a first-class feature?

Because safe editing requires explicit non-mutation when the declared conditions do not support execution.

The core law is:

`uncertain target OR invalidated meaning OR excess authority -> no silent mutation`

A valid refusal preserves:

`zero mutation + explicit state + stable reason + evidence`

---

### G2. What kinds of outcomes can produce refusal evidence?

Current refusal families include:

- `AMBIGUOUS`
- `UNSUPPORTED`
- `STALE`
- `CONFLICT`

---

### G3. What is a refusal witness?

A refusal witness is deterministic evidence describing why a proposed mutation did not receive executable authority.

Depending on the refusal family, it may bind information such as:

- candidate-set identity
- requested schema or scope
- expected and current target fingerprints
- expected and current admission fingerprints
- mutation-envelope evidence

---

### G4. Is the human-readable refusal explanation part of canonical evidence?

No.

The separation is:

`reason_code = canonical evidence`

`human explanation = presentation`

A human-readable explanation may improve without changing the deterministic refusal identity.

---

### G5. Why separate explanation from evidence?

Because presentation language may evolve.

The structural evidence should remain stable.

Therefore:

`explanation != evidence authority`

---

### G6. Does a refusal count as a successful SERA outcome?

Yes, when refusal is the correct result under the declared rules.

A correct refusal is not a failed architecture outcome.

It is evidence that unsafe or unsupported mutation did not silently proceed.

---

## SECTION H — Receipts, Replay & Verification

### H1. What is a SERA receipt?

A receipt is deterministic evidence for one declared transition or refusal boundary.

Current receipt kinds include:

- `GENESIS`
- `EDIT`
- `REFUSAL`
- `UNDO`
- `REDO`

---

### H2. What does a receipt record?

Depending on receipt kind, evidence may include:

- proposal identity
- resolution evidence
- admission evidence
- canonical plan
- mutation envelope
- preview commitment
- structural edit permit
- refusal witness
- pre-document identity
- post-document identity
- previous receipt identity

---

### H3. Are receipts chained?

Yes.

The current receipt architecture binds each non-genesis receipt to the previous receipt identity.

The genesis receipt begins the session chain.

---

### H4. Does a refusal mutate the document?

A valid refusal is expected to preserve zero successful mutation.

The semantic relation is:

`REFUSAL -> post_document_hash = pre_document_hash`

This requirement must be verified semantically, not merely assumed from JSON shape.

---

### H5. What is a session bundle?

A session bundle is a producer export containing the information required for replay-oriented verification.

It may include:

- profile manifest
- genesis document
- receipt chain
- final document identity
- chain head
- producer-side checks

Producer checks are assertions.

They are not independent verification.

---

### H6. What does producer-side replay establish?

Producer-side replay checks that the reference implementation can reconstruct its own declared transition sequence.

It is useful assurance.

It is not the same as independent verification.

---

### H7. Is there an independent verifier now?

No.

The current external reference release does not claim independent verification.

The current separation is:

`producer audit PASS != independent verifier PASS`

A separately implemented verifier remains a future assurance milestone.

---

### H8. What should an independent verifier eventually do?

A separate verifier should reconstruct rather than trust producer-generated PASS labels.

It should be able to check areas such as:

- canonical identities
- receipt hashes
- chain continuity
- refusal non-mutation
- plan hashes
- mutation-envelope bounds
- replayed final document identity
- producer and verifier result agreement

---

### H9. What is the current producer-side audit result?

The current verified full release audit is:

`329/329 PASS`

with:

`INTEGRITY REGRESSION = 0`

`UNEXPECTED MUTATION = 0`

`KNOWN REGRESSIONS = 27/27 PASS`

`FEATURE COVERAGE = 34/34 PASS`

`FINAL STATUS = PASS`

The current audit profile is:

`SERA-AUDIT-1-D04`

This is producer-side assurance.

It is not independent certification.

---

### H10. What is the current quick-audit result?

The current quick audit is:

`102/102 PASS`

It is intended for development iteration and fast deterministic verification.

Its current composition contains no layout-dependent checks, so it can also run in headless DOM environments without a rendering engine.

The complete full release gate includes viewport and focus-behavior checks that require a real rendering browser.

The quick audit does not replace the full release gate.

The current verification roles are:

`quick audit -> fast deterministic and headless-compatible reference checks`

`full release audit -> complete producer-side verification in a rendering browser`

`independent verifier -> future reconstruction of declared evidence outside the producer implementation`

---

### H11. What is the current grapheme conformance result?

The current frozen grapheme conformance result is:

`766/766 PASS`

under the declared frozen grapheme profile.

The reference implements grapheme segmentation internally against the declared frozen profile and validates it against the frozen 766-vector conformance corpus rather than delegating segmentation authority to a browser-provided segmentation API.

This keeps declared grapheme behavior reproducible across browser and engine versions under the frozen profile.

This is producer-side conformance evidence for the declared corpus.

It is not a claim of universal linguistic correctness.

---

## SECTION I — JSON Schemas & Interoperability

### I1. Does SERA provide machine-readable JSON schemas?

Yes.

The current local schema package includes:

- `schema/SERA_Proposal_Schema_v1_0.json`
- `schema/SERA_Refusal_Witness_Schema_v1_0.json`
- `schema/SERA_Receipt_Schema_v2_0.json`
- `schema/SERA_Session_Bundle_Schema_v2_0.json`

The schemas are intended to be stored and used locally.

The schema package declares local schema identities so that inter-schema references can be resolved from the local package by compatible JSON Schema Draft 2020-12 validators.

No hosted SERA schema service is required.

---

### I2. Are the JSON schemas the semantic authority?

No.

The separation is:

`JSON Schema -> structural validation`

`SERA Conformance Specification -> normative semantics`

`independent verifier -> reconstructed evidence validity`

---

### I3. Why not put all semantics into JSON Schema?

Because JSON Schema can validate structural properties such as:

- required fields
- types
- enumerated values
- hash string shape

It cannot by itself prove semantic relations such as:

`prev[n] = receipt_hash[n-1]`

`receipt_hash = recomputed canonical hash`

`REFUSAL -> no mutation`

`write_set(E_c) subseteq envelope`

`preview target = commit target`

These require semantic verification.

---

### I4. Does SERA require schema hosting?

No.

The local JSON files are sufficient for the current reference package.

Ordinary operation does not depend on a hosted SERA schema endpoint.

---

### I5. Does the `$schema` declaration create a network dependency?

No.

A `$schema` declaration identifies the JSON Schema dialect.

The SERA architecture does not require network retrieval for ordinary local operation.

---

### I6. Can adapters accept richer proposal inputs than the canonical proposal?

Yes.

A future or external adapter may accept a richer submission envelope containing information such as:

- source metadata
- timestamps
- natural-language intent
- multiple locator hints
- host coordinates

The preferred separation is:

`rich submission envelope -> deterministic normalization -> canonical proposal`

Therefore:

`adapter convenience != canonical identity`

---

## SECTION J — Current Reference Demo

### J1. What does the browser demo demonstrate?

The current browser reference demonstrates:

- persistent structural scope
- structural navigation
- canonical planning
- preview commitment
- explicit ambiguity
- dependency-aware admission
- mutation envelopes
- structural edit permits
- canonical machine proposals
- strict agent range-hint handling
- No Silent Retarget
- refusal witnesses
- human-readable refusal explanations
- Structural Relevance classification
- Structural Admission Survival
- concurrent proposal demonstrations
- Admission Boundary Matrix
- deterministic receipts
- producer-side replay
- verifier fixtures
- grapheme-aware structural resolution
- multilingual demonstration content
- cumulative regression audit

---

### J2. What is the current browser reference version?

The current reference demo is:

`SERA v0.9.2`

The main reference file is:

`demo/SERA_Structural_Keyboard_Reference_Demo_v0_9_2.html`

---

### J3. Does the demo require a server?

No.

Ordinary reference operation is designed to run locally in a current browser.

No server, model, database, or network service is required for ordinary local operation.

---

### J4. Does the demo require an external AI model?

No.

The Agent Proposal interface demonstrates the proposal and admission contract.

It does not require an external model to run the reference behavior.

---

### J5. Does the demo use external runtime libraries?

The current self-contained reference HTML is designed to operate without external runtime libraries for ordinary local use.

---

### J6. What is the main release audit command?

Open the browser developer console and run:

`await SERA_AUDIT.runAll()`

The current expected principal result is:

`329/329 PASS`

---

### J7. What other verification commands are available?

Useful commands include:

`await SERA_AUDIT.quick()`

`SERA_AUDIT.regressions()`

`SERA_AUDIT.coverage()`

`SERA_AUDIT.lastFull()`

`SERA_AUDIT.inspect()`

`SERADemo.runMultilingualDemoCheck()`

`SERADemo.runFrozenGraphemeConformance()`

Focused audit commands are also available for areas such as proposals, refusals, concurrency, admission boundaries, Unicode, and No Silent Retarget.

---

### J8. What is the purpose of Agent Admission Races?

The race demonstrations show that concurrent change can produce different outcomes depending on structural relevance.

The current direction demonstrates cases where:

`independent change -> authority may survive`

and:

`relevant interference -> proposal becomes stale or conflicting`

This supports the principle:

`document changed != proposal automatically stale`

---

### J9. What is the purpose of the Refusal Challenge?

The Refusal Challenge demonstrates:

`RESOLVED + PREVIEWED`

followed by a structural change, then:

`STALE`

`NO MUTATION`

with refusal evidence and a human-readable explanation.

It demonstrates the No Silent Retarget boundary.

---

### J10. What is the purpose of the Multilingual Demo?

The Multilingual Demo provides a separate reference surface for current Tamil and French demonstration content.

It is intentionally separate from the Boundary Challenge.

The deeper Unicode audit also includes additional grapheme and complex-script vectors.

---

## SECTION K — Comparison & Practical Meaning

### K1. How is SERA different from direct range or patch application?

Direct application commonly allows supplied coordinates to determine the practical target.

SERA instead treats proposal coordinates as proposal information and independently resolves the target under the active structural contract.

---

### K2. How is SERA different from character-offset editing?

Character-offset editing depends on position identity and host coordinate behavior.

SERA adds an explicit structural resolution, commitment, dependency revalidation, admission, and bounded-mutation layer.

---

### K3. How is SERA different from whole-document optimistic locking?

Whole-document optimistic locking may invalidate a proposal whenever the document identity changes.

SERA may preserve a proposal when unrelated change occurs and its declared dependencies remain valid.

---

### K4. How is SERA different from structural or tree editing?

Structural editing may already provide robust node or structural-object targeting.

SERA's distinct focus is the joined contract:

`independent resolution + canonical planning + preview commitment + dependency revalidation + bounded mutation + evidenced refusal`

Structural targeting alone is not the complete SERA admission contract.

---

### K5. Does SERA claim that structural editing itself is new?

No.

The project does not base its contribution on the claim that structural navigation, scope-based editing, or tree targeting are new ideas.

Its architectural focus is the combined proposal-to-mutation admission contract.

---

### K6. Does SERA guarantee that AI-generated edits are semantically correct?

No.

SERA does not determine whether proposed content is factually correct, desirable, lawful, secure, or appropriate.

Its concern is whether the proposed mutation has sufficient declared structural authority to execute.

---

### K7. Does SERA guarantee that every edit can be resolved?

No.

The architecture explicitly permits:

`AMBIGUOUS`

and:

`UNSUPPORTED`

Absence is preferred over fabricated precision when the declared resolver cannot safely establish one supported target.

---

### K8. Does SERA guarantee better performance?

No.

The current reference focuses on architecture, deterministic semantics, admission behavior, and evidence.

Large-scale performance and scaling remain areas for future measurement.

---

### K9. Does SERA guarantee better usability?

No universal usability superiority is claimed.

Structural Keyboard is a reference interaction surface.

Broader usability and accessibility claims require dedicated evaluation.

---

### K10. Is SERA production-ready?

No production certification is claimed.

Production deployment would require, where relevant:

- independent verification
- domain-specific testing
- security review
- accessibility review
- operational testing
- performance characterization
- host-adapter validation

---

## SECTION L — Assurance Boundaries & Non-Claims

### L1. What does the current release demonstrate?

Within the declared browser reference and audit boundary, it demonstrates:

- deterministic structural resolution for the tested cases
- explicit non-resolution
- canonical proposal identity
- strict machine range-hint handling
- canonical planning
- Preview Commitment
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
- grapheme-aware scoping
- multilingual reference demonstrations
- cumulative regression protection

---

### L2. What does the current release not establish?

It does not establish:

- universal linguistic correctness
- universal structural resolution
- universal edit safety
- semantic correctness of proposed content
- legal authorization
- organizational authorization
- complete cybersecurity protection
- production readiness
- third-party certification
- independent verification
- universal browser compatibility
- universal accessibility outcomes
- universal performance superiority
- universal concurrency safety
- implemented commutativity certification

---

### L3. Is the current audit independent verification?

No.

The current principal release result is producer-side.

The correct interpretation is:

`the reference implementation passed its declared producer-side regression and assurance suite`

not:

`an independent implementation verified all SERA semantics`

---

### L4. Are formal machine-checked proofs included?

No machine-checked proof is currently claimed.

The architecture is supported through explicit invariants, conformance rules, deterministic evidence, and executable regression tests.

---

### L5. Why is independent verification a separate milestone?

Because a producer can reproduce its own assumptions and implementation errors.

Independent verification requires a separate implementation path that reconstructs declared evidence rather than trusting the producer's own result labels.

---

## SECTION M — Future Work

### M1. What are the strongest next assurance priorities?

Current priorities include:

- independent replay verifier
- frozen adversarial concurrent-edit corpus
- dependency-survival measurement
- independent second resolver
- second host adapter
- cross-offset adapter conformance
- broader multilingual review
- performance and scaling measurement
- accessibility qualification
- bounded commutativity certification

---

### M2. What should an adversarial corpus measure?

A useful corpus should measure both unsafe acceptance and unnecessary invalidation.

Relevant outcomes include:

- silent wrong mutation
- explicit correct refusal
- correct target mutation
- over-broad mutation
- safe continued admission
- unnecessary proposal invalidation

This is important because dependency-aware admission should demonstrate both:

`zero silent mutation`

and:

`useful authority survival where declared dependencies remain valid`

---

### M3. Why is a second host adapter useful?

A second host adapter would demonstrate that:

`SERA semantics != browser UI semantics`

and:

`same admission architecture -> multiple execution hosts`

A minimal file or command-line host would be sufficient for this purpose.

---

### M4. Why is a second resolver useful?

An independently implemented resolver can help detect assumptions accidentally shared by one implementation path.

It is most useful after verifier-facing semantics are sufficiently frozen.

---

### M5. What is the future commutativity direction?

For two plans `A` and `B`, a future profile may evaluate:

`A(B(D)) == B(A(D))`

Possible outcomes may include:

- `COMMUTES`
- `DOES_NOT_COMMUTE`
- `NOT_PROVEN`

This remains future work.

---

## SECTION N — Shunyaya Ecosystem Context

### N1. How should SERA be described within the wider Shunyaya ecosystem?

SERA is best described as a structural edit-resolution and admission architecture.

Its central focus is:

- proposal authority separation
- structural target resolution
- canonical pre-commit planning
- dependency-aware admission
- bounded mutation authority
- explicit refusal
- deterministic evidence

---

### N2. What is the unifying SERA principle?

`Anyone may propose. Structure resolves. Admission permits. Evidence records.`

---

### N3. What is the Structural Keyboard principle?

`Edit at the level you think.`

---

## 📝 Note on Naming

SERA in this repository means:

`Structural Edit Resolution and Admission`

within the Shunyaya ecosystem.

It is unrelated to other uses of the same acronym.

---

## ⭐ Final Summary

SERA is a deterministic structural edit-resolution and admission architecture.

Its central authority law is:

`proposal authority != target authority != mutation authority`

Its processing relation is:

`proposal -> resolve -> plan -> preview -> revalidate -> admit -> execute OR refuse -> receipt`

Its concurrency principle is:

`document changed != proposal automatically stale`

Its dependency principle is:

`required dependencies unchanged -> authority may survive`

`required dependencies changed -> old authority must not silently survive`

Its preview law is:

`preview_target_fingerprint != commit_target_fingerprint -> no execution under old commitment`

Its mutation-boundary law is:

`write_set(E_c) subseteq admitted_mutation_envelope`

Its refusal law is:

`valid refusal -> zero mutation + explicit state + stable reason + evidence`

The current browser reference has demonstrated a producer-side release audit of:

`329/329 PASS`

with:

`27/27 known regressions PASS`

`34/34 feature coverage PASS`

`766/766 frozen grapheme conformance PASS`

`INTEGRITY REGRESSION = 0`

`UNEXPECTED MUTATION = 0`

Independent verification, a second resolver, broader host deployment, adversarial corpus publication, and commutativity certification remain future work.

**This is SERA — Structural Edit Resolution and Admission.**
