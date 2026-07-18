# SERA

## Architecture At A Glance

**Document version:** v1.0  
**Project:** SERA - Structural Edit Resolution and Admission  
**Reference human interaction surface:** Structural Keyboard  
**Version date:** July 2026  
**Status:** External architecture overview for the current SERA v0.9.2 reference implementation.

---

## 1. What SERA Is

SERA is a deterministic edit-resolution and admission architecture that governs the boundary between an edit proposal and actual mutation authority.

Its central authority separation is:

`proposal authority != target authority != mutation authority`

A human, AI agent, API, assistive system, automation layer, or other declared source may propose an edit.

The proposal does not automatically determine the exact target.

A resolved target does not automatically authorize mutation.

A planned edit does not automatically receive authority to write outside the structure required by that plan.

The governing pipeline is:

`proposal -> resolve -> plan -> preview -> revalidate -> admit -> execute OR refuse -> receipt`

The public principle is:

`Anyone may propose. Structure resolves. Admission permits. Evidence records.`

The human-facing Structural Keyboard principle is:

`Edit at the level you think.`

---

## 2. The Problem

Many editing paths ultimately operate through:

- `offsets`
- `ranges`
- `patches`
- `replacements`
- `transactions`
- `structural nodes`

These mechanisms are useful and remain compatible with SERA.

The SERA problem is different:

`the artifact that proposes an edit should not silently become the authority over what is changed`

This is especially important for machine and agent editing.

A machine may propose:

- `range`
- `patch`
- `replacement`
- `workspace edit`
- `structural locator`
- `raw coordinates`

SERA treats these as proposal information rather than automatic mutation authority.

The intended relation is:

`agent proposes -> SERA resolves and admits -> host executes`

This separates:

`model proposal quality != edit-admission correctness`

---

## 3. The Three Failure Classes

SERA is designed to address three broad classes of silent editing failure within a declared profile.

### Silent mis-targeting

`proposal points to the wrong structure -> mutation still proceeds`

### Stale application

`required structure changes after preview -> old authority still executes`

### Over-broad mutation

`declared edit intent is narrow -> actual write exceeds required structure`

SERA responds through:

- `independent resolution`
- `canonical planning`
- `preview commitment`
- `commit-time structural revalidation`
- `dependency-aware admission`
- `bounded mutation authority`
- `explicit refusal`
- `deterministic evidence`

---

## 4. Dependency-Aware Admission

SERA separates:

`document_hash`

from:

`admission_fingerprint`

The document hash identifies the complete canonical document.

The admission fingerprint identifies the declared structure on which one proposal actually depends.

The key principle is:

`document changed != proposal automatically stale`

Instead:

`required dependency changed -> revalidation or refusal`

`required dependency unchanged -> proposal may remain admissible`

This creates the Relevant Change Principle:

`irrelevant change must not automatically invalidate valid edit authority`

paired with:

`dependency-changing mutation must not silently preserve old edit authority`

The resulting relation is:

`unrelated change -> authority may survive`

`relevant change -> authority must be re-established`

This is Structural Admission Survival:

`concurrent mutation + unchanged required dependencies -> preserved admissibility may remain possible`

SERA therefore aims to avoid both extremes:

`accept everything`

and:

`invalidate everything`

The objective is:

`preserve edit authority exactly while its required structure remains valid`

---

## 5. No Silent Retarget

A prepared edit must not silently transfer its authority to a different target.

The governing law is:

`preview_target_fingerprint != commit_target_fingerprint -> no execution under old commitment`

A valid continuation requires:

`re-resolve -> new preview -> new commitment -> new admission`

The old proposal may remain as evidence.

Its authority must not silently move to newly resolved structure.

This rule applies regardless of proposal source:

- `HUMAN`
- `AI_AGENT`
- `API`
- `ASSISTIVE_TECHNOLOGY`

---

## 6. Minimum Mutation Authority

After resolution and canonical planning, SERA derives a mutation envelope.

The governing law is:

`write_set(E_c) subseteq admitted_mutation_envelope`

where:

`E_c = canonical classical edit plan`

The structural least-authority principle is:

`resolved action -> minimum declared mutation authority required for that action`

If the plan attempts to write outside the admitted envelope:

`plan escape -> CONFLICT -> no admitted execution`

