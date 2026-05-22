# TECHNICAL_SCORE_TRANSLATOR_OUTPUT_DIRECTIVE.md

## 1. Purpose

Version: v0.2

Use this directive to create a human-readable companion document for a complex
PDF, code file, specification, framework, research note, or technical system.

The companion document should work like a music sheet:

```text
Human Lyric      = readable explanation
Technical Notes  = source structure underneath
Locked Meaning   = invariant meaning that must survive translation
Audit Layer      = dependencies, assumptions, failure risks, confidence, status
```

The goal is not to simplify the source until it becomes vague.

The goal is to make the source readable while keeping the original meaning,
structure, dependencies, limits, and failure risks visible.

## 2. Non-Claims

The translated companion does not claim:

```text
proof
validation
correctness
production readiness
public readiness
execution authority
expert replacement
domain certification
that analogy proves the source
that readability replaces the source
```

Readable does not mean proven.

Clear does not mean complete.

Useful does not mean validated.

## 3. Core Rule

```text
Readable language may explain the source.
Readable language may not replace, distort, erase, or overclaim the source.
```

If the plain-language explanation changes the source meaning, flag:

```text
DRIFT_RISK
```

If the source cannot be safely translated from the available context, flag:

```text
NEEDS_CONTEXT
```

If no safe human-language mapping exists yet, flag:

```text
MISSING_MAPPING
```

## Source Trace Rule

Every Technical Score Block must remain traceable to the source.

For PDFs, identify page number, section, heading, figure, table, equation,
paragraph, citation, or other available location.

For Python files, identify file name, class, function, method, constant, code
region, import, object, or line range when available.

For framework documents, identify section, primitive, operator, state variable,
status block, claim, definition, or rule.

If the source location is unclear or unavailable, mark:

```text
NEEDS_CONTEXT
```

Do not create a Human Lyric that cannot be traced back to Technical Notes.

## 4. Output Directive

When asked to translate a complex source into human terms, produce this output:

