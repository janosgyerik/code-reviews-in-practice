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

The purpose should not be too big.
=> It's hard to review a changeset of a 1000+ lines.

The branch should start from the latest version of the source code.
=> The risk of conflicts is higher if the branch is based on outdated code.

    git fetch origin master
    git checkout -b descriptive-name origin/master

Working on the branch
---------------------

One commit should be about one logical change.
=> It's hard to review commits with multiple unrelated changes.

Every commit should have a descriptive log message.
=> It's hard to review commits with empty or unhelpful log message.

Review the diff before committing.
=> It's a waste of time to review irrelevant changes that should not have been committed.

Creating the merge request
--------------------------

    git push origin HEAD

Review the **Changes** tab before assigning the merge request.
=>

Reviewing the merge request
---------------------------

Attitude...
=>

Accepting the merge request
---------------------------

TODO

