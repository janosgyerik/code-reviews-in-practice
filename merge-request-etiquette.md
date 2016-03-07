Merge Request etiquette
=======================

*Note: work in progress, incomplete*

Merge Request in GitLab = Pull Request in GitHub = X in your favorite repo manager tool Y.

The purpose of Merge Requests is reviewing changesets.
Reviewing changesets can be a nightmare if you don't follow some rules.

Several stages to go through.

Before creating a branch
------------------------

The branch should have a clear purpose.  
=> It's hard to review a changeset with multiple unrelated changes.  
=> Code review horror: a large changeset with a bugfix, a new feature, a refactoring, and coding style changes, all in one.

The purpose should not be too big.  
=> It's hard to review a changeset of a 1000+ lines.  
=> Code review horror: a large changeset with 1000+ lines in 100+ files

The branch should start from the latest version of the source code.  
=> The risk of conflicts is higher if the branch is based on outdated code.  
=> Code review horror: a new branch based on code from 6 months ago, pre-dating a large refactoring 2 months ago

    git fetch origin master
    git checkout -b descriptive-name origin/master

Working on the branch
---------------------

One commit should be about one logical change.  
=> It's hard to review commits with multiple unrelated changes.  
=> Code review horror: a single commit with a bugfix, a new feature, a refactoring, and coding style changes, all in one.

Every commit should have a descriptive log message.  
=> It's hard to review commits with empty or unhelpful log message.  
=> Code review horror: commit messages like "fix", "refactoring", ".", "" (no message)

Review the diff before committing.  
=> It's a waste of time to review irrelevant changes that should not have been committed.  
=> Code review horror: a 100 lines diff with 99 line ending changes and one bugfix hidden somewhere in there

Creating the merge request
--------------------------

    git push origin HEAD

Review the **Changes** tab before assigning the merge request.
=> It's the final safety net for catching odd changes that should not have been committed.  
=> Code review horror: a 1000 lines diff, too many changes for GitLab to show at once.

Mark with `WIP: ` or `[WIP] ` prefix a branch that is not ready for review.
=> It's a waste of time to review something that's still a work in progress and might be heavily rewritten


Reviewing the merge request
---------------------------

Try to review merge requests you receive ASAP.  
=> The risk of conflicts is higher if the branch becomes outdated.  
=> Code review horror: by the time your merge request is reviewed, other changes in the project put the branch in conflict.

When you're done reviewing, leave a comment in the **Discussion** tab.  
=> Without an explicit signal, it's not clear when the reviewer is done reviewing.  
=> Code review horror: the coder is waiting for the reviewer, who's waiting for the coder to make corrections...

Try to make the requested corrections ASAP.  
=> The risk of conflicts is higher if the branch becomes outdated.  
=> Code review horror: by the time the corrections are done, you already forgot what the merge request was about.

When you're done making corrections, don't forget to `git push`.  
=> Without pushing, the corrections are not visible to anybody else.  
=> Code review horror: the reviewer is waiting for the coder to make corrections, who's waiting for the reviewer to review...

When you're done making corrections, leave a comment in the **Discussion** tab.  
=> Without an explicit signal, it's not clear when the coder is done making corrections.  
=> Code review horror: the reviewer is waiting for the coder to make corrections, who's waiting for the reviewer to review...

Don't make changes to the branch before the review process is completed.  
=> It's a waste of time to review a branch again and again because changes keep coming.  
=> Code review horror: after reviewing 200+ lines of heavy refactoring, the coder tells you he pushed "just one more" feature.

Avoid lengthy cycles with more than 3 rounds of reviews and corrections.  
=> 

The reviewer should not insist on perfection.  
=>

The coder should have more power than the reviewer.  
=>
=> Code review horror: the reviewer insists on using his preferred naming convention without explaining

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
=> Code review horror: 100+ obsolete branches in the project because the short lived branches were never deleted

