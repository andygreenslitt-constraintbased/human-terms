# First-Principles Admissibility — Human Terms Technical Score

## 1. Source Identity

SOURCE:
`https://github.com/andygreenslitt-constraintbased/first-principles-admissibility`

Implementation alignment source:
`first_principles_audit.py` (local runtime adapter)

SOURCE TYPE:
GitHub repository / Python audit engine / framework one-page / test file

SOURCE ROLE:
Public structural claim-audit tool for checking whether a claim, model, plan,
AI output, process, or theory has earned movement under declared constraints.

CLAIM STRENGTH:
public framework / local implementation / local tests

READER LEVEL:
general / technical beginner / builder

SOURCE SUPPORT:
VISIBLE

The public repository includes README, one-page framework summary, Python audit
engine, and test file. The README states 42 tests covering five layers, twelve
failure signatures, four directive states, and diagnostic phrases. This is
visible source support for the tool’s stated structure and local behavior, not
external validation of claim truth.

TRANSLATION STATUS:
ANCHOR_HELD

## 2. Whole-Document Human Lyric

First-Principles Admissibility is a claim auditor.

It does not ask:

```text
Does this sound convincing?
```

It asks:

```text
What breaks first, and did the claim admit that break before asking to move?
```

The plain-language idea is:

```text
A claim has not earned movement just because it sounds good, worked once, has a
model, has a label, or has documentation.
```

Before a claim can move, it must show:

- what carries it;
- where it holds;
- what it costs;
- how it transfers;
- how it fails;
- who repairs it;
- what budget preserves it.

This is useful for AI outputs, plans, governance claims, engineering proposals,
institutional processes, theories, and documentation because it blocks false
closure. It keeps a reader from mistaking presentation, utility, policy,
training, or one-off success for structural admissibility.

## 3. Whole-Document Technical Notes

Public repo files reviewed:

- `README.md`
- `FIRST_PRINCIPLES_ADMISSIBILITY_FRAMEWORK_ONE_PAGE.md`
- `first_principles_audit.py`
- `test_first_principles_audit.py`

Core rule:

```text
Possible != Repeatable != Scalable != Transferable != Admissible
```

Five audit layers:

1. False Closure
2. First-Principles Admissibility
3. Upstream Formulation Failure
4. Transfer Integrity
5. Constraint Budget

Directive states:

- `ADVANCE`
- `REPAIR`
- `HOLD`
- `BLOCK`

Twelve master failure signatures:

- False Closure
- Possible-Once -> System-Admissible
- Deleted Carrier / Ghost Gradient
- Transfer Failure
- Hidden Bill
- Static Fantasy
- Representation Reified
- Evidence-State Inflation
- Boundary Smuggling
- Receiver Collapse
- Governance Theater
- Behavior from Formal State

Implementation objects:

- `Directive`
- `FailureSignature`
- `AuditInput`
- layer evaluator functions
- `run_audit`
- `audit_from_dict`
- `AuditReceipt`

## 4. Locked Document Meaning

The locked meaning is:

First-Principles Admissibility audits whether a claim has declared enough
structural support to keep moving. It outputs structural status under stated
constraints, not truth.

This meaning must not be changed into:

- “The tool proves the claim true.”
- “The tool validates the claim.”
- “The tool replaces domain review.”
- “The tool decides real-world action.”
- “The tool certifies safety, legality, policy, medicine, or engineering.”
- “Passing the audit means the claim is correct.”

## 5. What This Does Not Claim

This companion does not claim:

- proof;
- validation;
- correctness;
- production readiness;
- public readiness;
- execution authority;
- expert replacement;
- domain certification;
- that tests prove the framework correct;
- that readability replaces the source.

The source itself says the output is structural admissibility status, not truth.
This companion preserves that boundary.

## 6. Technical Score Blocks

---

### SCORE BLOCK 1: Core Question

SOURCE LOCATION:
`README.md`, opening block; `FIRST_PRINCIPLES_ADMISSIBILITY_FRAMEWORK_ONE_PAGE.md`,
Purpose section

