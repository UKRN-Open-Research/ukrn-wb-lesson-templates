---
layout: page
title: Background and Design
permalink: /design/
---

## Project structure

This template is a skeleton for creating workshop websites.
It is used by the [UKRN Workshop Builder](/404.html) to produce repositories containing complete, bespoke workshop websites which are owned and controlled by the individual workshop hosts.
The UKRN offers train-the-trainer instruction taking people through the creation of their workshop using the Builder tool.

We can understand how to customise websites created from this template by understanding how the Builder tool does its job.
The overarching framework in which we work is as follows:
* **Topics** are areas of Open Research practice for which the UKRN has developed enough expertise and resources to allow people to design and deliver **workshops** teaching people the skills they need to implement those practices in their own work.
    Topics will usually be accompanied by a [UKRN Primer](https://ukrn.org/primers) and other central resources.
    * Examples include _Open Code_ and _Preregistration_.
* **Workshops** are taught classes which equip attendees with the practical skills necessary to embed an Open Research **topic** in their workflow.
    Each workshop is designed and delivered by a researcher and covers the practical implementation of a topic for researchers _in a particular area_.
    Each workshop is supported by a website which contains all of the resources required to participate.
    The topic of the workshop is delivered via a series of **lessons**.
* **Lessons** are collections of **episodes** and form modular blocks of content on specific skills.
    Lessons are only used for collecting episodes together - they don't actually show up as discrete entities in the final workshops.
    * Examples for lessons in the _Open Code_ topic might be: _Introducing Open Code_, _Version Control_, _Getting a DOI for Code_.
* **Episodes** are indivisible chunks of content.
    Episodes can be interspersed with breaks.
    * The _Version Control_ lesson might include episodes on _Introducing Git_, _Publishing on GitHub_, and _Semantic Versioning_.

### How the Builder tool works

The Builder tool takes the following steps:
1. Create a repository in the instructor's GitHub account from this template.
2. Trim the template down to remove references to unused topics, implement any custom changes to the introductory or general-purpose pages, and write the schedule from the list of selected episodes.
3. Import selected Lessons from existing GitHub repositories
4. Customise the imported Lessons
    1. Remove unused episodes
    2. Prepend the repository owner name to the resources and their references to avoid conflicts
    3. Apply any customisation to episodes

All of these steps can be reproduced manually.
Care should be taken when implementing episodes from different sources that they do not have conflicts over files in shared folders (e.g. that you don't have two different episodes trying to create `fig/example01.png`). Make sure to update references to these resources as well as the names of the resources themselves!

### Customising Lessons

Lessons are stored as GitHub repositories based on this template, but can be barebones because only the content is imported.
Lessons should have at least one item in the `_episodes` or `_episodes_rmd` directory, and may additionally have resources in other directories.
Lessons are imported into workshop websites and built and served as Jekyll pages as described below.

To make your lesson appear automatically as an option in the appropriate workshop, ensure the GitHub repository has the appropriate tags. All lessons need the `ukrn-open-research` tag, and at least one topic tag (e.g. `open-code`) specifying which workshops the lesson will work with.

#### Gotchas

The Lessons require shared files which are shared with this basic template (e.g. layouts `_layouts`), and would therefore be duplicated for each lesson.
To avoid this issue, the Builder tool checks whether the file to be copied is exactly the same as the version in the template, and skips it if so.
If it is different, the user and repository are prepended to the filename, so `_layouts/base.html` becomes `_layouts/github-user_example-lesson_base.html` and references to `_layouts/base.html` in the lesson files are updated accordingly.

## Working with Git and GitHub

There are a few things you need to know in order to understand why we
do things the way we do.  Some of them are specific to GitHub, rather
than Git itself.

1.  Git uses the term "clone" to mean "a copy of a repository".
    GitHub uses the term "fork" to mean, "a copy of a GitHub-hosted
    repo that is also hosted on GitHub", and the term "clone" to mean
    "a copy of a GitHub-hosted repo that's located on someone else's
    machine".  In both cases, the duplicate has a remote called
    `origin` that points to the original repo; other remotes can be
    added manually.

2.  A user on GitHub can only have one fork of a particular repo.
    This is a problem for us because an instructor may be involved in
    several workshops, each of which has its own website repo. To avoid
    this issue, we use the template functionality (you could also use the
    `import.github.com` functionality).

3.  If a repository has a file called `README.md` in its root
    directory, GitHub displays the contents of that file on the
    repository's home page.

4.  If a repository has a branch called `gh-pages` (which stands for
    "GitHub pages"), then GitHub uses the HTML and Markdown files in
    that branch to create a website for the repository.  If the
    repository's URL is `http://github.com/darwin/finches`, the URL
    for the website is `http://darwin.github.io/finches`.

5.  If an HTML or Markdown file has a header consisting of three
    dashes, some data about the page, and three more dashes:

    ```yaml
    ---
    key: value
    other_key: other_value
    ---
    content of the page
    ```

    then GitHub doesn't just copy the file over verbatim.  Instead, it
    runs the file through a translator called [Jekyll][jekyll] that
    looks for specially-formatted commands embedded in the file and
    uses them to fill in the page.

6.  Commands can be embedded in the body of a page.  One is
    `{% raw %}{% include something.html %}{% endraw %}`, which tells
    Jekyll to copy the contents of `something.html` into the file
    being translated; this is used to create standard headers and
    footers for pages.  Another is `{% raw %}{{variable}}{% endraw %}`: when Jekyll sees
    this, it replaces it with the value of `variable`.  This is used
    to insert things like a contact email address and the URL for our
    Twitter account.

7.  Jekyll gets variables from two places: a file called `_config.yml`
    located in the repo's root directory, and the header of each
    individual page.  Variables from `_config.yml` are put in an
    object called `site`, and referred to as `site.variable`, so that
    (for example) `{% raw %}{{site.swc_site}}{% endraw %}` in a page is replaced by the URL
    of the main Software Carpentry web site ({{site.swc_site}}).  Variables from the
    page's header are put in an object called `page`, and referred to
    as `page.variable`, so if a page's header defines a variable
    called `venue`, `{% raw %}{{page.venue}}{% endraw %}` is replaced by "Euphoric State
    University" (or whatever value the variable has).

8.  If a page uses `{% raw %}{% include something.html %}{% endraw %}`
    to include a snippet of HTML, Jekyll looks in a directory called
    `_includes` to find `something.html`.  It always looks there, and
    nowhere else, so anything we want people to be able to include in
    their pages has to be stored in `_includes`.

9.  A repository can have another special directory called `_layouts`.
    If a page like `index.html` has a variable called `layout`, and
    that variable's value is `standard.html`, Jekyll loads the file
    `_layouts/standard.html` and copies the content of `index.html`
    into it, then expands the result.  This is used to give the pages
    in a site a uniform appearance.
    We have created two layouts for workshop pages:

    * `workshop.html` is used for workshops' home pages, and is the
      layout for the `index.html` page in your repo's root directory.
      That `index.html` page's header must define several variables as
      specified in the the customization instructions in order for
      your workshop to be included in our main website.

    * `page.html` is used for any other pages you want to create.
      **Note:** if you create extra pages, you *must* edit the values
      in the top section of `_config.yml` as described in
      [the lesson template documentation]({{ site.example_site }}).

## Extra Directories

This workshop template shares resources with the template used for
Carpentry lessons.  As a result, your workshop website's repository
contains directories that most workshops don't need, but which can be
used to store extra material when necessary:

*   `_extras/`: extra pages (like this one).
*   `_episodes/`: lesson episodes (which workshops usually don't have).
*   `_episodes_rmd/`: R Markdown lesson episodes (if any).
*   `code/`: for code samples.
*   `data/`: for data files.
*   `fig/`: for figures and other images.
*   `files/`: for miscellaneous files.

For more information on these, please see [the documentation for the
lesson template]({{ site.example_site }}).

[jekyll]: https://jekyllrb.com/
