# Skill health

Assess the library the user selected. Use documented host behavior where available; a common file convention is not proof that every host implements it identically.

## Discovery and metadata

Inventory each entry point by path, declared name, description, and source root. Track aliases or duplicate paths so one physical skill is not counted twice. Separate installed files, discovered entries, and entries visible to the model when the evidence distinguishes them.

Parse the frontmatter and check the fields the intended host requires. For a portable `SKILL.md`, the baseline is a nonempty string `name` and `description`; additional fields may be host-specific. Flag dependencies on unsupported metadata only when documentation or execution establishes that lack of support. Do not invent a universal name limit, nesting rule, precedence order, or malformed-frontmatter fallback.

Discover an available runtime and trusted parser before attempting validation. A missing executable alias establishes only that the alias is missing, not that metadata validation is unavailable; check available alternatives before reporting a gap.

A repeated name is a possible collision, not proof that either skill is unused or which definition wins. Cite all locations and the known loading policy. Where the policy is unknown, report the ambiguity. Renaming can preserve separate jobs; merging requires evidence that the jobs and constraints belong together. A short or generic name alone is not a defect.

## Routing and contract

Compare the entry's advertised task with its body, side effects, dependencies, and output. Report descriptions that route unrelated tasks into a narrow workflow, omit a needed trigger, or promise behavior the body cannot deliver. A description that says read-only while the body requires mutations is a contract mismatch.

Assess overlapping descriptions by their tasks and boundaries, not shared vocabulary. Recommend a clearer boundary when a request could reasonably select the wrong skill. Keep distinct tasks separate unless a combined skill would preserve both contracts and improve selection.

Separate routing text from behavioral instructions. Descriptions should help the host or model select the skill; procedures belong in the body or linked reference. For user-invoked skills, honor the host's documented invocation semantics rather than demanding autonomous trigger coverage. Route model-sensitive concerns through the prompt audit reference when that audit is included.

## References and portability

Resolve local references relative to the file containing them. Check path spelling and case, anchors when present, and whether required assets or scripts exist. Distinguish a missing literal path from a documented template path. Inspect code or manifests to validate named entry points and flags when needed; do not run a skill's commands merely to see what they do.

Each required reference needs a pointer explaining when to read it. Follow the in-scope reference graph until the task's prerequisites are accounted for; report unresolved or out-of-scope dependencies. A reference to an unavailable sibling skill is a portability gap even if the current host happens to provide it.

Look for private absolute paths, internal tool URLs, mandatory slash commands, and assumptions about settings or transcript layouts. Explain which behavior depends on the original host and how to express it through a capability or a self-contained reference. Retain exact tool contracts where those tools are the skill's subject; portability does not mean removing necessary domain knowledge.

Before proposing a move, trace callers and links. A root instruction, path-scoped rule, and lazily read reference have different reach. Moving a universal or safety-critical instruction into a reference can remove protection from tasks that never load it.

## Usage and retirement

Use history only if the user supplies it or the host exposes an authorized, documented source. Separate lifetime counts from activity within a named window. Count recorded invocations using the source's actual schema; a name appearing in conversation is not an invocation. Distinguish a model-selected skill, explicit user selection, and guidance read indirectly where the evidence permits.

With no reliable history, mark usage **unknown**. Zero recorded invocations does not prove that a referenced, manually selected, new, or emergency skill provides no value. Do not recommend retirement from missing telemetry, name similarity, or zero counts alone.

A retirement proposal needs a reason beyond a count: the user confirms the workflow is retired, a successor covers its callers and contract, or the dependency it serves no longer exists. Explain the evidence and the consequence of removing it. Preserve safety guidance and shared references; propose redirects through caller updates rather than leaving broken pointers.

## Context and lazy loading

Distinguish description/listing cost, body cost on invocation, and reference cost when read. Report actual host-injected text if available. Otherwise describe disk size as disk size, not resident context. A file being under `references/` does not prove that the host defers it.

If tokens are requested and no tokenizer is available, characters / 4 may be reported only as a rough estimate with the counting scope and tokenizer limitation stated. Do not assert a universal listing budget or per-session savings. Potential savings depend on what the host actually loads and how often.

Prefer a short entry point with task-specific references when it improves selection or reading. Keep prerequisite context, failure contracts, and protective rules where every affected task will encounter them. Duplication across different loading scopes can be deliberate; propose deduplication only after demonstrating that the remaining copy reaches every relevant consumer.
