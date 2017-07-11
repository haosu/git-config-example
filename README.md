# Git configuration examples

Here is a quick example of the git configuration that I've found useful. They come primarily in the form of aliases configured in the `.gitconfig` file. To use these configurations, append the `.` to the file names (eg: `mv gitconfig .gitignore`). Obviously, modify these files to match your workflow and preferences. I started using many of the aliases while using a rebase and cherry-pick workflow.

The following documentation will include explanation for select configurations.

## .gitconfig

### [alias]

Here are some notable aliases. There are many others what are just single character shortcuts to common actions. I've most commonly used: `ap`, `ci`, `rb, `rbc`,`rbi`.

* amend    = "!f() { scripts/amend "$@"; }; f"

  Calls a script to amend a specific commit. This can also be replaced with `git commit --amend --verbose`. The verbose flag is useful in that it shows a diff of the upstream change.

* amsc     = commit --amend --no-verify --verbose

  The majority of repos I've worked in have many built in githooks for obvious reasons. Sometimes they can be slow, and sometimes I can be lazy. This is useful for quick WIP amends for sharing. Not recommended for anything but drafts.

*  cisc     = commit --no-verify

  Another "draft only" or laziness shortcut

* fresh    = "!f() { scripts/fresh "$@"; }; f"

  Fetches remote changes to the current branch and initiates a rebase if necessary. See the script for additional functionality explanation.

* rf       = ...

  See `.gitconfig` for the action. This is a sloppy way to save current uncommitted progress and rebase to the newest remote change. It will also run Rails database migrations. Most useful in a cherry-pick model. I'm including this here as an example of inlining commands in the config.

* wip      = commit -m WIP --no-verify

  Sometimes the stash isn't good enough. Share your works in progress with a WIP commit.

### [apply]

* whitespace = fix

  Removes trailing whitespace from the changes in your commit. Super useful, I forgot I was using this

### [credential]

* helper = osxkeychain

  Keep me logged in :-D

### [help]

* autocorrect = 10

  Make a typo? Don't worry, `git` will help run your intended command after the configured timeout.

## .gitignore

Drop filename patterns here to prevent git from committing unwanted garbage! This obviously changes depending on what tools you like to use.

## A few best practices

### --patch

This option allows you to `add` or `checkout` changes line by line. Working this way provides a more in-depth look into changes before any more permanent action. It's a low cost method of reducing absent minded mistakes.