SOURCE TRACE:
The README calls the project a structural claim auditor and states it does not
ask whether a claim sounds right. It asks what breaks first and whether that
break was declared before movement.

ROLE IN THE WHOLE PIECE:
Defines the frame of the tool.

HUMAN LYRIC:
The tool starts by distrusting smoothness. It does not care whether a claim
sounds impressive. It asks where the claim will fail first and whether the claim
admitted that weak point before trying to advance.

TECHNICAL NOTES:
QUOTE:
`What breaks first, and was that break declared before movement?`

FAITHFUL PARAPHRASE:
The source frames the framework as a structural auditor rather than a truth
engine.

INTERPRETATION:
This is a direct anti-fabrication and anti-overclaim posture.

LOCKED MEANING:
The tool audits movement entitlement, not truth.

DEPENDENCIES:
Depends on having a specific object, claim, and domain to audit.

OUTPUT / EFFECT:
Sets the audit posture for the entire repo.

ASSUMPTIONS:
A claim can be inspected by asking where it breaks and whether the break was
declared.

FAILURE RISK:
The phrase “bullshit detector” in the one-page version is readable and punchy,
but in formal settings it should be translated as “structural claim auditor.”

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

TRANSLATION STATUS:
ANCHOR_HELD

---

### SCORE BLOCK 2: Core Rule

SOURCE LOCATION:
`README.md`, Core Rule; `FIRST_PRINCIPLES_ADMISSIBILITY_FRAMEWORK_ONE_PAGE.md`,
Core rule

SOURCE TRACE:
Both files state: Possible does not equal Repeatable, Scalable, Transferable, or
Admissible.

ROLE IN THE WHOLE PIECE:
Provides the central distinction.

HUMAN LYRIC:
Just because something can happen once does not mean it can run as a system,
scale, transfer, or survive over time. A claim must earn each step separately.

TECHNICAL NOTES:
QUOTE:
`Possible != Repeatable != Scalable != Transferable != Admissible`

FAITHFUL PARAPHRASE:
The source says a claim must declare carrier, scope, cost, transfer mechanism,
failure mode, repair responsibility, and preservation budget before it has
earned movement.

INTERPRETATION:
This rule blocks one-off success from being promoted into a broad system claim.

LOCKED MEANING:
Possibility is only one layer. It is not enough for admissibility.

DEPENDENCIES:
Depends on the five-layer audit and failure signatures.

OUTPUT / EFFECT:
Forces claims to separate existence, repetition, scaling, transfer, and
endurance.

ASSUMPTIONS:
The claim is trying to move beyond a narrow bounded instance.

FAILURE RISK:
Readers may treat “possible” as the whole argument. The source explicitly blocks
that.

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

TRANSLATION STATUS:
ANCHOR_HELD

---

### SCORE BLOCK 3: Five-Layer Audit

SOURCE LOCATION:
`README.md`, Five Audit Layers; one-page framework, Five-layer audit

SOURCE TRACE:
The source lists False Closure, First-Principles Admissibility, Upstream
Formulation Failure, Transfer Integrity, and Constraint Budget.

ROLE IN THE WHOLE PIECE:
Defines the inspection route.

HUMAN LYRIC:
The audit checks five ways a claim can be fake-complete:

1. It closes too early.
2. It worked once but cannot survive as a system.
3. It erased the hard part before becoming clean.
4. It transferred a label instead of structure.
5. It hid the bill.

TECHNICAL NOTES:
FAITHFUL PARAPHRASE:
The audit layers ask whether the claim closed early, whether it can exist,
repeat, transfer, and endure, what formulation erased, whether the receiver got
structure or label, and who pays the cost.

INTERPRETATION:
The audit is a route through common overclaim patterns.

LOCKED MEANING:
Claims must pass through layered structural checks before movement.

DEPENDENCIES:
Depends on the object, claim, domain, and declared support fields.

OUTPUT / EFFECT:
Identifies failed layers and routes the claim to ADVANCE, REPAIR, HOLD, or
BLOCK.

ASSUMPTIONS:
The claim can be represented through audit fields.

FAILURE RISK:
If used loosely, the five layers can become rhetoric. They need a specific claim
and source facts.

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

