Code reviews in practice
========================

*This is a work in progress.*
*If you have some specific ideas or questions, feel free to [create an issue](https://github.com/janosgyerik/code-reviews-in-practice/issues) and I'll try to include it. [Pull requests](https://github.com/janosgyerik/code-reviews-in-practice) are also welcome!*

What is a code review? How does it work? There are many interpretations, implementations and misconceptions.

In this document I explain one way of doing it, that's simple, practical and has minimal administrative overhead. The benefits are cost savings, improved quality of code, improved collaboration and team morale.

My goal is for this document to become a handbook that anybody can use to implement the practice of code reviews in their teams efficiently, and to realize its benefits easily.

What is a code review?
----------------------

In the context of this document, code review is about getting your changes reviewed by another programmer before merging it into the main code-base of a project. Ideally the reviewer is in the same team and has a good understanding of the project. But it could be any other programmer. It's crucial to have *somebody else* review your work. There can be multiple reviewers, but there should be at least one.

The review is an iterative process: the reviewer suggests improvements, you make corrections, and the reviewer checks again. Repeat until the code looks good enough (to the reviewer).

The code review workflow
------------------------

In a nutshell:

- The project advances forward through short-lived feature branches. This working style is a pre-requisite.

- You implement a specific change in a series of commits on a dedicated feature branch, and propose it to another developer for merging.

- The other developer reviews the changeset, and suggests improvements by leaving comments on specific lines, or on the changeset as a whole.

- Following the suggestions, you improve the changeset and push the new commits for another round of review.

- The review + corrections cycle repeats until the reviewer is satisfied, and accepts the changeset into mainline.

Some crucial points:

- The practice of short-lived feature branches is a prerequisite. If the team doesn't follow this recommended working style, then code reviews may not be feasible.

- It's important to use a tool like GitHub, GitLab, or similar, where commenting on specific lines is easy, with a user-friendly interface.

- The review process should not hold up development. You can work on another branch while waiting for the review. This implies that developers should be comfortable with working on multiple branches in parallel.

Some common misconceptions:

- Myth: "we don't have time for code reviews". To understand the time cost of code reviews, you need to consider the long-term effects. Correcting bugs released in production can be extremely expensive. Code reviews are known to be an effective method to catch bugs early. They also help catching conceptual errors early, which would be extremely expensive to correct later. Code reviews have many other positive effects that feed back to cost savings. Overall, code reviews save far more time than they cost.

- Myth: "code review is just too hard to do, because it's impossible to review large changesets". The problem is not with the idea of code reviews, but with the changesets. Such changesets indicate incorrect use of feature branches. Keep changesets to a manageable size.

- Myth: "doing code reviews slows down development, because the reviewer keeps the developer waiting". No, the developers shouldn't wait for the review. They should know how to work on another branch. The other branch may be a continuation of the branch pending review.

- Myth: "it's impossible to read diffs". It's not impossible. It may take a couple of days, but you can get used to it.

Is my team ready for code reviews?
----------------------------------

It's important to evaluate the readiness of your team first. Trying to push code reviews may fail spectacularly if the team is not yet following certain good practices:

- One commit == one logical change. Developers should have the good sense to commit each logical step by step, going from stable build to stable build. Try to educate the team: committing this way is widely recommended.

- Development advances forward through short-lived feature branches. Feature branches are the crucial unit of work in the workflow outlined above. Try to transition the team to this working style.

- Using distributed version control system. Without a distributed version control system, branch management might be too hard to be practical. Try to migrate your tools to any of the well-known distributed VCS.

- Developers are open-minded, curious, and willing to learn from their peers. They can take their egos out of the equation, able to both give and take constructive criticism. Reading Chapter 33 in Code Complete might help achieving that.

Without the above, code reviews are unlikely to work well. Try to get the above issues out of the way. Rest assured, these are all recommended and widely accepted practices that any project would benefit from, regardless of using code reviews or not. Be patient and calm, keep pushing, inching forward step by step.

Resources
---------

I was most inspired by these articles:

- [Code Reviews: Just Do It](http://blog.codinghorror.com/code-reviews-just-do-it/)
- [Pair Programming vs. Code Reviews](http://blog.codinghorror.com/pair-programming-vs-code-reviews/)
- [Code Complete 2: Chapter 28: Managing Construction](http://www.cc2e.com/)

To be continued...
------------------

More sections are coming soon with more details. For example, practical tips & tricks about our process in my teams.

*If you have some specific ideas or questions, feel free to [create an issue](https://github.com/janosgyerik/code-reviews-in-practice/issues) and I'll try to include it. [Pull requests](https://github.com/janosgyerik/code-reviews-in-practice) are also welcome!*
