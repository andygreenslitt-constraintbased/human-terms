# Conversation Corral — Human Terms Technical Score

## 1. Source Identity

SOURCE:
`corral_runtime.py` (local runtime component)

Supporting test source:
`test_conversation_corral.py` (local test file)

SOURCE TYPE:
Python file / runtime support module / local test file

SOURCE ROLE:
Conversation Corral is a local runtime component for multi-turn interpretation
narrowing. It holds ambiguous user intent in a structured state until the object
is stable enough to proceed or until fabrication risk requires blocking.

CLAIM STRENGTH:
local implementation / tested runtime behavior / structured output support

READER LEVEL:
technical beginner / builder

SOURCE SUPPORT:
VISIBLE

The source file and test file are visible locally. The tests verify corral entry,
corral narrowing, social-input bypass, premature-commitment prevention, explicit
confirmation unlock, fabrication block behavior, and compatibility with the
existing assumption-box flow. This is local test support, not external
validation.

TRANSLATION STATUS:
ANCHOR_HELD

## 2. Whole-Document Human Lyric

Conversation Corral is a safety layer for ambiguous conversation.

Its job is simple:

```text
Do not execute a request until the system knows what the user actually means.
```

When a user says something incomplete like:

```text
the demo for the case study
```

the runtime should not invent the missing command. It should hold the request in
a narrowing state, track what is still unresolved, and ask for the smallest
clarification needed.

The Corral turns ambiguity into an inspectable state:

- current best reading;
- candidate intents;
- unresolved anchors;
- drift flags;
- commitment readiness;
- whether proceed is allowed;
- whether fabrication risk must block movement.

In human terms:

```text
The Corral keeps the conversation from becoming a fake task.
```

## 3. Whole-Document Technical Notes

Primary file:

```text
corral_runtime.py
```

Main objects and functions:

- `ConversationCorralState`
- `corral_state_from_dict`
- `_derive_corral_center`
- `_suggest_next_move`
- `_build_rationale`
- `init_corral_from_gary`
- `update_corral_state`
- `should_hold_in_corral`
- `should_shrink_corral`
- `should_proceed_from_corral`
- `should_block_for_fabrication`
- `build_corral_context_block`

Important thresholds:

- `CORRAL_PROCEED_THRESHOLD = 0.65`
- `CORRAL_ANCHOR_CLEAR_COUNT = 0`
- `FABRICATION_BLOCK_ANCHOR_MIN = 2`
- `CORRAL_STALL_TURNS = 3`
- `CORRAL_IC_TRIGGER_THRESHOLD = 0.55`

Test scenarios in `test_conversation_corral.py`:

- incomplete fragment enters corral;
- productive narrowing improves readiness or narrows width;
- social/motivational content does not enter corral;
- premature commitment is blocked without confirmation;
- explicit confirmation unlocks proceed;
- fabrication block trips when object is unstable with multiple missing anchors;
- existing assumption-box flow remains intact.

## 4. Locked Document Meaning

The locked meaning is:

Conversation Corral prevents premature task execution by holding ambiguous user
intent in a structured state until the object, target, operation, or other
anchors are stable enough to proceed.

This meaning must not be changed into:

- “The Corral decides what the user means automatically.”
- “The Corral validates intent.”
- “The Corral proves the answer is correct.”
- “The Corral replaces human clarification.”
- “The Corral makes ambiguous input safe to execute without repair.”

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
- that tests prove the runtime correct;
- that readability replaces the source.

The source is a local runtime component with local tests. The companion preserves
that boundary.

## 6. Technical Score Blocks

---

### SCORE BLOCK 1: Doctrine Header

SOURCE LOCATION:
`corral_runtime.py`, module docstring, lines 1–16

SOURCE TRACE:
The module docstring names Conversation Corral, states the doctrine, and says
control logic lives here while user-facing language lives elsewhere.

ROLE IN THE WHOLE PIECE:
Sets the purpose and boundary of the file.

HUMAN LYRIC:
The file begins by saying: narrow the interpretation before committing. Do not
execute a task before the object is stable.

TECHNICAL NOTES:
QUOTE:
`Confine the interpretation state space first, THEN commit.`

FAITHFUL PARAPHRASE:
The docstring says the corral holds a live interpretation with explicit width,
narrows it across turns, and commits only when width collapses into a
proceed-eligible band.

