# AlliedCrowds General Style Guidelines

# "Alliedcrowds"
AlliedCrowds should always be styled "AlliedCrowds," never "alliedcrowds", "alliedCrowds", or "Alliedcrowds"

# Content
* Capitalize only the first word in buttons, texts, descriptions, placeholders, headers for tables, etc regardless of whether it is a complete sentence or not.

# Git workflow

Our Git workflow is heavily inspired by the [‘Gitflow’ workflow](http://nvie.com/posts/a-successful-git-branching-model/). Although one major difference is the lack of a `develop` branch. Instead opting to use `master` as our staging branch and using Git tags as our way of deployment.

## Issues
If you come across a bug or think of a missing feature, create an issue.

* Issues should have succinct headers and be tagged appropriately,
* You are encouraged to add an explanation and image to make is as understandable as possible (imagine someone else reading the issue for the first time).

## Commits

Indiviual commits should be [atomic changes](https://en.wikipedia.org/wiki/Atomic_commit) to the codebase.

* A commit should not leave the code in a broken state waiting on a later commit to fix it. These commits are fine in development stages but *have* to be squashed before pulling into the master branch.
* Changes that aren't related should be split into separate commits. This must be taken with the previous rule in mind to help determine what's related or not. Bugfixes that are prerequisites to your change but not the main point of the change should be made in separate commits that come first.

Please follow the [git commit message standard](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html).

It's a good idea to include the rationale for a change in the explanatory text for non-trivial changes:

>This is why commit messages are important - they explain why the code was changed. Hence the code review process is not just about the code - the reviewers need to understand why the code is being changed and the process that led to the change being proposed. The commit history is going to be the only record of why this code exists in 10 years time, so the explanation needs to be correct.

See: https://lwn.net/Articles/637896/

## Make sure changes are rebased on latest master.

Ensure your code is up-to-date to prevent merge conflicts.

## .gitignore

Since most developers at AlliedCrowds use the same tools, specifically the Intellij line of products and computers running OSX, files such as `.DS_Store` and `.idea` should be added to the global gitignore. If you use different tools such as Vim and its `*.swo` files, you should add these files to your [personal global gitignore](https://help.github.com/articles/ignoring-files/#create-a-global-gitignore) file.

# Pull Requests

* Once you have finished your branch and are ready for someone else to look over your code, submit a pull request and apply the `review needed` flag.
* When you begin reviewing a pull request, assign yourself to it.
* If you review a pull request and approve of everything in the code, merge the pull request.
    * If you have changes, ensure to comment on the latest commit (‘Files Changes‘ in the Github Web GUI)
    * Do NOT commit to someone elses branch. If you wish to submit changes to another person's branch use native Git pull requests and submit a comment with the changes.
    * Branch off of the other person's branch. Do not push this branch to origin under any circumstances.
    * Make the changes you wish to make and commit them locally.
    * Use `request-pull` or `diff` to submit your changes to the branch owner

## Tagging

All tags should follow [SemVer v2.0.0](http://semver.org/spec/v2.0.0.html). Please read over the linked document and ensure you fully understand it.

## Rebasing

Never rewrite history. If the code is in the master branch **DO NOT** attempt rewrite it in any way, shape or form.

## Writing Tests
* All new features and bug fixes must have associated tests or they will not be merged in
* Working locally, you can choose the testing methodology that works best for you.
