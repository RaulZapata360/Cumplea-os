# SOP Standardizer

Convert any process description into a formal, executable SOP that a new hire can follow on day one — no assumed knowledge, no ambiguity, no "we."

## SOP Quality Standards

A great SOP has these properties:

- **No assumed knowledge** — Every step is explicit, even the obvious ones
- **Role-specific** — It's clear WHO does each step (not "we" — a specific role)
- **Decision-ready** — Edge cases and decision points are explicitly handled inline
- **Tool-specific** — Every step names the exact tool used (Notion / Slack / Salesforce)
- **Outcome-defined** — It's clear what a completed step looks like
- **Independently executable** — A person with no context can run this process

## Process

```
1. READ      -> Read the full description before writing anything
2. EXTRACT   -> Identify all steps (explicit and implied), roles, and tools
3. GAPS      -> Flag unclear or missing steps before filling them in — ask, don't guess
4. WRITE     -> Fill in the SOP template exactly as shown below
5. CHECKLIST -> After the full SOP, produce a condensed one-page quick reference version
```

## SOP Template (Always Use This Exactly)

```markdown
# [Process Name]

**Purpose**: [One sentence: why this process exists]
**Process Owner**: [Role title — never a person's name]
**Trigger**: [What event or condition starts this process?]
**Frequency**: [How often is this run?]
**Tools Required**: [List every tool used]
**Output**: [What is produced when this process is complete?]
**Estimated Time**: [How long does this take end to end?]

---

## Steps

### Step 1: [Action Verb + Object]
**Who**: [Role]
**Tool**: [Specific tool/platform]
**Action**: [Exact steps to take — numbered sub-steps if needed]
**Output**: [What does "done" look like for this step?]
**If [edge case] happens**: [What to do]

### Step 2: [Action Verb + Object]
**Who**: [Role]
**Tool**: [Specific tool/platform]
**Action**: [Exact steps]
**Output**: [Done state]

[Continue for all steps...]

---

## Quality Checks
- [ ] [Check 1]
- [ ] [Check 2]

## Common Mistakes
- **[Mistake 1]**: How to avoid it
- **[Mistake 2]**: How to avoid it

## Version History
| Date | Change | Author |
|---|---|---|
| [Date] | Initial version | [Role] |
```

---

## Condensed Quick Reference (Always Include After Full SOP)

After the full SOP, produce a one-page version for people running the process regularly:

```markdown
## Quick Reference: [Process Name]

**Trigger**: [One line]
**Owner**: [Role]
**Time**: [Estimate]

| Step | Who | Tool | Done When |
|---|---|---|---|
| 1. [Action] | [Role] | [Tool] | [Output] |
| 2. [Action] | [Role] | [Tool] | [Output] |
| 3. [Action] | [Role] | [Tool] | [Output] |

**Quality checks**: [List inline]
**Common mistakes**: [List inline]
```

## Writing Rules

- Start every step with an action verb: Open / Click / Enter / Review / Send / Confirm / Notify
- Never use "we" — always a specific role title
- If a step requires judgment, mark it: ⚠️ JUDGMENT REQUIRED — then explain what factors to weigh
- Every edge case goes inline: "If [X] happens: [do Y]" — not in a footnote
- If a tool isn't specified in the input, flag it: "[Tool unknown — confirm with process owner]"

## How to Trigger

```
"Convert this into a formal SOP with the standard structure. Flag anything unclear."
[Paste notes, transcript, bullet points, or verbal brain dump]
```

## Edge Cases

**Complex process with many branches**: Break into sub-SOPs. Write a parent SOP that references them by name. Long, heavily nested SOPs are harder to follow than a family of shorter linked ones.

**Process owned by multiple roles**: Add a RACI table at the top before the steps:

```markdown
## RACI
| Step | Responsible | Accountable | Consulted | Informed |
|---|---|---|---|---|
| Step 1 | [Role] | [Role] | [Role] | [Role] |
```

**Process that has never been documented before**: After completing the SOP, add this note at the top:

```
⚠️ DRAFT: This SOP was written from [description/verbal input].
Recommend running one real execution while following these steps
and updating anything that was missing or wrong before publishing.
```

**Missing information in the input**: List every gap explicitly before writing the SOP:

```
Before I write this SOP, I need to clarify:
1. [Question about unclear step]
2. [Question about which tool is used]
3. [Question about who owns step X]
```
Do not guess and fill gaps silently — always surface them.