TRANSLATION STATUS:
ANCHOR_HELD

---

### SCORE BLOCK 4: Twelve Master Failure Signatures

SOURCE LOCATION:
`README.md`, Twelve Master Failure Signatures; one-page framework, Twelve master
failure signatures

SOURCE TRACE:
The files list twelve named failure signatures and their core failures.

ROLE IN THE WHOLE PIECE:
Provides diagnostic names for common structural failures.

HUMAN LYRIC:
The signatures are names for the ways claims pretend to be stronger than they
are. They catch things like a model being treated as reality, weak evidence
being promoted to closure, a plan being treated as execution, and a label
surviving after the structure died.

TECHNICAL NOTES:
FAITHFUL PARAPHRASE:
The twelve signatures include false closure, possible-once to
system-admissible, deleted carrier, transfer failure, hidden bill, static
fantasy, representation reified, evidence-state inflation, boundary smuggling,
receiver collapse, governance theater, and behavior from formal state.

INTERPRETATION:
These are reusable claim-audit labels for AI, governance, planning, and process
review.

LOCKED MEANING:
Each failure signature names a specific structural break, not a general insult.

DEPENDENCIES:
Depends on audit inputs and layer evaluators.

OUTPUT / EFFECT:
Gives the audit a language for what failed.

ASSUMPTIONS:
The failure can be traced to one of the defined structural patterns.

FAILURE RISK:
The signatures can become buzzwords if not tied to the actual failed layer.

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

TRANSLATION STATUS:
ANCHOR_HELD

---

### SCORE BLOCK 5: Directive States

SOURCE LOCATION:
`README.md`, Directive States; `first_principles_audit.py`, `Directive` enum

SOURCE TRACE:
The README defines ADVANCE, REPAIR, HOLD, and BLOCK. The Python file implements
the same directive enum.

ROLE IN THE WHOLE PIECE:
Defines the audit output surface.

HUMAN LYRIC:
The audit does not return “true” or “false.” It returns a movement status:
continue, repair, hold because there is not enough information, or block because
the framing is structurally inadmissible.

TECHNICAL NOTES:
QUOTE:
`ADVANCE | REPAIR | HOLD | BLOCK`

FAITHFUL PARAPHRASE:
ADVANCE means structurally allowed to continue under stated constraints. REPAIR
means missing carrier, budget, boundary, transfer path, evidence state, or
correction loop. HOLD means not enough information. BLOCK means structurally
inadmissible under current framing.

INTERPRETATION:
This mirrors the resume language around HOLD/REPAIR/BLOCK routing.

LOCKED MEANING:
Directives are structural movement states, not truth claims.

DEPENDENCIES:
Depends on audit layer results and failure signatures.

OUTPUT / EFFECT:
Produces a reviewable routing status.

ASSUMPTIONS:
The audit input is specific enough to classify.

FAILURE RISK:
ADVANCE can be misread as approval. It only means structurally allowed to
continue under stated constraints.

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

TRANSLATION STATUS:
ANCHOR_HELD

---

### SCORE BLOCK 6: Python Audit Engine

SOURCE LOCATION:
`first_principles_audit.py`, module docstring, enums, `AuditInput`, layer
evaluators, `run_audit`, `audit_from_dict`

SOURCE TRACE:
The Python file implements the framework as an audit engine with dataclasses,
enums, layer evaluators, directive resolution, and dictionary input support.

ROLE IN THE WHOLE PIECE:
Turns the framework into runnable audit behavior.

HUMAN LYRIC:
The code turns the framework into a structured checklist with consequences. You
give it an object, claim, domain, and support fields; it returns what failed and
what movement status is allowed.

TECHNICAL NOTES:
FAITHFUL PARAPHRASE:
The engine defines `AuditInput`, validates numeric ranges, evaluates each audit
layer, collects failure signatures, resolves directives, and exposes dictionary
input support.

INTERPRETATION:
This is practical evidence that the concept has been translated into working
code.

LOCKED MEANING:
The code audits declared structure. It does not verify external truth.