INTERPRETATION:
This is the anti-fabrication principle in conversation form.

LOCKED MEANING:
No task execution before object stability.

DEPENDENCIES:
Depends on Gary surfacing interpretation signals and the downstream runtime
respecting the corral state.

OUTPUT / EFFECT:
Defines the control boundary for ambiguity handling.

ASSUMPTIONS:
Ambiguous input can be represented as a narrowing state rather than forced into
immediate execution.

FAILURE RISK:
If this is described as “asking follow-up questions,” the deeper behavior is
lost. It is not just a question prompt; it is a state machine for commitment
control.

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

TRANSLATION STATUS:
ANCHOR_HELD

---

### SCORE BLOCK 2: Threshold Constants

SOURCE LOCATION:
`corral_runtime.py`, threshold constants, lines 24–42

SOURCE TRACE:
The file defines proceed threshold, anchor clear count, fabrication block anchor
minimum, stall turns, and IC trigger threshold.

ROLE IN THE WHOLE PIECE:
Makes the commitment rules explicit and tuneable.

HUMAN LYRIC:
The Corral does not rely on vibes. It has named thresholds for when readiness is
high enough, when anchors are clear enough, when fabrication risk should block,
and when a conversation has stalled.

TECHNICAL NOTES:
FAITHFUL PARAPHRASE:
The file sets `CORRAL_PROCEED_THRESHOLD` to 0.65, fabrication block minimum to 2
unresolved anchors, stall turns to 3, and IC trigger threshold to 0.55.

INTERPRETATION:
The exact numbers are local runtime settings, not universal values.

LOCKED MEANING:
Commitment thresholds are explicit, inspectable, and adjustable.

DEPENDENCIES:
Depends on the meaning of IC ratio, anchors, object stability, and readiness.

OUTPUT / EFFECT:
Controls proceed, hold, block, and stall behavior.

ASSUMPTIONS:
The local runtime can produce signals these thresholds can act on.

FAILURE RISK:
Do not describe these thresholds as calibrated empirical measures. They are
local control settings.

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

TRANSLATION STATUS:
ANCHOR_HELD

---

### SCORE BLOCK 3: ConversationCorralState

SOURCE LOCATION:
`corral_runtime.py`, `ConversationCorralState`, lines 49–78

SOURCE TRACE:
The dataclass defines the serialized corral state, including trace, center,
width, intents, unresolved anchors, drift flags, pressures, readiness, next
move, proceed eligibility, and fabrication risk.

ROLE IN THE WHOLE PIECE:
Provides the central state object.

HUMAN LYRIC:
This state object is the corral’s memory. It records what the system thinks the
user might mean, how wide the ambiguity still is, what is unresolved, and whether
the request is ready to proceed or must stay held.

TECHNICAL NOTES:
FAITHFUL PARAPHRASE:
The dataclass stores fields including `trace_id`, `active`, `corral_center`,
`corral_width`, `candidate_intents`, `unresolved_anchors`, `drift_flags`,
`commitment_readiness`, `suggested_next_move`, `proceed_eligible`, and
`block_fabrication_risk`.

INTERPRETATION:
This is a schema-like receipt for ambiguity, not an answer.

LOCKED MEANING:
Ambiguity is represented as state, not hidden inside fluent language.

DEPENDENCIES:
Depends on Gary’s clarity and interpretation payload.

OUTPUT / EFFECT:
Creates a serializable object that can be carried across turns.

ASSUMPTIONS:
The runtime can preserve this state between conversation turns.

FAILURE RISK:
If the state is ignored downstream, the runtime can still fabricate by jumping
past unresolved anchors.

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

TRANSLATION STATUS:
ANCHOR_HELD

---

### SCORE BLOCK 4: Deriving the Corral Center and Next Move

SOURCE LOCATION:
`corral_runtime.py`, `_derive_corral_center`, `_suggest_next_move`,
`_build_rationale`, lines 92–157

SOURCE TRACE:
These helper functions strip internal prefixes, identify the compact best
reading, choose a next move from missing anchors, and build rationale strings.

ROLE IN THE WHOLE PIECE:
Turns Gary’s raw interpretation signals into a readable narrowing target.

HUMAN LYRIC:
The Corral tries to name the current best reading of the user’s request and then
names the smallest missing piece: object, target, scope, operation, deadline,
audience, or intent.

