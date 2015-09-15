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

Code review is an iterative process: the reviewer suggests improvements, you make corrections as appropriate, and the reviewer checks again. Repeat until the code looks good enough.

What benefits can you expect?
-----------------------------

The practice of code reviews can bring great benefits:

- Catch construction bugs early: fixing a bug in production can be very expensive. Code reviews can prevent bugs from getting released by catching them early.

- Catch class design bugs early: poorly designed classes and methods can lead to unmaintainable spaghetti code. Code reviews can prevent long-term code rot by catching bad tendencies early.

- Improved collective knowledge about the code-base of the project: thanks to the review process, at least two developers understand every piece of code in the code-base.

- Improved collaboration and team morale: the review process requires multiple developers to work together. The process improves confidence in their own work and that of their peers.

What are the challenges in implementing code reviews?
-----------------------------------------------------

The workflow presented in the next section addresses these main challenges:

- How to avoid slowing down development?
- What tools can make it easy and how?

Other questions can be answered easily:

- Should you review very small changesets that seem trivial?
  + Yes! There's a lot of empirical evidence of single-line changes causing massive failures.

- How often to perform, and how much code to cover at a time?
  + Work on feature branches, and keep them small enough for reasonably easy reviewing. Too small changesets are not very interesting, too big changesets are too hard to review.

- How deeply should you inspect the code?
  + It depends on the project or the task in question. If you have an intuition that you should go deeper but don't have enough time, then ask another developer to continue.

- How to deal with disagreement between author and reviewer?
  + Try to find objective evidence. Avoid religious issues. Ask a third person and let his be the decisive vote.

The code review workflow
------------------------

In a nutshell:

- The project advances forward through short-lived feature branches. This working style is a pre-requisite.

- You implement a specific change in a series of commits on a dedicated feature branch, and propose it to another developer for merging.

- The other developer reviews the changeset, and suggests improvements by leaving comments on specific lines, or on the changeset as a whole.

- Following the suggestions, you improve the changeset and push the new commits for another round of review.

- The review + corrections cycle is repeated until the reviewer is satisfied, and accepts the changeset by merging it into mainline.

Some crucial points:

- The practice of short-lived feature branches is a prerequisite. If the team doesn't follow this recommended working style, then code reviews may not be feasible.

- It's important to use a tool like GitHub, GitLab, or similar, where commenting on specific lines is easy, with a user-friendly interface.

- The review process should not hold up development. You can work on another branch while waiting for the review. This implies that developers are comfortable with working on multiple branches in parallel.

Some common misconceptions:

- Myth: *"we don't have time for code reviews"*. To understand the time cost of code reviews, you need to consider the long-term effects. Correcting bugs released in production can be extremely expensive. Code reviews are known to be an effective method to catch bugs early. They also help catching conceptual errors early, which may be extremely expensive to correct later. Code reviews can have many other positive effects that feed back to cost savings. Overall, code reviews save far more time than they cost.

- Myth: *"code review is just too hard to do, because it's impossible to review large changesets"*. The problem is not with the idea of code reviews, but with the changesets. Such changesets indicate incorrect use of feature branches. Keep changesets to a manageable size.

- Myth: *"doing code reviews slows down development, because the reviewer keeps the developer waiting"*. A developer shouldn't wait for the reviewer. The developer should know how to work on another branch while a another review is pending. Sometimes the other branch can be a continuation of the branch pending review.

- Myth: *"it's impossible to read diffs"*. It's not impossible. It may take a couple of days, but you can get used to it.

Is my team ready for code reviews?
----------------------------------

It's important to evaluate the readiness of your team first. Trying to push code reviews may fail spectacularly if the team is not yet following certain good practices:

- One commit == one logical change. Developers should have the good sense to commit improvements in small logical steps. Not too big, not too small. Through these steps, development can move forward in stable increments. Try to transition the team to this working style.

- Development advances forward through short-lived feature branches. Feature branches are the crucial unit of work in the workflow outlined above. Try to transition the team to this working style.

- Using distributed version control system. Without a distributed version control system, branch management might be too hard to be practical. Try to migrate your project and tools to any of the well-known distributed version control systems.

- Developers are open-minded, curious, and willing to learn from their peers. They can take their egos out of the equation, able to both give and take constructive criticism. Reading [Chapter 33 in Code Complete][cc2] might help achieving that.

Without the above, code reviews are unlikely to work well. Try to get the above issues out of the way first. Rest assured, these are all recommended and widely accepted practices that any project would benefit from, regardless of using code reviews or not. Be patient and calm, keep pushing, inching forward step by step.

Resources
---------

I was most inspired by these articles:

- [Code Reviews: Just Do It](http://blog.codinghorror.com/code-reviews-just-do-it/)
- [Pair Programming vs. Code Reviews](http://blog.codinghorror.com/pair-programming-vs-code-reviews/)
- [Code Complete 2: Chapter 28: Managing Construction][cc2]

To be continued...
------------------

More sections are coming soon with more details. For example, practical tips & tricks about our process in my teams.

*If you have some specific ideas or questions, feel free to [create an issue](https://github.com/janosgyerik/code-reviews-in-practice/issues) and I'll try to include it. [Pull requests](https://github.com/janosgyerik/code-reviews-in-practice) are also welcome!*

[cc2]: http://www.cc2e.com/
