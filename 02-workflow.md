# Workflow
A high level overview or the process a feature progresses through including some developer specific steps.

## Tools
- [Unfuddle](https://mindmixer.unfuddle.com/projects/2083)
- [Git](http://git-scm.com/)
- Slack ([web](https://slack.com) or [app](https://itunes.apple.com/us/app/slack/id803453959?mt=12))

## Feature workflow
Not a waterfall workflow. Not an agile workflow. Just the workflow that works for us.

**Design & discussion**

_Most_ things start via a discussion that was prompted by a discussion from a customer or is a result of a discussion with a customer. Some dreaming happens here, some dream crushing happens here, generally ideas and comps start flowing out of this.

This part of process usually includes a technical person being involved to talk about feasibility, work required and to push the technical questions about interaction and changes to existing functionality.

**Ticketing & "pointing"**

Once we have an idea of what the new feature, revision of a feature is going to include we can start writing out the technical requirements for it in Unfuddle tickets. Large items will likely be broken into several small ones.

Happening concurrently-ish should be some level of rough estimation (features or large revisions only) that will help us understand what the amount of work required is and what type of work is required since not all engineers have the same skill sets.

**Branches**

Once the requirements and specifics have been written up in a ticket, the ticket should be marked as accepted by the individual who is working on it. A branch should be created using the following "template" `[TICKET NUMBER]-[2-3 WORD DESCRIPTION]`, e.g. `1234-my-ticket-name`. Short sweet to the point. Ticket numbers help make sure names don't collide, and the words help identify branch focus.

**QA**

Once all or most of the requirements have been satisfied for a given ticket, the branch should be merged into the `qa` branch. Pushing a merged branch will trigger unit and integration tests. You should run all tests locally before pushing (if not all, at least language specific).

Once you have pushed your branch you can follow along with the notifications in the organization Slack channels (#developers for errors, #jenkins for progress). You should give your changes a quick review in `qa` on https://qammx.com and then mark the ticket(s) as resolved and reassign to QA.

NOTE: Change the ticket status before who it is assigned to (it removes who it is assigned if you change status second)

**Ready to deploy**

If there are any issues, continue the cycle of fixing things locally, merging to `qa` and sending back to QA.

When QA gives it the green light, your branch (not the `qa` branch) can be merged to `stage`. Once you have done that, do a quick check once the build finishes and pass back to QA so he can monitor what is in stage and ready for production.

**Release**

We standardly release at end of day Monday every week. Occasionally a hotfix may go out to address critical issues (usually in the evenings again). Follow the production channel for build schedules and notes about what is/was included.

You can also check out [Product Updates](https://mysidewalk.readme.io/docs/product-updates) which is a client facing set of notes.


## Git Workflow
1. Update from master `git checkout master` and to be safe `git pull`
2. Create a local branch to work from `git checkout -b [BRANCH NAME]`
3. Commit against your local branch `git add .` `git commit -m "#[TICKET NUMBER] - [SHORT MESSAGE]"`
4. Push your branch remotely `git push -u origin [BRANCH NAME]`
5. Merge to QA `git checkout qa`, to be sure your are up to date `git pull`, then merge `git merge [BRANCH NAME]`, resolve any conflicts their might be and then `git push`


#### Links
- Next up: [Structure](03-structure.md)
- Previously: [Setup](01-setup.md)