```text
# [Source Title] — Human Terms Technical Score

## 1. Source Identity

SOURCE:
[file name, PDF title, repo link, section, code file, or artifact name]

SOURCE TYPE:
[PDF / Python file / specification / framework / research note / codebase / other]

SOURCE ROLE:
[what this source does in the larger body of work]

CLAIM STRENGTH:
[conceptual / exploratory / formal / implementation / reference / instructional / empirical / unknown]

READER LEVEL:
[general / technical beginner / technical practitioner / domain expert / executive / builder]

SOURCE SUPPORT:
[VISIBLE / PARTIAL / WEAK / NOT_ASSESSED]

TRANSLATION STATUS:
[ANCHOR_HELD / NEEDS_CONTEXT / MISSING_MAPPING / DRIFT_RISK / UNSUPPORTED / REPAIR_NEEDED]

## 2. Whole-Document Human Lyric

[Plain-language explanation of what the source is really about.]

Write this as if explaining it to a capable person who does not know the
technical vocabulary yet.

Do not make it childish.

Do not erase the technical structure.

## 3. Whole-Document Technical Notes

[Faithful structural summary of the source.]

Include the major:

- sections
- definitions
- equations
- classes/functions
- claims
- tables/figures
- dependencies
- output objects
- status boundaries

## 4. Locked Document Meaning

[The invariant meaning that must survive any plain-language translation.]

This is the part that cannot change even if the explanation changes style.

## 5. What This Does Not Claim

[Explicit non-claims from the source or required by context.]

Include uncertainty, missing evidence, limits, and authority boundaries.

## 6. Technical Score Blocks

Repeat this block for each major section, function, claim, equation, table,
figure, or concept.

---

### SCORE BLOCK [number]: [source location / section / object]

SOURCE LOCATION:
[page / section / heading / function / class / equation / table / paragraph]

SOURCE TRACE:
[exact source location, line range, page, section, heading, function, class,
equation, table, figure, or code region]

ROLE IN THE WHOLE PIECE:
[what this block does inside the source]

HUMAN LYRIC:
[plain-language meaning]

TECHNICAL NOTES:
[exact quote, faithful paraphrase, code behavior, equation, definition, table,
or structural source]

LOCKED MEANING:
[meaning that must not change]

DEPENDENCIES:
[what this block relies on]

OUTPUT / EFFECT:
[what this block produces, blocks, computes, explains, routes, authorizes, or
does not authorize]

ASSUMPTIONS:
[what must be true for this block to hold]

FAILURE RISK:
[how this block could be misunderstood, overclaimed, mistranslated, skipped, or
misused]

TRANSLATION CONFIDENCE:
[HIGH / MEDIUM / LOW]

SOURCE SUPPORT:
[VISIBLE / PARTIAL / WEAK / NOT_ASSESSED]

TRANSLATION STATUS:
[ANCHOR_HELD / NEEDS_CONTEXT / MISSING_MAPPING / DRIFT_RISK / UNSUPPORTED /
REPAIR_NEEDED]

---

## 7. Source Dependency Map

[Show how the major pieces rely on one another.]

Use plain language.

Example:

- Section 2 defines the object.
- Section 3 defines the constraint.
- Section 4 depends on Section 3.
- Section 5 should not be read as independent proof.

## 8. Failure / Drift Map

List the biggest ways a reader could misunderstand the source:

- [risk 1]
- [risk 2]
- [risk 3]

For each risk, state the repair:

- [repair 1]
- [repair 2]
- [repair 3]

## 9. Human Terms Glossary

Translate technical terms into readable terms without changing meaning.

| Technical Term | Human-Term Translation | Locked Meaning | Drift Risk |
| --- | --- | --- | --- |
| [term] | [plain language] | [invariant meaning] | [risk] |

## 10. One-Page Reader Version

Write a compressed version for a nontechnical reader:

- What this is:
- Why it exists:
- What problem it addresses:
- What the source actually does:
- What it does not claim:
- What to read next:

## 11. Final Audit

TRANSLATION STATUS:
[ANCHOR_HELD / NEEDS_CONTEXT / MISSING_MAPPING / DRIFT_RISK / UNSUPPORTED /
REPAIR_NEEDED]

TRANSLATION CONFIDENCE:
[HIGH / MEDIUM / LOW]

SOURCE SUPPORT:
[VISIBLE / PARTIAL / WEAK / NOT_ASSESSED]

SOURCE VISIBILITY:
[what source material remains traceable]

MISSING CONTEXT:
[anything needed before stronger translation]

REPAIR NEEDED:
[specific repair, if any]
```

## 5. Short Output Directive

Use this when the instruction budget is small:

```text
Translate the source into a Technical Score companion.

Use four layers:
1. Human Lyric — plain-language meaning.
2. Technical Notes — source structure, quote, equation, code behavior, or
   faithful technical summary.
3. Locked Meaning — invariant meaning that must not change.
4. Audit Layer — dependencies, assumptions, failure risks, confidence, and
   translation status.

Include Source Trace, Reader Level, and Source Support. Keep exact quote,
faithful paraphrase, and interpretation separate.

Do not claim proof, validation, correctness, production readiness, public
readiness, execution authority, or expert replacement.

If the source is unclear, mark NEEDS_CONTEXT.
If no safe mapping exists, mark MISSING_MAPPING.
If the readable explanation may change the source meaning, mark DRIFT_RISK.

Readable language may explain the source.
Readable language may not replace, distort, erase, or overclaim the source.
```

## 6. Status Values

Use only:

```text
ANCHOR_HELD
NEEDS_CONTEXT
MISSING_MAPPING
DRIFT_RISK
UNSUPPORTED
REPAIR_NEEDED
```

Definitions:

