# OHBM SEA-SIG website

This is the repository for the OHBM Sustainability and Environment Action Special Interest Group (SEA-SIG).
It is built with the [Jekyll static website generator](https://jekyllrb.com/) and uses the [Minimal Mistakes theme](https://mmistakes.github.io/minimal-mistakes/). Most of the website content is written using the Markdown syntax.

## How to update the website (general)

### Updating directly through GitHub interface

Existing pages can be updated through the browser by using the [github.dev editor](https://docs.github.com/en/codespaces/the-githubdev-web-based-editor), which can be launched using the [`.` keyboard shortcut](https://docs.github.com/en/get-started/accessibility/keyboard-shortcuts#source-code-editing). This will open a Visual Studio Code-like interface, where you should:

1. Create a new branch by clicking on the button on the bottom left side of the editor (the default branch is called `main`).
2. Make desired changes to the repository (i.e. create/edit files).
3. Go to the "Source control" tab on the left sidebar, stage changes and commit/push.
4. Open a pull request (PR) to merge the changes from your branch back to the `main` branch (see [here](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request) for more instructions).

In the new pull request, there will be a link to a preview of the website with your changes.
Write a meaningful PR title and verify that the website looks as expected, then you can merge the PR.
GitHub pages will then auto-update the actual website (may take a few minutes).

### Local setup

It is also possible to set up a development environment locally instead of only making changes on the browser.
This requires more installation steps but has the benefit of being able to serve the website locally, which can lead to faster visualization of changes.

If you are on Windows, consider using the browser method instead of a local setup because the Windows command line is trickier to work with.

#### Prerequisite

You need to be given "write" access to the repository.
Ask other committee members to add you if needed.

#### Required software
- Git: most likely you already have this installed (try running `git --version` in a Terminal window). If not, see instructions [here](https://git-scm.com/install/).
- Ruby: follow instructions specific to your operating system on [this page](https://www.ruby-lang.org/en/documentation/installation/). The website is built with Ruby 3.1.

#### Steps

If this is your first time using Git on your computer, follow these steps to set up your `GitHub` account (you will only need to do this once):
1. Configure Git following instructions [here](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup). Make sure to use the email associated with your GitHub account.
2. Create and add an SSH key to your GitHub account (GitHub no longer allows the use of passwords for authentication through the command line). See instructions [here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) and [here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).

Clone the repository:

```
git clone git@github.com:ohbmenvironment/website.git
```

Create a new branch and switch to it:

```
git checkout -b your_username/branch_name
```

To serve the website locally:

```
bundle exec jekyll serve --incremental
```

This should eventually print out something like this:

```
Server address: http://127.0.0.1:4000
```

Open a web browser and go to this URL to see the rendered website. The website should be rebuilt automatically whenever any files are changed (except for `_config.yml`).

## How to add a Team page

Members of the active committee are shown near the bottom of the [home page](https://ohbm-environment.org/) and on a dedicated ["Team"](https://ohbm-environment.org/team/) page. 

To add the team page for a new year:
1. In `_data/teams.yml`
    1. Change the key for the previous year's team entry:
        ```yaml
        latest: &latest
        ```
        becomes something like this (use appropriate years)
        ```yaml
        20XX-20YY:
        ```
    2. Copy, uncomment, and fill in the template entry. It should be the only one with `latest: &latest`
2. In `_data/authors.yml`
    1. Add an entry for anyone who is not already in this document. Otherwise, their avatar will be the SEA-SIG logo.
3. In the `_pages/teams` directory, make a new file for the previous year's team. You can copy the `2024-2025.md` file and rename it with the appropriate years `20XX-20YY.md` (see 1.1), and update all the years in the contents of that file.
4. In `_data/navigation.yml`, scroll down to the `teams` section and add an entry under `Current` for the previous year's team:
    ```yaml
    - title: 20XX-20YY
      url: /team-20XX-20YY/
    ```
5. Check that the changes have been made correctly:
    1. On the home page, the "Our team" section should have the current team.
    2. On the Team page, the current team should be displayed, and there should be a new sub-page for the previous team.

## How to add a blog post

Blog posts will appear in the [News](https://ohbm-environment.org/blog/) page. The most recent posts will also appear in the "Latest news" section of the [home page](https://ohbm-environment.org/).

To add a new blog post (for example announcing elections):
1. Make a copy of `_posts/template.md` in the same directory.
2. Rename that file following this format: `YYYY-MM-DD-my-great-title.md`. Note that the `my-great-title` part must be unique since it determines the page's URL.
3. Update the front matter (block at the top of this file) to have a new title.
4. Optionally set tag(s) in the front matter. Tags allow for grouping of posts in the [Tags page](https://ohbm-environment.org/tags/).

## How to add an event page

Events appear as sub-pages under the main [Events](https://ohbm-environment.org/events/) page.

To add a new event page:
1. Make a copy of `_pages/events/template.md` in the same directory.
2. Rename that file.
3. Update the front matter (block at the top of this file) to have a new title and permalink.
4. Add the page to the `_data/navigation.yml` file's `events` section. The `url` field must match the file's permalink.
    1. If the event is for a new year, create a new section for the year.
    2. Otherwise, add it as a child of an existing section.
