---
layout: workshop      # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
---

{% comment %}
Each of the sections below can be found in an individual markdown file.
This makes it easier for people to edit the contents in the UKRN Workshop Builder.
{% endcomment %}

{% comment %}
HEADER

Edit the values in the block above to be appropriate for your workshop.
If the value is not 'true', 'false', 'null', or a number, please use
double quotation marks around the value, unless specified otherwise.
And run 'make workshop-check' *before* committing to make sure that changes are good.
{% endcomment %}

{% if site.eventbrite %}
**Some adblockers block the registration window. If you do not see the
  registration box below, please check your adblocker settings.**

<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{site.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="280px"
  scrolling="auto">
</iframe>
{% endif %}


<h2 id="general">General Information</h2>

{% if site.topic == "open-data" %}
{% include intro/topic-intros/open-data.md %}
{% elsif site.topic == "open-code" %}
{% include intro/topic-intros/open-code.md %}
{% elsif site.topic == "open-access" %}
{% include intro/topic-intros/open-access.md %}
{% elsif site.topic == "preregistration" %}
{% include intro/topic-intros/preregistration.md %}
{% elsif site.topic == "preprints" %}
{% include intro/topic-intros/preprints.md %}
{% else %}
{% include intro/topic-intros/unknown-topic.md %}
{% endif %}

{% comment %}
LOCATION

This block displays the address and links to maps showing directions
if the latitude and longitude of the workshop have been set.  You
can use https://itouchmap.com/latlong.html to find the lat/long of an
address.
{% endcomment %}
{% assign begin_address = site.address | slice: 0, 4 | downcase  %}
{% if site.address == "online" %}
{% assign online = "true_private" %}
{% elsif begin_address contains "http" %}
{% assign online = "true_public" %}
{% else %}
{% assign online = "false" %}
{% endif %}
{% if site.latitude and site.longitude and online == "false" %}
<p id="where">
  <strong>Where:</strong>
  {{site.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{site.latitude}}&mlon={{site.longitude}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{site.latitude}},{{site.longitude}}">Google Maps</a>.
</p>
{% elsif online == "true_public" %}
<p id="where">
  <strong>Where:</strong>
  online at <a href="{{site.address}}">{{site.address}}</a>.
  If you need a password or other information to access the training,
  the instructor will pass it on to you before the workshop.
</p>
{% elsif online == "true_private" %}
<p id="where">
  <strong>Where:</strong> This training will take place online.
  The instructors will provide you with the information you will need to connect to this meeting.
</p>
{% endif %}

{% comment %}
DATE

This block displays the date and links to Google Calendar.
{% endcomment %}
{% if site.start_date %}
<p id="when">
  <strong>When:</strong>
  {{site.start_date | date: "%y %m %d - %H:%M" }}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %} Include the extra optional files listed in optional_intro_sections {% endcomment %}
{% for X in site.optional_intro_sections %}
{% include intro/{{ X }}.md %}
{% endfor %}

{% comment %}
CONTACT EMAIL ADDRESS

Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contact:</strong>
  Please email
  {% if site.instructor_emails %}
  {% for email in site.instructor_emails %}
  {% if forloop.last and site.instructor_emails.size > 1 %}
  or
  {% else %}
  {% unless forloop.first %}
  ,
  {% endunless %}
  {% endif %}
  <a href='mailto:{{email}}'>{{email}}</a>
  {% endfor %}
  {% else %}
  to-be-announced
  {% endif %}
  for more information.
</p>

<hr/>

{% comment%}
CODE OF CONDUCT
{% endcomment %}
<h2 id="code-of-conduct">Code of Conduct</h2>

<p>
Everyone who participates in Carpentries activities is required to conform to the <a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">Code of Conduct</a>. This document also outlines how to report an incident if needed.
</p>

<p class="text-center">
  <a href="https://goo.gl/forms/KoUfO53Za3apOuOK2">
    <button type="button" class="btn btn-info">Report a Code of Conduct Incident</button>
  </a>
</p>
<hr/>


{% comment %}
Collaborative Notes

If you want to use an Etherpad, go to

https://pad.carpentries.org/YYYY-MM-DD-site

where 'YYYY-MM-DD-site' is the identifier for your workshop,
e.g., '2015-06-10-esu'.

Note we also have a CodiMD (the open-source version of HackMD)
available at https://codimd.carpentries.org
{% endcomment %}
{% if site.collaborative_notes %}
<h2 id="collaborative_notes">Collaborative Notes</h2>

<p>
We will use this <a href="{{ site.collaborative_notes }}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
<hr/>
{% endif %}

{% assign pre = site.pre_survey | size %}
{% assign post = site.post_survey | size %}
{% if pre > 0 or post > 0 %}
<h2 id="surveys">Surveys</h2>
{% if pre > 0 and post > 0 %}
<p>Please be sure to complete these surveys before and after the workshop.</p>
<p><a href="{{ site.pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% else %}
<p>Please be sure to complete this survey {% if pre > 0 %}before{% else %}after{% endif %} the workshop.</p>
{% if pre > 0 %}<p><a href="{{ site.pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
{% else %}<p><a href="{{ site.post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>{% endif %}
{% endif %}
<hr/>
{% endif %}

{% comment %}
SCHEDULE

Show the workshop's schedule.

The schedule is automatically generated from the lessons in `./_episodes` and `./episodes_rmd`, which are in turn produced by the generator tool.
{% endcomment %}

<h2 id="schedule">Schedule</h2>

{% include schedule.html %}

<hr/>


{% comment %}
SETUP

The setup page simply loops through the entries in site.setup_files and links them with available installation guides from _includes/install_instructions
{% endcomment %}
{% if site.setup_files %}
{% comment %}Sum up the times taken to install the software{% endcomment %}
{% assign setup_time = 0 %}
{% for X in site.setup_files %}
{% assign setup_time = setup_time | plus: X.exercise %}
{% endfor %}
<h2 id="setup">Setup</h2>

To participate in a {{ site.title | capitalize }}
workshop,
you will need access to the software described below.
Installing this software will take around {{ setup_time }} minutes.
In addition, you will need an up-to-date web browser.

The Carpentries maintain a list of common issues that occur during installation as a reference for instructors
that may be useful on the
[Configuration Problems and Solutions wiki](https://github.com/carpentries/workshop-template/wiki/Configuration-Problems-and-Solutions).

{% include intro/_participant-setup.html %}
{% endif %}
