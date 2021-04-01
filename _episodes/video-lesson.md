---
title: Video Lesson # title of the episode
teaching: # time required to teach (minutes)
exercises: # time required for participants to do the activities (minutes)
duration: # duration for a break, not needed if teaching/exercises are present (minutes)
# summary of the episode content for displaying on the schedule page
summary: This template shows you how to include embedded videos in your lessons.
questions: # list of questions we are trying to answer
objectives: # list of learning outcomes
keypoints: # list of take-home points
is-break:  # whether this episode is a break (has different presentation)
ukrn_wb_rules: # list of rules for the UKRN Workshop Builder tool
    - allow-multiple # when dragged into the schedule, create a new instance
    - remove-on-stash # when dragged into the stash, remove
day: 1
order: 5
---

## Markdown

### Embedding Videos

You can copy the embedding code from the video's host website and simply paste it into the document.

```html
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/7jr0p94fEEg" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
```
{: .source}

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/7jr0p94fEEg" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen class="output"></iframe>

#### Finding the Embed Code

Here is a step-by-step guide for YouTube, but other video providers use a similar approach.

1. Go to the video page [https://www.youtube.com/watch?v=7jr0p94fEEg](https://www.youtube.com/watch?v=7jr0p94fEEg)
2. Click the `Share` button
3. Select `Embed`
4. Customise the embedding options as necessary, and copy the produced HTML code.
5. Paste the HTML code directly into the lesson where you want the video.

### Embedding Audio

The approach for audio is similar to video - find the embed code and paste it into the document:

<iframe width="100%" height="166" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/792848608&color=%23ff5500&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe><div style="font-size: 10px; color: #cccccc;line-break: anywhere;word-break: normal;overflow: hidden;white-space: nowrap;text-overflow: ellipsis; font-family: Interstate,Lucida Grande,Lucida Sans Unicode,Lucida Sans,Garuda,Verdana,Tahoma,sans-serif;font-weight: 100;"><a href="https://soundcloud.com/reproducibilitea" title="ReproducibiliTea Podcast" target="_blank" style="color: #cccccc; text-decoration: none;">ReproducibiliTea Podcast</a> · <a href="https://soundcloud.com/reproducibilitea/episode-32-crisis-research-with-anne-scheel" title="Episode 32 - Crisis Research With Anne Scheel" target="_blank" style="color: #cccccc; text-decoration: none;">Episode 32 - Crisis Research With Anne Scheel</a></div>

### Advanced Embedding

It is possible to embed content within e.g. the `{: .solution}` section tags:

> ## UKRN Testimonial
> <iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/7jr0p94fEEg" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen class="output"></iframe>
{: .testimonial}

> ## Hidden video
> <iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/7jr0p94fEEg" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen class="output"></iframe>
{: .solution}
