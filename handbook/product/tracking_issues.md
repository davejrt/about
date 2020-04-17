# Tracking issues

## Table of contents

1. [What is a Tracking issue?](#what-is-a-tracking-issue)
1. [Creating a Tracking issue](#creating-a-tracking-issue)
1. [Populating and maintaining a Tracking issue](#populating-and-maintaining-a-tracking-issue)
1. [Planning a milestone with a Tracking issue](#planning-a-milestone-with-a-tracking-issue)
1. [Using a Tracking issue for progress check-ins](#using-a-tracking-issue-for-progress-check-ins)
1. [Contributing to the Tracking issue tool](#contributing-to-the-tracking-issue-tool)

## What is a Tracking issue?

A Tracking issue is a GitHub issue that captures the planned and on-going work of a milestone — from larger roadmap items to smaller tasks and bug fixes and everything in between. This artifact is a medium used for planning, progress check-ins and stakeholder communication.

You can take a look at [examples of open tracking issues](https://github.com/sourcegraph/sourcegraph/issues?q=is%3Aopen+is%3Aissue+label%3Atracking) to get a sense of what they look like.

## Creating a Tracking issue

During the last week of a milestone, each team should create a Tracking issue for a next milestone by doing the following:

1. Create a new GitHub issue with the [Tracking issue template](https://github.com/sourcegraph/sourcegraph/issues/new?assignees=&labels=tracking&template=tracking_issue.md&title=%24TEAM%3A+%24MILESTONE+Tracking+issue).
1. Give it the **"$TEAM: $MILESTONE Tracking Issue"** title.
1. Assign it to the right milestone, creating such milestone if it doesn't yet exist.
1. Ensure both the **team/$TEAM** and **tracking** labels are set.

## Populating and maintaining a Tracking issue

A Tracking issue is populated and kept up to date with the GitHub issues and pull requests of its team as they are opened, closed, merged, etc.

Those issues and pull requests must have the **team/$TEAM** label and be in the same milestone as the tracking issue.

Open tracking issues are maintained automatically by the [tracking-issue tool](#contributing-to-the-tracking-issue-tool) which [runs in response to GitHub issue events](https://github.com/sourcegraph/sourcegraph/blob/master/.github/workflows/tracking-issue.yml#L6) happening in [https://github.com/sourcegraph/sourcegraph](https://github.com/sourcegraph/sourcegraph).

### Rendering

There are a number of ways to affect how the workload section of a tracking issue is rendered.

#### Labels

These are the labels you can use to refine how each work item in the tracking issue looks. You can add any number of these labels to an issue or pull request.

- **roadmap**: Issues related to work planned in our roadmap will be displayed the 🛠 emoji.
- **customer**: Important issues reported or desired by a customer will be displayed with the 👩 emoji. If the issue body includes a Hubspot link to the customer's profile, then the emoji will be linked to it. If you have the Sourcegraph extension installed with *Experimental link previews* enabled and authorized the Hubspot's domain for it, then the customer's name will show up next to the emoji.
- **spike**: Time boxed investigation tasks meant to facilitate more granular planning will be displayed with the 🕵️ emoji.
- **bug**: An error, flaw or fault that produces an incorrect or unexpected result, or behavior. These will be displayed with the 🐛 emoji.
- **debt**: Technical debt issues will be displayed with the 🧶emoji.
- **estimate/$Nd**: A rough day level estimate of the task will be displayed alongside the emojis and summed up to a total workload in days that is displayed next to the teammate's GitHub handle.

#### Pull Requests

Pull requests, if labeled and milestoned correctly, will show up in their author's workload. They can be easily spotted by looking for the <img src="https://github.githubassets.com/images/icons/emoji/shipit.png" height=20 width=20/> emoji. Additionally, if a pull request's body contains the issue number (i.e. #1234) that it relates to, the it will show up under that issue as a nested list item.

## Planning a milestone with a Tracking issue

## Using a Tracking issue for progress check-ins

## Contributing to the Tracking issue tool

## References

These category labels have the following meaning:

- **roadmap**: Issues related to work planned in our roadmap.
- **customer**: Important issues reported or desired by a customer.
- **spike**: Time boxed investigation meant to facilitate more granular planning.
- **bug**: An error, flaw or fault that produces an incorrect or unexpected result, or behavior.
- **debt**: Technical debt.

After this triage process, the team manager puts together a draft tracking issue containing this initial proposed work for the iteration. Most of the body of the tracking issue is [automatically generated](https://github.com/sourcegraph/sourcegraph/blob/master/internal/cmd/tracking-issue/main.go) from  properly labeled GitHub issues — they're in the right milestone, have the **team/core-services** label, are estimated *and* categorized.

This means teammates *need not check off, remove or add issues* to the task list in the tracking issue — that is done automatically throughout the planning process and throughout the iteration itself.

When the draft tracking issue is published, everyone on the team is asked to:

1. Update their availability for the month in the Not Working calendar and write down the number of working days in the designated section in the tracking issue.
1. Propose other work for the iteration in a comment in the tracking issue. Each proposed work item must be captured in a separate GitHub issue that is assigned to the right owner, estimated, and categorized as per the above mentioned requirements.

All planned work items are meant to be finished in the iteration. If this doesn't happen, it is either due to unknown unknowns or lack of estimating accuracy. While we cannot work on the former, we can on the latter — over time, we aim to estimate better.

Teammates should be conservative by picking an estimate somewhere in between the median case and worst case scenarios, not best case. The higher someone's level of experience with the issue being estimated as well as estimation itself, the closer the estimate can be to the best case scenario. The opposite is also true.

Despite estimation having a bad reputation in some circles, we find it valuable to:

1. Prevent any single team member having more work assigned than available work days.
1. Ensure everyone has enough slack in the iteration (~20% of their time). This is to account for unexpected things, to foster creativity and to prevent burn-out.
1. Remind the person working on the issue to avoid time sinks or approaches that would miss the estimate.

Roadmap items may take more than an iteration to implement. As such please link to an issue which is scoped to this iteration. If it isn't clear how to break down a larger item in a scope increment, a **spike** of one or two days could be appropriate to determine such scope and then create the resulting issues for the iteration — it's fine to update the tracking issue with the results of a spike during the iteration.

After the internal discussion of the team's work plan for the iteration ends, the tracking issue is ready to be *reviewed* by external stake-holders. The team manager asks for +1s from the relevant [Product Manager](../../product/roles.md#product-manager) and the [VP of Engineering](../roles.md#vp-engineering).

After adjusting the work plan according to their feedback (if necessary), the team manager marks the tracking issue as approved in its "Status" section and labels all planned issues with a `planned/$MILESTONE` label.

Because this label allows the `tracking-issue` tool to keep track of issues that are taken out of the milestone during the iteration, it should not be removed from those issues when that happens.
