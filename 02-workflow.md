# Workflow

## Tools
- [Unfuddle](https://mindmixer.unfuddle.com)
- [Git](http://git-scm.com/)
- Slack + Jenkins (Friendly neighborhood build bot)

## Process
Not a waterfall workflow. Not an agile workflow. Just the workflow that works for us.

**Design & discussion**

_Most_ things start via a discussion that was prompted by a discussion from a customer or is a result of a discussion with a customer. Some dreaming happens here, some dream crushing happens here, generally ideas and comps start flowing out of this.

This part of process usually includes a technical person being involved to talk about feasibility, work required and to push the technical questions about interaction and changes to existing functionality.

**Ticketing & "pointing"**

Once we have an idea of what the new feature, revision of a feature is going to include we can start writing out the technical requirements for it in Unfuddle tickets. Large items will likely be broken into several small ones.

Happening concurrently-ish should be some level of rough estimation (features or large revisions only) that will help us understand what the amount of work required is and what type of work is required since not all engineers have the same skill sets.

**Branches**

Once the requirements and specifics have been written up in a ticket, the ticket should be marked as accepted by the individual who is working on it. A branch should be created using the following "template" `[TICKET NUMBER]-[2-3 WORD DESCRIPTION]`. Short sweet to the point. Ticket numbers help make sure names don't collide, and the words help identify branch focus.

**QA**

Once all or most of the requirements have been satisfied for a given ticket, the branch should be merged into the `qa` branch. Pushing a merged branch will trigger unit and integration tests. You should run all tests locally before pushing (if not all, at least language specific).

Once you have pushed your branch you can follow along with the notifications in the organization Slack channels (#developers for errors, #jenkins for progress). You should give your changes a quick review in `qa` on https://qammx.com and then mark the ticket(s) as resolved and reassign to Ryan F.

NOTE: Change the ticket status before who it is assigned to (it removes who it is assigned if you change status second)

**Ready to deploy**

If there are any issues, continue the cycle of fixing things locally, merging to `qa` and sending back to Ryan.

When Ryan gives it the green light, your branch (not the `qa` branch) can be merged to `stage`. Once you have done that, do a quick check once the build finishes and pass back to Ryan so he can monitor what is in stage and ready for production.

**Release**

We standardly release at end of day Monday every week. Occasionally a hotfix may go out to address critical issues (usually in the evenings again). Follow the production channel for build schedules and notes about what is/was included.

You can also check out [Product Updates](https://mysidewalk.readme.io/docs/product-updates) which is a client facing set of notes.


#### Links
- Next up: [Architecture](03-architecture.md)
- Previously: [Setup](01-setup.md)