```text
ANCHOR_HELD:
The human lyric preserves the technical notes and locked meaning.

NEEDS_CONTEXT:
The source cannot be translated safely without more surrounding material.

MISSING_MAPPING:
A technical object, term, equation, claim, function, or concept has no safe
human-language mapping yet.

DRIFT_RISK:
The readable explanation may be changing, weakening, overstating, or replacing
the source meaning.

UNSUPPORTED:
The source makes a claim without enough visible support in the available
material.

REPAIR_NEEDED:
The translation, source interpretation, or source structure needs correction
before it can be trusted.
```

## 7. Confidence Values

Use only:

```text
HIGH
MEDIUM
LOW
```

Definitions:

```text
HIGH:
The source is clear, the technical notes are visible, and the human lyric
preserves the locked meaning.

MEDIUM:
The source is mostly clear, but some dependency, context, or interpretation risk
remains.

LOW:
The source is ambiguous, incomplete, image-based, underspecified, highly
technical, or dependent on missing context.
```

## 7A. Source Support Values

Use only:

```text
VISIBLE
PARTIAL
WEAK
NOT_ASSESSED
```

Definitions:

```text
VISIBLE:
The source material needed to support the translation is present and traceable.

PARTIAL:
Some source support is visible, but dependencies, context, evidence, or
surrounding material are incomplete.

WEAK:
The source claim or source structure is visible, but support is thin,
unsupported, circular, speculative, or not enough to carry stronger claims.

NOT_ASSESSED:
The translation has not evaluated whether the source itself is supported. Only
readability or structure has been translated.
```

## Quote / Paraphrase / Interpretation Rule

When translating source material, distinguish exact source text, faithful
paraphrase, and interpretation.

Use:

```text
QUOTE:
Exact source language. Keep quotes short and source-located.

FAITHFUL PARAPHRASE:
Restates the source meaning without claiming to be exact wording.

INTERPRETATION:
Adds explanatory framing, implications, or reader-facing meaning beyond the
literal source wording.
```

Rules:

- Do not present interpretation as source text.
- Do not present paraphrase as exact quote.
- Do not present source claims as validated facts unless validation is actually
  present.
- If the output depends on interpretation, preserve that boundary in the Audit
  Layer.
- If the quote, paraphrase, or interpretation cannot be traced back to the
  source, mark NEEDS_CONTEXT.

## 8. Rules For PDFs

For PDFs, preserve:

```text
title
document role
claim strength
section structure
definitions
equations
figures
tables
citations or references when present
non-claims
dependencies between sections
```

Do not turn a polished PDF into proof.

Do not treat formal notation as empirical evidence.

Do not treat analogy as validation.

## 9. Rules For Python Files

For Python files, preserve:

```text
file role
imports
local dependencies
classes
functions
constants
input objects
output objects
side effects
control flow
failure modes
runtime assumptions
```

Do not describe code as secure, correct, or production-ready unless the source
explicitly supports that claim and the audit layer preserves the limitation.

## 10. Rules For Framework Documents

For frameworks, preserve:

```text
core object
state variables
operator list
stage sequence
receipt or evidence model
authority boundary
claim strength
non-claims
open obligations
failure modes
```

Do not let the translation become a pitch deck.

The companion should help the reader understand the work, not inflate it.

## 11. Folder Use

Recommended folder shape:

```text
Human_Terms/
  00_READ_ME_FIRST.md
  Technical_Score_Translator_Output_Directive.md
  Glossary_Human_Terms.md
  By_Document/
    [Source_Name]_Human_Terms.md
```

Each companion should point back to the source:

```text
SOURCE:
[path or GitHub URL]
```

## 12. Current Verdict

```text
ACCEPT_TECHNICAL_SCORE_TRANSLATOR_OUTPUT_DIRECTIVE_V0_2
READY_FOR_FIRST_TEST_COMPANION
HOLD_PROOF_VALIDATION_READINESS_CLAIMS
PRESERVE_SOURCE_TRACE_AND_TRANSLATION_BOUNDARIES
```

TECHNICAL_SCORE_TRANSLATOR_OUTPUT_DIRECTIVE_COMPLETE
