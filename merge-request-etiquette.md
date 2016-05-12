Merge Request etiquette
=======================

*Note: work in progress, incomplete*

*Merge Request* in GitLab is equivalent to *Pull Request* in GitHub.
For simplicity I will use only merge request consistently in this document.
Please translate it to the appropriate equivalent in your toolbox.

The purpose of merge requests is reviewing changesets,
in order to find problems, such as bugs, careless mistakes, bad practices.
It's a good way to guide less experienced programmers.
It's an effective way to make all programmers on the team better,
bringing everybody up to the same high level.

How to benefit the most from using merge requests?
Some developers think that merge requests take too much time.
That's only true when not done well.

This document is a listing of practical tips and recommendations,
grouped by stages in the typical lifecycle of a feature branch.
Each example starts with a clear statement (recommendation),
followed by an explanation or justification,
followed by examples (from real life!) of what can go wrong,
labeled *Code Review Horror*.
You will do well to avoid these *merge request smells*!

Before creating a branch
------------------------

The branch should have a clear purpose.

It's hard to review a changeset with many unrelated changes.
Take a moment to think carefully before diving head first into coding.

Code Review Horror: a large changeset containing a bugfix... and a new feature... and a refactoring... and coding style changes... all in one.

---

The purpose of the branch should not be too big.

When a changeset grows to (and beyond) 200+ changed lines in 20+ files,
it can become extremely difficult to review and understand.
If it's not possible to divide a purpose to smaller logical steps,
at least try to divide to stable stages.

Code Review Horror: a large changeset with 1000+ lines in 100+ files

---

The branch should start from the latest version of the source code.

    git fetch origin master
    git checkout -b descriptive-name origin/master

The risk of conflicts is higher if the branch is based on outdated code.

Code Review Horror: a new branch based on code from 6 months ago, pre-dating a large refactoring 2 months ago

Working on the branch
---------------------

Commits should be atomic: perform a single logical change.

It's hard to review commits with multiple unrelated changes.

Code Review Horror: a single commit containing a bugfix... and a new feature... and a refactoring... and coding style changes... all in one.

---

Every commit should have a descriptive log message.

It's hard to review commits with empty or unhelpful log message.

Code Review Horror: commit messages like "fix", "refactoring", ".", "" (no message)

---

Review the diff before committing.

It's a waste of time to review irrelevant changes that should not have been committed.

Code Review Horror: a 100 lines diff with 99 line ending changes and one bugfix hidden somewhere in there

Creating the merge request
--------------------------

    git push origin HEAD

Review the **Changes** tab before assigning the merge request.

It's the final safety net for catching odd changes that should not have been committed.

Code Review Horror: a 1000 lines diff, too many changes for GitLab to show at once.

---

Mark with `WIP: ` or `[WIP] ` prefix a branch that is not ready for review.

It's a waste of time to review something that's still a work in progress and might be heavily rewritten.

Code Review Horror: after you reviewed a difficult changeset, the author pushes 10 more commits that completely change the implementation strategy, invalidating your review.

Code Review Horror: after you point out obvious problems in the code, the author tells you that "he knows", the code so far was just a temporary step, he was just about to do some cleaning up of exactly the things you pointed out.

Reviewing the merge request
---------------------------

Try to review merge requests you receive ASAP.

The risk of conflicts is higher if the branch becomes outdated.

Code Review Horror: by the time your merge request is reviewed, other changes in the project put the branch in conflict.

---

When you're done reviewing, leave a comment in the **Discussion** tab.

Without an explicit signal, it's not clear when the reviewer is done reviewing.

Code Review Horror: the coder is waiting for the reviewer, who's waiting for the coder to make corrections...

---

Try to make the requested corrections ASAP.

The risk of conflicts is higher if the branch becomes outdated.

Code Review Horror: by the time the corrections are done, you already forgot what the merge request was about.

---

When you're done making corrections, don't forget to `git push`.

Without pushing, the corrections are not visible to anybody else.

Code Review Horror: the reviewer is waiting for the coder to make corrections, who's waiting for the reviewer to review...

---

When you're done making corrections, leave a comment in the **Discussion** tab.

Without an explicit signal, it's not clear when the coder is done making corrections.

Code Review Horror: the reviewer is waiting for the coder to make corrections, who's waiting for the reviewer to review...

---

Don't make changes to the branch before the review process is completed.

It's a waste of time to review a branch again and again because changes keep coming.

Code Review Horror: after reviewing 200+ lines of heavy refactoring, the coder tells you he pushed "just one more" feature.

---

Avoid lengthy cycles with more than 3 rounds of reviews and corrections.

TODO why

TODO Code Review Horror

---

The reviewer should not insist on perfection.

TODO why

TODO Code Review Horror

---

The coder should have more power than the reviewer.

TODO why

Code Review Horror: the reviewer insists on using his preferred naming convention without explaining

---

Don't attack the coder.

TODO why

TODO Code Review Horror

---

Don't attack the reviewer.

TODO why

TODO Code Review Horror

---

Avoid reviewing unassign or self-assigned merge requests.

TODO why

TODO Code Review Horror

Accepting the merge request
---------------------------

Delete the source branch.

TODO why

Code Review Horror: 100+ obsolete branches in the project because the short lived branches were never deleted