DEPENDENCIES:
Depends on supplied audit fields accurately representing the claim.

OUTPUT / EFFECT:
Produces an audit receipt with directive, failed layers, missing carrier,
hidden bill, binding constraint, dominant signature, all signatures, and layer
detail.

ASSUMPTIONS:
The caller supplies honest inputs.

FAILURE RISK:
If the input fields are wrong or gamed, the receipt can look cleaner than the
claim deserves.

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

TRANSLATION STATUS:
ANCHOR_HELD

---

### SCORE BLOCK 7: Test Coverage

SOURCE LOCATION:
`test_first_principles_audit.py`, header and test functions

SOURCE TRACE:
The test file says it covers clean ADVANCE, each layer in isolation, directive
resolution, dominant signature, dict round-trip, required keys, missing keys,
and float validation.

ROLE IN THE WHOLE PIECE:
Provides local behavioral evidence for the implementation.

HUMAN LYRIC:
The tests check that the audit does what the framework says it should do: clean
inputs advance, missing carriers block, hidden bills repair, weak evidence holds
or repairs, and bad input ranges fail.

TECHNICAL NOTES:
FAITHFUL PARAPHRASE:
The README states 42 tests covering all five layers, all twelve failure
signatures, all four directives, and diagnostic phrases. The test file includes
layer-specific and directive-resolution cases.

INTERPRETATION:
The tests support implementation discipline. They do not prove the framework is
externally correct.

LOCKED MEANING:
Passing tests means tested behaviors passed, not truth or validation.

DEPENDENCIES:
Depends on local test execution and accurate test design.

OUTPUT / EFFECT:
Gives evidence that the implementation has targeted behavioral checks.

ASSUMPTIONS:
The tests run in the intended environment.

FAILURE RISK:
Do not translate “42 tests” into validation. Tests are local evidence of
specified behavior.

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

TRANSLATION STATUS:
ANCHOR_HELD

---

### SCORE BLOCK 8: Claim Boundary

SOURCE LOCATION:
`README.md`, Claim Boundary; one-page framework, Final guardrail

SOURCE TRACE:
The source states the framework outputs structural admissibility status, not
truth claims, and never outputs “This claim is true.”

ROLE IN THE WHOLE PIECE:
Protects the framework from overclaiming.

HUMAN LYRIC:
The strongest safe output is not “true.” The safe output is: under these stated
constraints, this claim is structurally allowed, repairable, held, or blocked.

TECHNICAL NOTES:
QUOTE:
`Never: "This claim is true."`

FAITHFUL PARAPHRASE:
The source says outputs should be framed as structural admissibility,
repairability, hold, or block under stated constraints.

INTERPRETATION:
This boundary is what makes the tool credible for resume and job contexts.

LOCKED MEANING:
The audit produces movement entitlement, not truth certification.

DEPENDENCIES:
Depends on preserving the directive and non-claim boundary.

OUTPUT / EFFECT:
Prevents the audit from being mistaken for proof.

ASSUMPTIONS:
Users will preserve the boundary when quoting or applying the tool.

FAILURE RISK:
If this boundary is removed, the tool becomes an overclaim engine.

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

TRANSLATION STATUS:
ANCHOR_HELD

---

## 7. Source Dependency Map

- README gives the public purpose, core rule, five layers, failure signatures,
  directives, quick start, tests, diagnostic phrases, and claim boundary.
- One-page framework gives the executive explanation and compressed receipt.
- Python file implements the audit engine.
- Test file checks local behavior across layers, directives, signatures, and
  input handling.
- Local runtime adapter aligns the concept with broader runtime receipts, but
  the public repo is the main source for this companion.

Most important dependency:

```text
The audit is only as strong as the declared inputs and preserved claim boundary.
```

## 8. Failure / Drift Map

Risk:

```text
Reader treats structural admissibility as truth.
```

Repair:

```text
Quote the source boundary: never "This claim is true."
```

Risk:

```text
Reader treats ADVANCE as approval.
```

Repair:

```text
State that ADVANCE means structurally allowed to continue under stated
constraints.
```

Risk:

```text
Reader treats passing tests as validation.
```

