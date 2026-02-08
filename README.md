# OHBM SEA-SIG website

This is the repository for the OHBM Sustainability and Environment Action Special Interest Group (SEA-SIG).
It is built with the [Jekyll static website generator](https://jekyllrb.com/) and uses the [Minimal Mistakes theme](https://mmistakes.github.io/minimal-mistakes/). Most of the website content is written using the Markdown syntax.

## Updating directly through GitHub interface

Existing pages can be updated through the browser by using the [github.dev editor](https://docs.github.com/en/codespaces/the-githubdev-web-based-editor), which can be launched using the [`.` keyboard shortcut](https://docs.github.com/en/get-started/accessibility/keyboard-shortcuts#source-code-editing). This will open a Visual Studio Code-like interface, where you should:

1. Create a new branch by clicking on the button on the bottom left side of the editor (the default branch is called `main`).
2. Make desired changes to the repository (i.e. create/edit files).
3. Go to the "Source control" tab on the left sidebar, stage changes and commit/push.
4. Open a pull request (PR) to merge the changes from your branch back to the `main` branch (see [here](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request) for more instructions).

In the new pull request, there will be a link to a preview of the website with your changes.
Write a meaningful PR title and verify that the website looks as expected, then you can merge the PR.
GitHub pages will then auto-update the actual website (may take a few minutes).

## Local setup

It is also possible to set up a development environment locally instead of only making changes on the browser.
This requires more installation steps but has the benefit of being able to serve the website locally, which can lead to faster visualization of changes.

If you are on Windows, consider using the browser method instead of a local setup because the Windows command line is trickier to work with.

### Prerequisite

You need to be given "write" access to the repository.
Ask other committee members to add you if needed.

### Required software
- Git: most likely you already have this installed (try running `git --version` in a Terminal window). If not, see instructions [here](https://git-scm.com/install/).
- Ruby: follow instructions specific to your operating system on [this page](https://www.ruby-lang.org/en/documentation/installation/).

### Steps

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
