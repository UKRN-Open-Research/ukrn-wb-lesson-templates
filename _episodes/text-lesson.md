---
title: Text Lesson # title of the episode
teaching: # time required to teach (minutes)
exercises: # time required for participants to do the activities (minutes)
duration: # duration for a break, not needed if teaching/exercises are present (minutes)
# summary of the episode content for displaying on the schedule page
summary: This template shows you how to use the various different special text boxes on offer.
questions: # list of questions we are trying to answer
objectives: # list of learning outcomes
keypoints: # list of take-home points
is-break:  # whether this episode is a break (has different presentation)
ukrn_wb_rules: # list of rules for the UKRN Workshop Builder tool
    - allow-multiple # when dragged into the schedule, create a new instance
    - remove-on-stash # when dragged into the stash, remove
day: 1
order: 1
---

## Markdown

The text in these episodes is written in markdown.
The **Workshop Builder** has a markdown editor, so it should not be _too difficult_ to edit the text to suit your requirements.

In addition to this, the website template we use has a variety of special highlighted sections that we use to draw attention to things.

### Lesson sections

The following lesson section tags are available:
* `{: .prereq}`
* `{: .callout}`
* `{: .challenge}`
* `{: .checklist}`
* `{: .discussion}`
* `{: .solution}`
* `{: .testimonial}`

Additionally, you can make extra copies of these tags, which are included automatically:
* `{: .objectives}`
* `{: .keypoints}`

Each tag is used in the same way, by including a section with a heading (`## heading`) in a block quote (`> quoted text`), and by having the tag `{: .tag-name}` on the line immediately following:

```markdown
> ## Section Title
> Here is the section body.
> This can be multiple lines long, and include images, code, etc.
>
> If you want paragraph breaks, make sure the quotation block continues
> by having the blank line start with >
>
> When you're finished, style the whole block by including the tag on the next line.
{: .tag-name}
```

### Examples

> ## `{: .prereq}` Tag
> This is a `{: .prereq}` tag block.
> This tag is usually used to tell participants what they need before they can complete a lesson.
{: .prereq}

> ## `{: .callout}` Tag
> This is a `{: .callout}` tag block.
> This tag is usually used to highlight something participants should take note of.
{: .callout}

> ## `{: .challenge}` Tag
> This is a `{: .challenge}` tag block.
> This tag is usually used to suggest an activity for participants to do, perhaps writing a bit of code or trying to complete an exercise.
{: .challenge}

> ## `{: .checklist}` Tag
> This is a `{: .checklist}` tag block.
> This tag is usually used to provide a list participants can use to make sure they don't forget an important step in a procedure.
{: .checklist}

> ## `{: .discussion}` Tag
> This is a `{: .discussion}` tag block.
> This tag is usually used to present a question for participants to discuss.
{: .discussion}

> ## `{: .solution}` Tag
> This is a `{: .solution}` tag block.
> This tag is usually used to present a solution to a problem.
> It is hidden by default, so that participants have to click to expand it and see the answer.
{: .solution}

```markdown
> Using a different heading level for the solution tag won't work.
> It has to be level 2.
```
{: .warning}

> ## `{: .testimonial}` Tag
> This is a `{: .testimonial}` tag block.
> This tag is usually used to present quotes from people who have previously participated in the course.
{: .testimonial}

### Advanced Tag Use

You can nest tags.
It's quite common to see `{: .solution}` tags nested inside `{: .challenge}` tags, for example.
They are done by stacking quote levels:
```markdown
> ## Question
> Why do you normally not need to use `{: .objectives}` and `{: .keypoints}` tags?
> > ## Answer
> > These tags are included automatically at the beginning and end of the lesson.
> {: .solution}
{: .challenge}
```

And it looks like:
> ## Question
> Why do you normally not need to use `{: .objectives}` and `{: .keypoints}` tags?
> > ## Answer
> > These tags are included automatically at the beginning and end of the lesson.
> {: .solution}
{: .challenge}

## HTML

You can also write in HTML.
The special `<kbd>` tag is available for use in neatly styling instructions like "press <kbd>Ctrl</kbd> + <kbd>Home</kbd>".
