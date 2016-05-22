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
Furthermore, Git recommends the following:

> Though not required, it's a good idea to begin the commit message with
> a single short (less than 50 character) line summarizing the change,
> followed by a blank line and then a more thorough description.

Code Review Horror: commit messages like "fix", "refactoring", ".", "" (no message), "again", "re"

---

Review the diff before committing.

Be careful to not commit irrelevant, unnecessary changes.
When unintended, irrelevant changes slip into the feature branch,
it can be distracting and confusing for reviewers.
It's a waste of time to review irrelevant changes that should not have been committed.

Code Review Horror: a 100 lines diff with 90+ line ending changes and one bugfix hidden somewhere within

Creating the merge request
--------------------------

Review the **Changes** tab before assigning the merge request.
(Optionally, assign the merge request to yourself, temporarily.)

Just like it's good to review the diff before every commit,
it's good to re-review the changes of the complete branch.
Do a self-review.
Look for bugs you overlooked.
Look for corner cases not handled.
Look for unrelated changes that were accidentally included.
Look for pointless changes that were accidentally included.
Is the code readable? Is the changeset reasonably small enough to review?
Make any necessary fixes and only assign the branch when it's ready.

Code Review Horror: a 1000 lines diff, with too many changes to diplay in the web interface, with a hodge-podge of unrelated changes, unnecessary changes, riddled with bugs and bad practices.

---

Mark with `WIP: ` or `[WIP] ` prefix a branch that is not ready for review.
(Alternatively, assign the merge request to yourself, temporarily.)

If a merge request is not ready,
you may not want others to look at it yet,
or at least give some kind of signal that it may be changed or even rewritten.

Code Review Horror: after you reviewed a difficult changeset, the coder pushes 10 more commits that completely change the implementation strategy, invalidating your review.

Code Review Horror: after you point out obvious problems in the code, the coder tells you that "he knows", the code so far was just a temporary step, he was just about to do some cleaning up of exactly the things you pointed out.

Reviewing the merge request
---------------------------

Try to review merge requests you receive ASAP.

The risk of conflicts is higher if the branch becomes outdated.
The cost of task switching (for the coder) is higher the next day,
and even higher later.

Code Review Horror: by the time your merge request is reviewed, other changes in the project put the branch in conflict.

Code Review Horror: by the time your merge request is reviewed, you already forgot what the merge request was about, and it's hard to refresh your memory.

---

When you're done reviewing, leave a comment in the **Discussion** tab, so that the coder knows that the ball is in his court.

Without an explicit signal, it's not clear when the reviewer is done reviewing.

Code Review Horror: the coder is waiting for the reviewer to finish reviewing, while at the same time the reviewer is waiting for the coder to make corrections...

---

Try to make the requested corrections ASAP.

The risk of conflicts is higher if the branch becomes outdated.
After you are done with corrections,
the reviewer has to review again.
If you let too much time pass,
the cost of task switching for the reviewer will increase.

Code Review Horror: by the time the corrections are done, you already forgot what the merge request was about and it's hard to refresh your memory.

---

When you're done making corrections, don't forget to `git push`.

Without pushing, the corrections are only on your computer, not visible anybody else.

Code Review Horror: the coder thinks he's done, and waiting for the reviewer, but the corrections are not even visibile yet, as they only exist on the coder's computer.

---

When you're done making corrections, leave a comment in the **Discussion** tab.

GitLab doesn't send a notification to reviewers on new pushes to the branch.
And that's normal, because a push doesn't necessarily mean that the branch is ready for the next round of review.
Only the coder can know that, so without an explicit signal by the coder,
the reviewer cannot know that the branch is ready for the next round of review.

Code Review Horror: the reviewer is waiting for the coder to make corrections, while at the same time the coder is waiting for the reviewer to review...

---

Don't make changes to the branch while the review is in progress.

It's not practical to review something that is still changing.
A change might invalidate some comments of the reviewer, making it a waste of time.
After reviewing the entire changeset, if something changes in the middle,
there's no easy way to review only the significant part,
the reviewer is typically forced to re-read the entire changeset,
which is a waste of time.

Code Review Horror: after reviewing 200+ lines of heavy refactoring, the coder tells you he pushed "just one more" feature.

Code Review Horror: while commenting on an approach, a new commit comes in that changes the approach, invalidating your comment.

---

Avoid lengthy cycles with more than 3 rounds of reviews and corrections.

After about 3 cycles of reviews and corrections,
both the coder and the reviewer start to get fatigued by the merge request.
This can lead to mistakes and strain the relationship.
If there are only minor issues with the merge request,
suggest to postpone corrections to a new "cleanup branch".
If there are serious issues with the merge request,
consider to reject and ask for rework from scratch.

TODO Code Review Horror

---

The reviewer should not insist on perfection.

If the coder has made some corrections,
the code review process has already served its purpose,
improving on the original work.
If the code is already good enough,
the cost of further improvements toward perfection might be too high compared to the benefits to gain.

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