Repair:

```text
State that tests verify local behavior, not external correctness.
```

Risk:

```text
Reader uses failure signatures as insults.
```

Repair:

```text
Tie each signature to a specific failed layer and source condition.
```

Risk:

```text
Reader audits a vague claim.
```

Repair:

```text
Require object, claim, domain, carrier, support, budget, and failure path.
```

## 9. Human Terms Glossary

| Technical Term | Human-Term Translation | Locked Meaning | Drift Risk |
| --- | --- | --- | --- |
| First-Principles Admissibility | Has the claim earned movement from the ground up? | Movement requires declared carrier, cost, transfer, failure, and repair | Treating it as truth |
| False Closure | Closing before the load-bearing condition is tested | Completeness must be earned | Mistaking fluency for completion |
| Deleted Carrier | Claim has no declared thing carrying it | Output needs substrate or support | Treating output as self-supporting |
| Transfer Failure | Label moved, structure did not | Receiver must inherit constraint state | Treating communication as transfer |
| Hidden Bill | Cost exists but was not declared | Someone/something must pay the load | Hiding burden downstream |
| Static Fantasy | Time, drift, decay, or maintenance ignored | Systems need upkeep | Treating a snapshot as durable |
| Representation Reified | Model treated as reality | Map is not territory | Treating metrics as the system |
| Evidence-State Inflation | Weak support promoted to closure | Evidence strength limits claim strength | Treating utility as proof |
| Boundary Smuggling | Bounded result presented too broadly | Scope must stay declared | Turning local result universal |
| Governance Theater | Artifact treated as control | Policy/checklist is not behavior | Treating documentation as enforcement |
| ADVANCE | Structurally allowed to continue | Not truth; movement under constraints | Treating as approval |
| REPAIR | Missing support must be fixed | Partial path exists but needs work | Treating as proceed |
| HOLD | Not enough to judge | More structure needed | Treating as failure |
| BLOCK | Structurally inadmissible now | Do not move under current framing | Treating as moral condemnation |

## 10. One-Page Reader Version

### What this is

First-Principles Admissibility is a structural claim-audit tool.

### Why it exists

It exists because claims often move too early. They sound complete before they
declare what carries them, what they cost, how they fail, how they transfer, or
who repairs them.

### What problem it addresses

It catches false closure, one-off success promoted into system claims, hidden
costs, missing carriers, transfer failures, weak evidence, and governance
theater.

### What the source actually does

It defines:

- a core rule;
- five audit layers;
- twelve failure signatures;
- four directive states;
- a Python audit engine;
- tests for local behavior;
- a claim boundary that blocks truth overclaiming.

### What it does not claim

It does not prove claims true.

It does not validate claims externally.

It does not replace legal, medical, engineering, safety, policy, or domain
review.

It does not turn passing tests into correctness.

### What to read next

For public readers:

```text
README.md
FIRST_PRINCIPLES_ADMISSIBILITY_FRAMEWORK_ONE_PAGE.md
```

For technical readers:

```text
first_principles_audit.py
test_first_principles_audit.py
```

For resume readers:

```text
This repo supports claim-audit, structured output review, and
HOLD/REPAIR/BLOCK-style routing credibility.
```

## 11. Final Audit

TRANSLATION STATUS:
ANCHOR_HELD

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

SOURCE VISIBILITY:
The companion uses file-level and section-level traces from the public GitHub
repo, plus implementation alignment from the local runtime adapter.

MISSING CONTEXT:
No missing context is needed to understand the public repo’s stated purpose.
External validation would require separate evidence beyond the repo and tests.

REPAIR NEEDED:
No repair is needed for this companion. Repair would be needed if the audit were
described as truth validation, production readiness, domain authority, expert
replacement, or proof of correctness.

## 12. Current Verdict

```text
ACCEPT_HUMAN_TERMS_COMPANION
SOURCE_STATUS_PUBLIC_FRAMEWORK_WITH_LOCAL_TESTS
READY_FOR_RESUME_EVIDENCE_SUPPORT
HOLD_PROOF_VALIDATION_READINESS_CLAIMS
```

