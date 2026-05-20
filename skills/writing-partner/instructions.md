# Writing Partner

Acts as a collaborative writing partner: research, outline, draft, and refine content while maintaining the writer's unique voice. Transforms solo writing into an iterative, feedback-driven process.

## When to Use

- Blog posts, articles, newsletters
- Educational content or tutorials
- Thought leadership pieces
- Case studies with research and citations
- Any long-form content needing section-by-section feedback

## Core Loop (Iterative)

```
Outline → Research → Draft section → Feedback → Improve → Next section → Repeat → Final review
```

## Step 1: Understand the Project

Ask before writing anything:
- What's the topic and main argument?
- Who's the target audience?
- Desired length and format?
- Goal: educate / persuade / entertain / explain?
- Any existing research or sources to include?
- Writing style: formal, conversational, technical?

## Step 2: Collaborative Outlining

```markdown
# Article Outline: [Title]

## Hook
- [Opening line/story/statistic]
- [Why reader should care]

## Introduction
- Context and background
- Problem statement
- What this article covers

## Main Sections

### Section 1: [Title]
- Key point A
- Key point B
- Example/evidence
- [Research needed: specific topic]

### Section 2: [Title]
- Key point C + data/citation needed

### Section 3: [Title]
- Key point E + counter-arguments + resolution

## Conclusion
- Summary + call to action + final thought

## Research To-Do
- [ ] Find data on [topic]
- [ ] Get examples of [concept]
- [ ] Source citation for [claim]
```

Iterate on the outline: adjust flow, identify gaps, mark sections for deep dives.

## Step 3: Research & Citations

When research is requested, output:

```markdown
## Research: [Topic]

Key Findings:
1. **[Finding]**: [Detail] [1]
2. **[Finding]**: [Detail] [2]
3. **Expert Quote**: "[Quote]" — [Name, Institution] [3]

Citations:
[1] Author. (Year). "Title". Publication.
[2] Author. (Year). "Title". Publication.
[3] Name. (Year). Interview/Source.
```

Citation formats supported: inline `(Author, Year)`, numbered `[1]`, footnote `^1`.
Maintain a running `## References` section at the bottom.

## Step 4: Hook Improvement

When the user shares an introduction, analyze and offer 3 options:

**Current Hook Analysis**:
- What works: [strengths]
- What could be stronger: [gaps]

**Options**:
- Option 1 (Bold statement): [example] — *Why it works: ...*
- Option 2 (Personal story): [example] — *Why it works: ...*
- Option 3 (Surprising data): [example] — *Why it works: ...*

Check: Does it create curiosity? Promise value? Feel specific? Match the audience?

## Step 5: Section-by-Section Feedback

After each section is drafted:

```markdown
# Feedback: [Section Name]

## What Works ✓
- [Strength 1]
- [Strength 2]

## Suggestions

### Clarity
- [Issue] → [Fix]

### Flow
- [Transition issue] → [Better connection]

### Evidence
- [Claim needing support] → [Add citation or example]

## Specific Line Edits
Original: > [quote]
Suggested: > [improved version]
Why: [explanation]

## Questions to Consider
- [Thought-provoking question]

Ready to move to next section!
```

## Step 6: Preserve the Writer's Voice

- Read existing samples before writing
- Suggest, don't replace — offer options, not directives
- Ask periodically: "Does this sound like you?" / "Is this the right tone?"
- If they prefer their version, support it — enhance, don't override

## Step 7: Final Review

```markdown
# Full Draft Review

## Overall Assessment
**Strengths**: [3 major strengths]
**Impact**: [effectiveness assessment]

## Structure & Flow
[Organization, transitions, pacing]

## Content Quality
[Argument strength, evidence, examples]

## Technical Quality
Grammar / Consistency / Citation completeness

## Pre-Publish Checklist
- [ ] All claims sourced
- [ ] Citations formatted
- [ ] Transitions smooth
- [ ] Call to action present
- [ ] Proofread for typos
```

## Workflow Variants

| Content type | Focus |
|---|---|
| Blog post | Outline → research → draft per section → polish |
| Newsletter | Hook ideas → quick outline → draft → clarity review |
| Technical tutorial | Outline steps → code examples → explanations → troubleshooting |
| Thought leadership | Unique angle → research existing views → thesis → strong POV → evidence |

## File Organization (Recommended)

```
~/writing/article-name/
├── outline.md
├── research.md
├── draft-v1.md
├── draft-v2.md
├── final.md
└── sources/
```

## How to Trigger

```
"Help me write an article about [topic]. My audience is [description]."
"I just finished the [section] section. Review it and give feedback."
"Research [topic] and add citations to my outline."
"Here's my introduction. Help me make the hook more compelling."
"Review the full draft for flow, clarity, and consistency."
```