TECHNICAL NOTES:
FAITHFUL PARAPHRASE:
The helpers derive `corral_center`, map missing anchors to clarification moves,
and build rationale from low IC ratio, missing anchors, or unstable object
state.

INTERPRETATION:
The Corral does not ask for random “more context.” It tries to ask for the
missing structural anchor.

LOCKED MEANING:
Clarification is targeted to the structural gap.

DEPENDENCIES:
Depends on Gary emitting missing anchors and clarity fields.

OUTPUT / EFFECT:
Produces a compact best reading, suggested next move, and rationale.

ASSUMPTIONS:
Missing anchors are meaningful enough to guide the next move.

FAILURE RISK:
If anchor labels are wrong upstream, the follow-up may narrow the wrong thing.

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

TRANSLATION STATUS:
ANCHOR_HELD

---

### SCORE BLOCK 5: Initializing the Corral From Gary

SOURCE LOCATION:
`corral_runtime.py`, `init_corral_from_gary`, lines 164–238

SOURCE TRACE:
The function builds initial corral state from Gary’s payload when Gary routes to
`conversation_corral`.

ROLE IN THE WHOLE PIECE:
Creates the first active corral state from a low-clarity interpretation.

HUMAN LYRIC:
When Gary cannot safely interpret the request, the Corral creates a structured
holding area. It calculates how open the ambiguity still is, how ready the
conversation is for commitment, and whether proceeding would fabricate missing
structure.

TECHNICAL NOTES:
FAITHFUL PARAPHRASE:
The function reads clarity, missing anchors, IC ratio, object stability, binding
act, interpreted request, candidate objectives, and raw input. It computes
`corral_width`, `commitment_readiness`, `block_fabrication`, and
`proceed_eligible`.

INTERPRETATION:
This is the entry point from interpretation uncertainty into controlled
narrowing.

LOCKED MEANING:
Low clarity becomes an explicit hold/repair state instead of hidden guesswork.

DEPENDENCIES:
Depends on Gary payload shape and IC governor output.

OUTPUT / EFFECT:
Returns a `ConversationCorralState`.

ASSUMPTIONS:
Gary’s payload contains enough structure to initialize the state.

FAILURE RISK:
Do not describe `commitment_readiness` as truth confidence. It is local readiness
to proceed, not correctness.

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

TRANSLATION STATUS:
ANCHOR_HELD

---

### SCORE BLOCK 6: Updating Across Turns

SOURCE LOCATION:
`corral_runtime.py`, `update_corral_state`, lines 251–289

SOURCE TRACE:
The function rebuilds state from Gary’s latest receipt, increments turn count,
checks explicit confirmation, and detects stall.

ROLE IN THE WHOLE PIECE:
Lets the Corral narrow over multiple conversation turns.

HUMAN LYRIC:
The Corral is not one question and done. It carries the state forward, watches
whether the ambiguity is shrinking, and only unlocks proceed when confirmation
or readiness is strong enough.

TECHNICAL NOTES:
FAITHFUL PARAPHRASE:
The function carries forward turn count and escape history, raises readiness on
explicit user confirmation, sets `proceed_eligible`, and adds `corral_stall`
when narrowing has stalled.

INTERPRETATION:
This turns conversation into an incremental narrowing process.

LOCKED MEANING:
User confirmation can unlock proceed, but unresolved ambiguity can still hold or
stall.

DEPENDENCIES:
Depends on prior corral state and a fresh Gary payload.

OUTPUT / EFFECT:
Returns an updated `ConversationCorralState`.

ASSUMPTIONS:
The new turn is related to the prior corral context.

FAILURE RISK:
Confirmation words can be risky if the center is wrong. The runtime must ensure
the confirmed center is actually the object being committed.

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

TRANSLATION STATUS:
ANCHOR_HELD

---

### SCORE BLOCK 7: Decision Methods

SOURCE LOCATION:
`corral_runtime.py`, `should_hold_in_corral`, `should_shrink_corral`,
`should_proceed_from_corral`, `should_block_for_fabrication`, lines 294–327

SOURCE TRACE:
These functions return whether the state should hold, shrink, proceed, or block
for fabrication risk.

ROLE IN THE WHOLE PIECE:
Turns state fields into routing decisions.