The mutation envelope does not replace host execution mechanisms.

It bounds the authority under which they may execute.

---

## 7. Refusal Is a Valid Outcome

SERA does not force a mutation when the declared structure does not support one.

Resolution may return:

- `RESOLVED`
- `AMBIGUOUS`
- `UNSUPPORTED`

Admission may return:

- `ADMITTED`
- `STALE`
- `CONFLICT`

A correct refusal preserves:

`zero mutation + explicit state + stable reason + evidence`

The governing principle is:

`uncertain target OR invalidated meaning OR excess authority -> no silent mutation`

The refusal witness is machine-verifiable evidence.

A human-readable explanation may be presented alongside it.

The two remain distinct:

`refusal witness = deterministic evidence`

`refusal explanation = human-readable interpretation`

`explanation != evidence authority`

---

## 8. Structural Relevance

A concurrent change may be classified relative to a prepared proposal.

Representative relevance classes are:

- `IRRELEVANT`
- `DEPENDENCY_RELEVANT`
- `TARGET_MUTATING`
- `RULES_RELEVANT`
- `SCHEMA_RELEVANT`

Their role is explanatory and may support future evidence profiles.

Conceptually:

`IRRELEVANT -> commitment may survive`

`DEPENDENCY_RELEVANT -> revalidate`

`TARGET_MUTATING -> old commitment cannot execute`

`RULES_RELEVANT -> re-resolve under applicable rules`

`SCHEMA_RELEVANT -> re-resolve under applicable schema`

A future Minimal Invalidating Witness may identify the smallest declared structural difference sufficient to invalidate admission.

The objective is to explain:

`why authority was lost`

rather than merely:

`the document changed`

---

## 9. SERA and Other Editing Mechanism Classes

SERA does not replace ordinary editing, patching, structural representation, version checking, or collaborative reconciliation.

Those mechanisms answer different questions.

Direct edit mechanisms ask:

`how is the change represented and applied?`

Collaborative reconciliation asks:

`how are concurrent states or operations combined?`

SERA asks:

`may this particular proposed mutation still execute against the structure that now exists?`

A compact property comparison follows.

### Direct patch or range application

- supplied coordinates commonly determine the practical target;
- stale context may cause failure, relocation, or unintended effect depending on the mechanism;
- structural admission is not inherent.

### Character-offset editing

- caret or selection positions determine the action target;
- correctness depends on how position identity is maintained as content changes.

### Whole-document version admission

- a complete document identity may gate execution;
- any detected document change may invalidate the proposal, including unrelated change;
- version equality does not independently establish target correctness.

### Collaborative reconciliation

- concurrent state or operations are reconciled under the collaboration model;
- structural proposal admission is a separate concern;
- SERA may operate beside or above such a layer.

### Structural or tree-based editing

- structural objects may determine targets directly;
- identity and revalidation behavior depend on the structural model;
- structural selection alone does not imply the complete SERA admission contract.

### SERA

- proposal information enters independent structural resolution;
- proposal coordinates may remain locator hints rather than mutation authority;
- declared dependencies govern staleness;
- commit-time revalidation protects the committed target and plan;
- mutation authority is bounded by an admitted envelope;
- refusal is explicit and evidence-bearing.

The architectural distinction is:

`state reconciliation != edit admission`

and:

`structural targeting alone != structural admission`

---

## 10. Actor-Independent Proposal Contract

SERA accepts multiple proposal sources through one declared contract.

Current source classes include:

- `HUMAN`
- `AI_AGENT`
- `API`
- `ASSISTIVE_TECHNOLOGY`

The source is evidence.

It does not become target authority.

The governing relation is:

`actor identity = proposal evidence`

`actor identity != structural authority`

For strict machine proposals:

`machine-supplied range = locator hint`

not:

`machine-supplied range = mutation authority`

---

## 11. Canonical Proposal and Adapter Separation

A deployment may accept a rich submission envelope containing convenient adapter information.

Examples may include:

- `source metadata`
- `timestamps`
- `natural-language intent`
- `host coordinates`
- `multiple locator hints`

Such information should not silently redefine the canonical proposal identity.

The preferred separation is:

`rich submission envelope -> deterministic normalization -> canonical proposal`

followed by:

