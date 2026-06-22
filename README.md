# su26-ai301-contribution
Weekly task for ai301
# Contribution 1: Keep action up to date in docs

**Contribution Number: 1**  
**Student:** TF - Sydelle  
**Issue:** :https://github.com/release-plz/release-plz/issues/2488  
**Status:** [Phase I / Phase II / Phase III / Phase IV] [In Progress / Complete]

---

## Why I Chose This Issue

[1-2 paragraphs explaining why this issue interests you, how it matches your skills/learning goals, what you hope to learn]
This issue seems to be very simple a a create start to my course. I already have some experience with Typescript and Python, with the 
hope to learn some rust during this project. As a punctual person myself, I like this project becuase it provides me with new algorithms and a new 
coding language to learn, and expand my skills at a steady pace.

---

## Understanding the Issue

### Problem Description

[In your own words, what's broken or missing?]
the project is using an outdated floater which poses as a security risk to pushing malicious codeto Github.

### Expected Behavior

Documentation examples should show how to pin the action to a specific commit hash, so that the action version is immutable and cannot be silently updated or tampered with.

### Current Behavior

The documentation uses floating version tags like release-plz/action@v0.5, which automatically resolve to the latest patch release. There is no warning in the primary quickstart examples that this poses a security risk.

### Affected Components

The files that contained the sensitive data and the outdates dependencies were affected the most.

---

## Reproduction Process

### Environment Setup

[Notes on setting up your local development environment - challenges you faced, how you solved them]

### Steps to Reproduce

1. Navigate to the release-plz GitHub Action documentation (e.g., the Quickstart page).
2. Observe that example workflow snippets reference the action as release-plz/action@v0.5 or similar floating tags.
3. gitIgnore should be working properly

### Reproduction Evidence

- **Commit showing reproduction:** https://github.com/SQueen19/crates.io
- **Screenshots/logs:** [If applicable]
- **My findings:** The documentation examples and the guidance on the security page are inconsistent — the security page recommends pinning to a commit hash, but other pages still show floating tags as the default examples.

---

## Solution Approach

### Analysis
[The root problem]
The root problem is a documentation inconsistency. The project's own security page correctly identifies the risk of floating version tags and recommends pinning to a commit SHA, but this best practice is not reflected in the primary usage examples throughout the docs.

### Proposed Solution

[High-level description of your fix approach]
Update the documentation examples to use a pinned commit hash (with the version noted in a comment) rather than a floating tag. This aligns the examples with the guidance already present on the security page and reduces risk for users who copy-paste from the docs without reading the security section.

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** The docs show release-plz/action@v0.5 in examples, which is a floating tag. The security page explains this is a risk and recommends using a full commit SHA instead.

**Match:**  The security page already provides a correct pinned example (release-plz/action@63ab0c2746bedc448370bad4b0b3d536458398b0 # v0.5.50). The same pattern is used in the crates.io repository's own CI configuration. This is the model to follow.

**Plan:** [Step-by-step implementation plan]
Identify all documentation markdown files that contain GitHub Action workflow examples using floating tags.
Replace floating tags with a pinned commit SHA, with the version noted in an inline comment for human readability.
Verify the updated examples are consistent with the security page guidance.


**Implement:** Changes are limited to markdown documentation files — no functional code changes required.

**Review:**  Confirm the updated examples match the format already shown on the security page, and that no other doc pages still show unpinned tags.

**Evaluate:** Success is verified by reading through the updated docs and confirming all action references use commit-pinned syntax.

---

## Testing Strategy - Left blank as it's all N/A as a TF

### Unit Tests

- [ ] Test case 1: [Description]
- [ ] Test case 2: [Description]
- [ ] Test case 3: [Description]

### Integration Tests

- [ ] Integration scenario 1
- [ ] Integration scenario 2

### Manual Testing

[What you tested manually and results]

---

## Implementation Notes

### Week [X] Progress

[What you built this week, challenges faced, decisions made]

### Week [Y] Progress

[Continue documenting as you work]

### Code Changes

- **Files modified:** [List]
- **Key commits:** [Links to important commits]
- **Approach decisions:** [Why you chose certain approaches]

---

## Pull Request

**PR Link:** [GitHub PR URL when submitted]

**PR Description:** [Draft or final PR description - much of the content above can be adapted]

**Maintainer Feedback:**
- [Date]: [Summary of feedback received]
- [Date]: [How you addressed it]

**Status:** [Awaiting review / Iterating / Approved / Merged]

---

## Learnings & Reflections

### Technical Skills Gained

[What you learned technically]

### Challenges Overcome

[What was hard and how you solved it]

### What I'd Do Differently Next Time

[Reflection on your process]

I would look at all documentation pages more systematically from the start, rather than just the ones directly linked from the issue, to make sure I caught every instance of the floating tag pattern before beginning the fix.
---

## Resources Used

- https://release-plz.dev/docs/github/security — Project's own security guidance page explaining the risk and recommended fix
- https://github.com/release-plz/release-plz/issues/2488 — Original issue
- https://github.com/rust-lang/crates.io/blob/7e52e11c5ddeb33db70f0000bbcdfb01e9b43b0d/.github/workflows/ci.yml#L30 — Real-world example of commit-pinned action reference used by crates.io