HUMAN LYRIC:
The Corral has four basic routing questions:

- should we keep holding?
- is the ambiguity narrowing?
- can we proceed?
- would proceeding require fabrication?

TECHNICAL NOTES:
FAITHFUL PARAPHRASE:
Hold requires active state without proceed eligibility or fabrication block.
Proceed is allowed when `proceed_eligible` or confirmed center is present.
Fabrication block requires fabrication risk, enough unresolved anchors, and no
proceed eligibility.

INTERPRETATION:
These methods are the runtime’s anti-premature-commitment switches.

LOCKED MEANING:
Proceed is not allowed just because the user wants motion.

DEPENDENCIES:
Depends on corral state fields being accurate.

OUTPUT / EFFECT:
Returns boolean routing decisions.

ASSUMPTIONS:
Downstream pipeline honors these booleans.

FAILURE RISK:
If downstream code overrides these decisions, the Corral becomes advisory rather
than controlling.

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

TRANSLATION STATUS:
ANCHOR_HELD

---

### SCORE BLOCK 8: Context Block Builder

SOURCE LOCATION:
`corral_runtime.py`, `build_corral_context_block`, lines 333–351

SOURCE TRACE:
The function builds a compact text block for Mothership’s system prompt,
including current best reading, unresolved anchors, plausible directions,
commitment readiness, suggested next move, turns narrowing, and stall note.

ROLE IN THE WHOLE PIECE:
Translates corral state into a concise context block for user-facing handling.

HUMAN LYRIC:
The runtime needs to explain the current ambiguity in normal terms. This helper
turns the structured state into a readable note for the response layer.

TECHNICAL NOTES:
FAITHFUL PARAPHRASE:
The function emits lines for current best reading, unresolved items, plausible
directions, readiness percentage, suggested next move, turn count, and stall
warning.

INTERPRETATION:
This is the bridge from state object to user-facing clarification.

LOCKED MEANING:
The response should expose the narrowing state without pretending the task is
ready.

DEPENDENCIES:
Depends on Mothership using the context block appropriately.

OUTPUT / EFFECT:
Returns a compact string for prompt context.

ASSUMPTIONS:
Natural-language context will help Mothership avoid fabrication.

FAILURE RISK:
If the text block is treated as optional decoration, the state discipline can be
lost.

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

TRANSLATION STATUS:
ANCHOR_HELD

---

### SCORE BLOCK 9: Local Test Coverage

SOURCE LOCATION:
`test_conversation_corral.py`, scenario list and test functions

SOURCE TRACE:
The test file lists scenarios A–G and implements tests for fragment handling,
narrowing, social content, premature commitment, confirmation, fabrication
blocking, and assumption-box compatibility.

ROLE IN THE WHOLE PIECE:
Provides local behavioral evidence that the Corral logic is testable.

HUMAN LYRIC:
The tests check the behavior that matters: vague inputs should not execute,
clarifying turns should narrow the state, social content should not be forced
into a task, and unsafe ambiguity should block fabrication.

TECHNICAL NOTES:
FAITHFUL PARAPHRASE:
The tests use fake or local runtime inputs and do not make API calls. They
verify state machine behavior, routing decisions, and pipeline plumbing.

INTERPRETATION:
These tests support the resume claim that the local runtime has structured
output discipline and fabrication-risk blocking. They do not prove the runtime
is correct in all cases.

LOCKED MEANING:
Local tests verify targeted behavior, not universal correctness.

DEPENDENCIES:
Depends on local `GaryRuntime`, pipeline behavior, and corral functions.

OUTPUT / EFFECT:
Provides local evidence for the Corral’s state-machine behavior.

ASSUMPTIONS:
The tests are run in the local runtime environment.

FAILURE RISK:
Do not translate passing tests as validation. They are evidence of tested
behavior only.

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

TRANSLATION STATUS:
ANCHOR_HELD

---

## 7. Source Dependency Map

- Gary produces interpretation, clarity, IC, missing-anchor, and object-stability
  signals.
- `init_corral_from_gary` converts Gary’s uncertain interpretation into a
  `ConversationCorralState`.
- `update_corral_state` carries the state across turns.
- Decision methods determine whether to hold, shrink, proceed, or block for
  fabrication risk.
- `build_corral_context_block` passes a readable state summary to the
  user-facing layer.