`canonical proposal -> independent resolution -> admission -> bounded execution`

This preserves:

`adapter convenience != canonical identity`

and:

`submission metadata != mutation authority`

---

## 12. Host and Coordinate Boundary

SERA distinguishes canonical structural meaning from host-native coordinate representation.

The current reference evidence offset unit is:

`UTF16_CODE_UNIT`

A host using another native unit must translate at the declared adapter boundary.

The governing principle is:

`canonical structural span -> declared translation -> host-native span`

A host adapter must not consume incompatible coordinate units without declared conversion.

The broader rule is:

`canonical structural identity != host offset representation`

---

## 13. Evidence

SERA records declared transitions and refusals through deterministic evidence profiles.

The current evidence direction includes:

- `proposal identity`
- `target fingerprint`
- `admission fingerprint`
- `canonical plan`
- `preview commitment`
- `mutation envelope`
- `edit permit`
- `refusal witness`
- `receipt chain`
- `session bundle`

The current architectural separation is:

`JSON Schema -> structural validation`

`SERA Conformance Specification -> normative semantics`

`independent verifier -> reconstructed evidence validity`

Producer-generated PASS labels are not independent verification.

---

## 14. Structural Keyboard

Structural Keyboard is the reference human interaction surface for SERA.

Its role is not to claim that structural navigation or scope-based editing is new.

Its role is to make the SERA contract visible through human interaction.

The relationship is:

`SERA = edit-resolution and admission architecture`

`Structural Keyboard = reference human interaction surface`

`proposal adapters = human, agent, API, and assistive proposal surfaces`

`schema providers = structural interpretation sources`

`host adapters = execution surfaces`

A keyboard surface may expose structural units such as:

- `GRAPHEME`
- `CODE_POINT`
- `WORD`
- `SENTENCE`
- `PARAGRAPH`
- `LIST_ITEM`
- `SECTION`

The same admission architecture can govern machine proposals without requiring the keyboard surface.

---

## 15. Current Reference Boundary

The current SERA v0.9.2 reference implementation demonstrates:

- `proposal authority separation`
- `independent target resolution`
- `canonical planning`
- `preview commitment`
- `No Silent Retarget`
- `dependency-aware admission`
- `Structural Relevance classification`
- `Structural Admission Survival`
- `mutation envelopes`
- `structural edit permits`
- `refusal witnesses`
- `human-readable refusal explanations`
- `deterministic receipts`
- `session bundles`
- `grapheme-aware structural scope`
- `producer-side replay-oriented evidence`

The current browser reference has demonstrated a producer-side release audit of:

`329/329 PASS`

with:

`KNOWN REGRESSIONS = 27/27 PASS`

`FEATURE COVERAGE = 34/34 PASS`

`INTEGRITY REGRESSION = 0`

`UNEXPECTED MUTATION = 0`

Independent verification remains a separate assurance boundary until a separate verifier reconstructs the declared evidence without trusting producer-generated PASS labels.

---

## 16. Forward Direction

The strongest next assurance and deployment directions are:

- `independent replay verifier`
- `frozen adversarial concurrent-edit corpus`
- `dependency-survival measurement`
- `second host adapter`
- `cross-offset adapter conformance`
- `performance and scaling measurement`
- `accessibility qualification`
- `bounded commutativity certification`

For two admitted plans `A` and `B`, a future commutativity profile may evaluate:

`A(B(D)) == B(A(D))`

with outcomes such as:

- `COMMUTES`
- `DOES_NOT_COMMUTE`
- `NOT_PROVEN`

This may support safe parallel proposal processing without making arrival order the sole resolution authority.

---

## 17. Compact SERA Model

The complete architecture can be summarized as:

`proposal authority != target authority != mutation authority`

`proposal -> resolve -> plan -> preview -> revalidate -> admit -> execute OR refuse -> receipt`

`document changed != proposal automatically stale`

`required dependencies unchanged -> authority may survive`

`required dependencies changed -> old authority must not silently survive`

`preview target changed -> old commitment cannot execute`

`write_set(E_c) subseteq admitted_mutation_envelope`

`valid refusal -> zero mutation + explicit state + evidence`

The intended result is:

`safe editing != accept everything`

`safe editing != invalidate everything`

`safe editing = preserve authority exactly while required structure remains valid`
