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

This document is a listing of bad examples, taken from real life,
labeled *Code Review Horror*, and how to avoid them.
The examples are grouped by stages in the typical lifecycle of a feature branch.

Before creating a branch
------------------------

The branch should have a clear purpose.  
=> It's hard to review a changeset with multiple unrelated changes.  
=> Code Review Horror: a large changeset with a bugfix, a new feature, a refactoring, and coding style changes, all in one.

The purpose should not be too big.  
=> It's hard to review a changeset of a 1000+ lines.  
=> Code Review Horror: a large changeset with 1000+ lines in 100+ files

The branch should start from the latest version of the source code.  
=> The risk of conflicts is higher if the branch is based on outdated code.  
=> Code Review Horror: a new branch based on code from 6 months ago, pre-dating a large refactoring 2 months ago

    git fetch origin master
    git checkout -b descriptive-name origin/master

Working on the branch
---------------------

One commit should be about one logical change.  
=> It's hard to review commits with multiple unrelated changes.  
=> Code Review Horror: a single commit with a bugfix, a new feature, a refactoring, and coding style changes, all in one.

Every commit should have a descriptive log message.  
=> It's hard to review commits with empty or unhelpful log message.  
=> Code Review Horror: commit messages like "fix", "refactoring", ".", "" (no message)

Review the diff before committing.  
=> It's a waste of time to review irrelevant changes that should not have been committed.  
=> Code Review Horror: a 100 lines diff with 99 line ending changes and one bugfix hidden somewhere in there

Creating the merge request
--------------------------

    git push origin HEAD

Review the **Changes** tab before assigning the merge request.
=> It's the final safety net for catching odd changes that should not have been committed.  
=> Code Review Horror: a 1000 lines diff, too many changes for GitLab to show at once.

Mark with `WIP: ` or `[WIP] ` prefix a branch that is not ready for review.
=> It's a waste of time to review something that's still a work in progress and might be heavily rewritten.  
=> Code Review Horror: after you reviewed a difficult changeset, the author pushes 10 more commits that completely change the implementation strategy, invalidating your review.  
=> Code Review Horror: after you point out obvious problems in the code, the author tells you that "he knows", the code so far was just a temporary step, he was just about to do some cleaning up of exactly the things you pointed out.


Reviewing the merge request
---------------------------

Try to review merge requests you receive ASAP.  
=> The risk of conflicts is higher if the branch becomes outdated.  
=> Code Review Horror: by the time your merge request is reviewed, other changes in the project put the branch in conflict.

When you're done reviewing, leave a comment in the **Discussion** tab.  
=> Without an explicit signal, it's not clear when the reviewer is done reviewing.  
=> Code Review Horror: the coder is waiting for the reviewer, who's waiting for the coder to make corrections...

Try to make the requested corrections ASAP.  
=> The risk of conflicts is higher if the branch becomes outdated.  
=> Code Review Horror: by the time the corrections are done, you already forgot what the merge request was about.

When you're done making corrections, don't forget to `git push`.  
=> Without pushing, the corrections are not visible to anybody else.  
=> Code Review Horror: the reviewer is waiting for the coder to make corrections, who's waiting for the reviewer to review...

When you're done making corrections, leave a comment in the **Discussion** tab.  
=> Without an explicit signal, it's not clear when the coder is done making corrections.  
=> Code Review Horror: the reviewer is waiting for the coder to make corrections, who's waiting for the reviewer to review...

Don't make changes to the branch before the review process is completed.  
=> It's a waste of time to review a branch again and again because changes keep coming.  
=> Code Review Horror: after reviewing 200+ lines of heavy refactoring, the coder tells you he pushed "just one more" feature.

Avoid lengthy cycles with more than 3 rounds of reviews and corrections.  
=> 

The reviewer should not insist on perfection.  
=>

The coder should have more power than the reviewer.  
=>
=> Code Review Horror: the reviewer insists on using his preferred naming convention without explaining

Don't attack the coder.  
=>

Don't attack the reviewer.  
=>

Avoid reviewing unassign or self-assigned merge requests.  
=>

Accepting the merge request
---------------------------

Delete the source branch.  
=> 
=> Code Review Horror: 100+ obsolete branches in the project because the short lived branches were never deleted