- Tests verify the most important routing behaviors locally.

Most important dependency:

```text
The Corral only works if downstream stages respect its hold/proceed/block state.
```

## 8. Failure / Drift Map

Risk:

```text
Reader thinks the Corral is only a follow-up-question helper.
```

Repair:

```text
Explain it as a state machine for commitment readiness and fabrication-risk
control.
```

Risk:

```text
Reader treats commitment_readiness as truth confidence.
```

Repair:

```text
State that it is readiness to proceed in the local runtime, not correctness.
```

Risk:

```text
Reader treats tests as validation.
```

Repair:

```text
State that tests verify targeted local behavior only.
```

Risk:

```text
Reader thinks the Corral decides user intent automatically.
```

Repair:

```text
State that it narrows and holds; it does not replace clarification.
```

Risk:

```text
Method exposure gives away product leverage.
```

Repair:

```text
Describe capability, state fields, and test coverage without publishing a
standalone implementation recipe.
```

## 9. Human Terms Glossary

| Technical Term | Human-Term Translation | Locked Meaning | Drift Risk |
| --- | --- | --- | --- |
| Conversation Corral | Ambiguity holding and narrowing layer | Do not execute until the object is stable | Treating it as ordinary follow-up |
| Corral Center | Current best reading | The compact likely meaning of the user input | Treating it as confirmed intent |
| Corral Width | Remaining ambiguity | Wider means less ready to commit | Treating it as calibrated measurement |
| Candidate Intents | Possible user meanings | More than one route may still be live | Picking one too early |
| Unresolved Anchors | Missing structural pieces | Object/target/scope/action gaps must be resolved | Ignoring missing pieces |
| Drift Flags | Signs interpretation is escaping the source | The request may be inflating or losing object | Treating drift as creativity |
| Commitment Readiness | Local proceed-readiness | Whether the runtime may commit to execution | Treating it as truth confidence |
| Proceed Eligible | Runtime may continue | Enough support exists for movement | Letting user pressure override it |
| Fabrication Block | Stop because proceeding would invent structure | Missing anchors make execution unsafe | Softening a block into a guess |
| Corral Stall | Narrowing has stopped | Reset or concrete direction may be needed | Repeating questions forever |

## 10. One-Page Reader Version

### What this is

Conversation Corral is a local runtime layer for handling ambiguous user input.

### Why it exists

It exists because AI systems often fabricate when they are forced to answer
before the object, target, scope, or action is clear.

### What problem it addresses

It prevents premature commitment. Instead of guessing what the user meant, it
holds the request in a structured state and narrows it across turns.

### What the source actually does

It defines a serializable corral state with fields for:

- best current reading;
- ambiguity width;
- candidate intents;
- unresolved anchors;
- drift flags;
- readiness;
- suggested next move;
- proceed eligibility;
- fabrication risk.

It also defines functions that initialize the state, update it, decide whether
to hold/proceed/block, and build a readable context block for the response layer.

### What it does not claim

It does not prove user intent.

It does not validate answers.

It does not replace clarification.

It does not make ambiguous input safe to execute without repair.

### What to read next

For implementation evidence:

```text
corral_runtime.py
test_conversation_corral.py
```

For resume evidence:

```text
This supports structured-output reliability, ambiguity control, and
fabrication-risk blocking.
```

## 11. Final Audit

TRANSLATION STATUS:
ANCHOR_HELD

TRANSLATION CONFIDENCE:
HIGH

SOURCE SUPPORT:
VISIBLE

SOURCE VISIBILITY:
The companion uses file-level, function-level, and test-scenario traces from the
local runtime source.

MISSING CONTEXT:
Public GitHub evidence may be needed if this claim is used outside a resume or
private portfolio context. The method should remain private if it is job/product
leverage.

REPAIR NEEDED:
No repair is needed for this companion. Repair would be needed if local tests
were described as external validation or if the private method sequence were
published before intended.

## 12. Current Verdict

```text
ACCEPT_HUMAN_TERMS_COMPANION
SOURCE_STATUS_LOCAL_TESTED_RUNTIME_COMPONENT
READY_FOR_RESUME_EVIDENCE_SUPPORT
PRIVATE_METHOD_DETAILS_HELD
HOLD_PROOF_VALIDATION_READINESS_CLAIMS
```

