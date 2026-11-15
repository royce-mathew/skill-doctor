# Prompt audit

Audit skill descriptions, bodies, references, and the instruction surfaces included by the user or host. The purpose is correct behavior for the intended tasks and models. Shorter text is useful only when it preserves that behavior.

## Establish the instruction contract

For each surface, identify who reads it, when it loads, what task it governs, and which model or models consume it if known. Distinguish a routing description, an always-loaded constraint, a scoped rule, an example, and a task procedure before judging similar wording.

Use current files, documented contracts, relevant history, and existing behavioral evaluations to explain why a rule exists. Inspect relevant version history when available and permitted; a recent edit is not automatically more authoritative than an older rule. Missing history is uncertainty, not permission to delete.

For a model-specific claim, use documentation for the target model or an observed before/after probe. If the target is unknown or several hosts use different models, keep the claim conditional. Do not assume that a newer model plans, reasons, formats, or selects tools well enough to make an instruction redundant.

## Patterns to investigate

| Pattern | Evidence that warrants a finding | Smallest useful response |
|---|---|---|
| Stale facts or broken references | A named local path, command, flag, or dependency disagrees with the current source or documented contract | Repair the fact and its affected references; show the conflicting source |
| Contradictory instructions | Two applicable passages require incompatible actions for the same task, and scope or explicit precedence does not resolve them | Quote both, identify the governing contract, and repair the subordinate text; flag unresolved authority |
| Description/body mismatch | The trigger or promised result differs from the actual procedure, side effects, or deliverable | Align the description and body with the intended task without hiding side effects |
| Duplicate instructions | Copies disagree, drift, or make the wrong version govern a task; or equivalent coverage after a proposed move is established | Choose one source of truth and update callers while preserving loading scope |
| Pressure and hedging | Emphasis or optional language changes a requirement's meaning, or a behavioral probe demonstrates over-triggering or under-delivery | State the intended behavior and reason plainly; retain deliberate routing emphasis and real prohibitions |
| Over-prescribed judgment | A rigid sequence, forced tool, or output cadence demonstrably prevents the task's required outcome | Replace the unnecessary method with its outcome and verification; keep fragile procedures exact |
| Model-era workaround | Provenance and target-model evidence show the original failure is obsolete or the workaround causes a current failure | Propose a small replacement or removal with a before/after probe |
| Misplaced reference material | Always-read text duplicates discoverable detail without adding rationale, or a task-specific section burdens unrelated tasks | Propose a scoped reference only after checking every affected reader retains needed context |
| Missing contract detail | A reader cannot determine a required input, side effect, failure condition, or success criterion from the skill and its available dependencies | Add the missing contract; do not invent domain facts or prescribe unnecessary implementation details |

Typography, length, a fixed number of steps, or words such as `MUST`, `NEVER`, and `think step by step` are signals for inspection, not automatic findings. Use of a familiar pattern alone supports at most a low-confidence flag. Unsupported universal claims can be flagged without claiming their opposite is true.

A scoped exception is not a contradiction. For example, an importer-specific test procedure need not be copied into a global rule that gives the general test command. Likewise, two skills may share a safety rule because they load independently. Cosmetic consistency alone does not justify merging them or deleting either copy.

## Preserve constraints and useful detail

Keep business rules, user preferences, audience context, environment facts, rationale, tool contracts, safety boundaries, and protections against demonstrated failures. Preserve format-sensitive examples and exact sequences for destructive, authentication, or compliance operations. A line that looks derivable may encode a non-obvious failure contract.

When the problem is how a constraint is expressed, rewrite it without weakening the requirement. A conflict involving a protective rule needs a proposal that preserves protection; otherwise flag it for the user instead of choosing the permissive side. Unknown model behavior or absent provenance is insufficient grounds to remove a safety rule.

Do not expand this audit into application API parameters, host permission settings, tool servers, installation health, or model migration unless the user separately requests that work. This package does not assume those facilities exist.

## Propose and verify

For each proposed edit, record the exact location, quoted evidence, violated contract or observed failure, confidence, replacement, and verification method. Static evidence can establish a stale path or direct contradiction. A claim about improved routing or model behavior requires a behavioral probe.

Keep uncertain model-era changes as flags until evidence supports them. A proposed patch should remain useful when those flags are omitted. If no demonstrated defect remains, report no justified edits; do not manufacture cleanup to populate a diff.

For an approved wording change, compare the original and revised prompt on the same task in separate fresh sessions with equivalent tools, inputs, model, and settings. Include a nearby task that should stay unaffected. Observe the resulting actions and outputs, not the model's opinion of the prompt. Treat differences in host setup or model as limits on the comparison. If a required behavior regresses, keep the original requirement and revise the wording or withdraw the change.

Use the main skill's report and approval workflow for all findings. The audit itself makes no changes to the files it inspects.
