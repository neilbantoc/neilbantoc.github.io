---
layout: post
title:  "Using Trello for Project Management"
thumbnail:
categories: project-management
---

This is just a quick tutorial (with pictures!) on how I imagine trello can be used to lead a design team and borrows a lot of concepts form the [agile process management method](https://en.wikipedia.org/wiki/Agile_management).

{% include jquery.html %}
{% include materialize.html %}

<br/>

---

<br/>

## List Setup

Before anything, the team needs to set up the Trello board with lists. The lists that are needed are as follows:

* **Brain dump:** literally a brain dump where team members can add cards for ideas that they have. A card can only be moved to the backlog if the team as a whole has agreed that the idea has value to the team.

* **Backlog:** a list of ideas that the team would want to pursue in the future. Though not required, subtasks may be added to the card (in the form of checklists) if the task is big enough to have multiple tasks.

* **Epics:** an idea is turned into an epic if the team has decided to work on the idea for the upcoming sprint. This will give the team a holistic view of the sprint and its goals.

* **To Do:** all tasks (and subtasks from epics) start here. The idea is to move all of the cards to a different list during the sprint with the goal of having it end up at the done list.

* **In Progress:** everytime a team member works on a task, there must be a card in this list corresponding to that task.

* **Blocked:** this list holds cards whose task is being blocked by something or someone, internal or external to the team.

* **Review:** for cards that need a verification by other team members before being moved to done.

* **Done:** tasks that have been completed. By the end of the sprint, all of the other lists should ideally be empty and all cards should be in this list.

<br />

---

<br/>

## Before A Sprint

<br />

### Prepping the Backlog

<img class="post-image-banner center materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/01-brain-dump.png"/>


Take cards from the brain dump list and move them to the backlog.


<br/>

<img class="post-image-large center materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/02-subtasks.png"/>

If an idea is big enough to have subtasks, add subtasks as lists. Start with a checklist labeled "Sprint 1" and if you feel that this task would take more than 1 sprint to complete, spread the subtasks across multiple checklists. You can always come back and change this.

<br/>

<img class="post-image-banner materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/03-backlog.png"/>

Move approved tasks to backlog. Ideas that the team wants to put work on for the upcoming sprint will become epics and will be transferred to the epics list. Any ideas for the future will stay in the backlog. It's also a good idea to arrange cards according to due date.

<br/>


### Prepping Epics and Tasks

<img class="post-image-large center materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/04-labels.png"/>

Labels can be used as a visual way of tagging tasks with their corresponding epic. Before the team moves tasks to the epic list, assign a label to that epic.

<br/>

<img class="post-image-banner materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/05-labels-overview.png"/>

You should have a clear overview of what the sprint aims to accomplish just by looking at the epics list. If a card from the backlog is small enough to be a standalone task, you don't need to assign a label to it. Just move it straight to the to do list.

<br/>

<img class="post-image-large center materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/06-convert-to-card.png"/>

Go through each subtask in an epic and convert them into task cards.

<br/>

<img class="post-image-banner materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/07-convert-to-card-overview.png"/>

The subtasks should look like this after being converted to a standalone task card.

<br/>

<img class="post-image-large center materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/08-relabel-converted-cards.png"/>

Before converting subtasks from another epic into task cards, it's a good idea to add an epic's label to the previously created task cards so that they don't get lost.

<br/>

<img class="post-image-banner materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/09-move-to-todo.png"/>

After adding labels to the task cards, you can now move them to the to do list.

<br/>

---

<br />

## Starting the Sprint

It's now time to start the sprint and work on tasks. For this part I'll show you how to use cards and lists to manage different kinds of tasks.

<br />

### Blocked tasks

Blocked tasks are tasks that have been started but are put on hold because of some dependency. Usually this dependency take a while to get resolved, so it is common to come back to blocked tasks at a much later time. Common tasks that fall under this category are emails, equipment orders, reimbursements, etc.

<img class="post-image-large center materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/10-assign-to-yourself.png"/>

As a general rule, team members must first assign the card to themselves before working on a task.

<br />

<img class="post-image-large center materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/11-make-comment.png"/>

It's also a good practice to write a comment before working on a task &mdash; something as simple as "I'm on it" so that regardless of where this card goes to, the team knows that it has been worked on by someone.

<br/>

<img class="post-image-banner center materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/12-move-to-in-progress.png"/>

The last thing to do before actually working on the task is to move the card to the in progress list. This way whenever a team member (especially the project manager) visits the board, they have a good idea on who's doing what and what tasks are still open. This also reduces the chance of two people working on the same task.

<br/>

<img class="post-image-large center materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/13-make-comment.png"/>

When you're done with the task, write another comment indicating that you're done.

<br/>

<img class="post-image-banner materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/14-move-to-blocked.png"/>

Since this task requires a response from the recepient, it can't be moved to the done list yet. Since it's not in progress anymore, and someone has already done work on it, it can't be moved to the in progress and to do lists respectively. This is where the blocked list comes in. Let's leave it there for now.

<br />

### Reviewed Tasks

Reviewed tasks are tasks that need the approval of another team member before being moved to done. Usual tasks that fall under this category are reports that need to be reviewed by team members, designs that need to be approved by the project manager, production code that needs to be tested by quality assurance, etc.

<img class="post-image-large center materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/15-make-comment.png"/>

As usual, before moving a task card to the in progress list, write a comment to mark that you've started on this task.

<br />

<img class="post-image-large center materialboxed responsive-img"
src="{{site.url}}/images/posts/main/trello/16-attach-document.png"/>

If the task requires team members to access an artefact such an online document, it's a good idea to add a link to that document as an attachment.

<br />

<img class="post-image-large center materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/17-attached-document.png"/>

This makes it easier for not only you but also your team members to review your work.

<br />

<img class="post-image-banner materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/18-in-progress.png"/>

Finally before starting work, move the task card to the in progress list.

<br />

<img class="post-image-banner materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/19-reviewers-blocked.png"/>

Of course, since you're working on a task that requires other team members to review your work, they may put their task card in the blocked list. But don't worry, we'll get back to that.

<br />

<img class="post-image-large center materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/20-done-with-document.png"/>

When you're done with your task and are ready for your team members do review your work, add a comment indicating your progress.

<br />

<img class="post-image-banner materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/21-move-to-review.png"/>

Move your task card to the review list so that other team members who are tasked to review your work can see that you are finished.

<br />

<img class="post-image-banner materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/22-move-reviewer-back-to-todo.png"/>

Oh and remember that guy who moved his task card to the blocked list because you were still working on your task? You can go ahead and move his review task card back to the to do list.

<br />

<img class="post-image-large center materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/23-inform-reviewer-of-document-completion.png"/>

Don't forget to be nice and tell them that you're done.

<br />

<img class="post-image-large center materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/24-review-done.png"/>

It's now the task of each reviewer to take a look at your work. If they have feedback regarding your work that you need to address, it's their job to add that in as a comment on their task card. If they don't have any feedback and are satisfied with your work, they can comment that in too.

<br />

<img class="post-image-banner materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/25-all-reviews-done.png"/>

Now, whenever you see someone done with their review, it's your job to open their task card to check if you need to make any changes. If that's the case, you would need to move that specific reviewer's review task card back to to do and move your task card back to in progress and start the cycle all over again.

<br />

<img class="post-image-large center materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/26-make-comment.png"/>

When everyone has finished reviewing your work, it's again time to add a comment...

<br />

<img class="post-image-banner materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/27-document-done.png"/>

...and finally mark your task as done.

<br />

## Detailed tasks

Detailed tasks are tasks that contain information that you might need to reference in the future. Tasks that have results that are of importance to the team such as an email to a client or an important data gathering exercise fall under this category.

<img class="post-image-large center materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/28-time-and-place.png"/>

The card description is a good place to put important information as it won't get buried in the comments section.

<br />

<img class="post-image-banner materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/29-email-details-new-task.png"/>

When you put a task card to the done list, it's also a good idea to mark it as having important information by adding a "\[Details\]" tag to the title.

<br />

<img class="post-image-large center materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/30-executive-summary.png"/>

If the information is too big to fit the description, a good strategy would be to have an executive summary along with a link to where the more comprehensive information can be accessed.

<br />

<img class="post-image-banner materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/31-add-details-tag.png"/>

Lastly, don't forget the "\[Details\]" tag.

<br />

---

<br />

## Post Sprint
<img class="post-image-banner materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/32-complete-sprint.png"/>

At the end of the sprint, all task cards should be on the done list.

<br/>

<img class="post-image-banner materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/33-archive-list.png"/>

To mark a successful sprint, add the dates that cover the whole sprint to the list title in preparation for archiving.

<br />

<img class="post-image-banner materialboxed responsive-img" src="{{site.url}}/images/posts/main/trello/34-archived-lists.png"/>

Of course, there's a way to revisit past sprints if the need arises.
