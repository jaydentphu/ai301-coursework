# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| maintainer-alive | Repo facts: "last 5 default-branch commits" and "maintainer first-response sample" | At least one of the last 5 default-branch commits is authored by a human (non-'bot') within 90 days of the capture date, OR the maintainer first-response sample shows a reply from someone with Owner/Member/Collaborator badge within 30 days | required |
| repo-in-use | Repo facts: "archived:", "latest release", "last push to any branch" | Repo is not archived, AND last push to any branch is within 180 days of the capture date | required |
| newcomer-scope | Issue body, Comments section, and linked-PR list in Repo facts | Fails if any of: (a) framed as a tracking issue whose sub-items are meant to be split into separate issues/PRs — a single cohesive task or bug with several internal steps or proposed approaches still passes; (b) an unresolved design debate is visible in the thread with no maintainer having settled it, OR the issue was authored by a bot (author name ends in [bot], author_association NONE) with zero human engagement in the comments; (c) a maintainer states the fix requires changes to core internals; (d) the issue has 2 or more closed, unmerged linked PRs, or the comment thread shows a repeated pattern of contributors claiming it and being auto-unassigned for inactivity | required |
| unclaimed | Repo facts: "this issue: assignees:", "linked PRs:", Comments section | No assignee is listed, no linked PR is in an open state, and no "I'll take this" style claim comment from another contributor is left unanswered/unaddressed by a maintainer | required |
| ai-policy-allows | Repo facts: "contribution policy" line (CONTRIBUTING.md / AI_POLICY.md content) | The contribution policy does not contain an outright ban on AI-generated or AI-assisted contributions. Disclosure requirements, testing requirements, or human-review requirements are conditions, not bans, and pass | required |
| good-first-label | Comments/label events in the thread | Issue currently carries a "good first issue" or equivalent newcomer-friendly label | preferred |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->

Accept only if every required check (maintainer-alive, repo-in-use, newcomer-scope, unclaimed, ai-policy-allows) passes. A single required check failing rejects the issue, regardless of the others. `unclear` on any required check counts as a fail for that check. The preferred check (good-first-label) never changes the verdict — it only ranks accepted issues higher when present.