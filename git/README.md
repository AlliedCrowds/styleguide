# Git Workflow

Our Git workflow is structurally similar to the ['Gitflow' workflow](http://nvie.com/posts/a-successful-git-branching-model/), also see the [Atlassian write up](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow). We have modified this workflow, prioritizing a clean and simple git history.

 One major difference is that we have removed the `develop` branch. Instead we use `master` as our `develop` branch and tag commits once we have reached a production ready state. There appears to be only one disadvantages to removing the `develop` branch in this way. This is addressed in the [Rebasing](#rebasing) section.

Another major difference is that we do not allow any merge commits in our `master` branch. The 'Gitflow' workflow prioritizes `feature/` and `bugfix/`branches as sources of truth. In the 'Gitflow' model merge commits make debugging botched features and bugfixes simple, as it is obvious where the feature is implemented.

In our model `feature/` and `bugfix/` branches are rebased and squashed directly on top of `master` and each commit represents a full implementation of the feature or bugfix. The realization here is that commits within `feature/` and `bugfix/` branches, although relevant to the author while developing and perhaps the reviewer, reviewing the PR, are irrelevant to the long term git history. Said otherwise, the benefit of including hundreds of these development commits is far smaller to the benefit of having a clear and succinct git history, provided `feature/` and `bugfix/` branches are focused and well defined.



## Branches

All branches (except `master`) must be prefixed with:

- `feature/`: Used for developing features, keep these specific and isolated to only related features that should be pushed up logically together. Develop locally (pushing up commits regularly) and when completed, create a pull request to `master`. All new features should have tests written for them before being pulled in.
- `release/`: Used for finalizing functionality and user testing before a new release. No new features can be added to `release` branches —only bug fixes, documentation generation, and other release-oriented tasks should go in this branch. Once it's ready to ship, the release gets merged into `master` and the commit is tagged.
- `bugfix/`: Used solely for fixing bugs and writing tests. Much like `feature/` branches, keep these specific, isolated to only related bugfixes. If a bug is fixed and can be tested, a test should be written that assures the bug will not resurface.
- `hotfix/`: Used solely for immediate fixes to the production environment. Branched from **the latest tag** of `master` and then rebased back into `master` after the latest tag. Hotfixes –like releases– will also have associated version number that bumps patch.

#### Separate your Branches

Do not include multiple new features, bugfixes and/or tests in a single branch that should be logically separated. Split each new feature, each bugfix and each test into its own branch if they are not related.

#### Branch Naming Conventions

- `/` is used for grouping (a delimiter between branch types and names)
- `-` is used in lieu of a space
- All branches (excluding those that bump versions numbers) should reference an issue and should end in `-#XYZ`, where "XYZ" is the issue number.
  - If an issue does not already exist, create one before creating the branch.
  - If multiple issues exist, reference the most prominent issue in the branch and reference the others in the commit messages.
- All branches that bump version numbers should end in `-vX.Y.Z` where "X.Y.Z" is the version number

Examples:

- `feature/restyle-homepage-#28`
- `bugix/replace-stubbed-ahref-#22`
- `hotfix/spelling-mistake-#43`
- `release/initial-public-launch-v1.0.0`
- `hotfix/user-session-dropping-v0.0.3`



## Issues

If you come across a bug or think of a missing feature, create an issue.

- Issues should have succinct headers and be labeled appropriately,
- You are encouraged to add an explanation and image to make is as understandable as possible. Imagine someone else reading the issue for the first time. Try to explain the issue in a way that they understand it without having to reference the code or the deployment.

## Labels

Labels are used to categorize issues and pull requests.  Use labels liberally, so long as they meet the descriptions below, as they serve to provide better and more readily available information regarding labeled items.

#### Priority

Used for indicating the priority of items.

- `HIGH PRIORITY` : Issues and PRs that should be resolved within 2 days of being labeled. If the two day deadline is infeasible, that must be communicated. If a shorter deadline is indicated, the new deadline will supersede the 2 days rule and be adhered to.
- `priority`: These are the next most important tasks to be done. They do not indicate a deadline, but should be prioritized over non-labeled and `low priority`
- `low priority`: These are lower priority than non-labeled items. Should be ignored unless all other issues/PRs have been addressed or if they can be trivially solved.

#### Review

Used in reviewing PRs. See below section on Pull Requests for more in depth examples.

- `review needed`: Used to indicate that a PR should be reviewed by someone other than the requester.
- `in progress`: Used to indicate that a PR is being worked on, or that it has been reviewed and rejected.

#### Blocking

- `blocked`: Used when an issue is unable to be addressed before another issue is resolved. The blocking issue must be referenced in the `blocked`
   issue.

#### Category

These are applied only to issues and are used to group issues within a similar category. They are self-explanatory and will vary by project, some issues may be tagged with multiple of these labels. Examples:

- `backend`
- `frontend`
- `bug`
- `feature`
- `test`

#### Feedback

Used for asking questions or delivering new information.

- `note`: Issues labeled as notes should be noted by all team members with a comment "noted". Once noted by all team members, these issues can be closed.
- `question`: Issues and PRs labeled as question should also assign the person that the question is directed to (if the question is directed to everyone, everyone should be assigned). The issue should then be closed by the asker once the question is answered. If the question is a part of a PR or only a part of an issue, the label will simply be removed.

## Commits

Individual commits should be [atomic changes](https://en.wikipedia.org/wiki/Atomic_commit) to the codebase.

- A commit should not leave the code in a broken state waiting on a later commit to fix it. These commits are fine in development stages but *have* to be squashed before pulling into `master`.
- Changes that are not related should be split into separate commits. Bugfixes that are prerequisites to your change but not the main purpose of the change should be made in separate commits.
- Make sure changes are rebased on latest `master`. Ensure your code is up-to-date with `master` to prevent merge conflicts.

#### Commit Messages

Follow the [git commit message standard](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html). See http://whatthecommit.com for examples of what not to commit (refresh page).

The following emphazises or overrides where applicable:

- The first character of every commit must be capitalized
- Commit messages must be informative regarding the code that you are committing.
- Commit title messages should aim to be < 90 chars
  - If you need more than 90 chars to explain your commit, consider using description space to expand upon what has been changed
- More detailed explanatory text is encouraged if necessary
- Write in the imperative `Fix bug` not `Fixed bug` or `Fixes bug`, this matches the conventions of git commands `git merge`, `git pull`, etc.
- When resolving issues append `, fix #XYZ` to your commit message where `XYZ` is the issue number you are resolving. This will automatically close the issue once the code is pulled into `master`. You may fix multiple issues in one commit, `, fix #ABC fix #XYZ`
- If referencing an issue, append `, reference #XYZ`

It's a good idea to include the rationale for a change in the explanatory text for non-trivial changes:

> This is why commit messages are important - they explain why the code was changed. Hence the code review process is not just about the code - the reviewers need to understand why the code is being changed and the process that led to the change being proposed. The commit history is going to be the only record of why this code exists in 10 years time, so the explanation needs to be correct.

See https://lwn.net/Articles/637896/

## Pull Requests

- Once you have finished your branch and are ready for someone else to look over your code, submit a pull request and apply the `review needed` flag.
- When you begin reviewing a pull request, assign yourself to it.
- If you review a pull request and approve of everything in the code, merge the pull request into `master`, squashing all redundant, unnecessary or nonatomic commits and rewriting poor commit messages.
- If you do not approve of everything in the code, make comments, remove the `review needed` label and apply the `in progress` label.
- You should not submit a pull request when there are pull requests with the `review needed` label, unless they are assigned to someone else.
  - You should review this pull request before submitting your PR.
  - Note: If Travis builds are failing or if there are merge conflicts, you may mark a PR `in progress`.
  - Note: You should not expect a PR to be reviewed if Travis builds are failing or if there are merge conflicts.
- If any of your PRs has an `in progress` flag you must address the comments, remove the `in progress` label and apply `review needed` label. Continue iterating this process until the branch is pulled in.
- If you disagree with someone's comments start a dialogue on Github with that person or via private chat (if you come to a resolution via private chat, post the conclusion on Github). If you cannot come to a resolution, bring a third party in to review the PR.
- If, for whatever reason, you are needed to change code directly on someone's branch. For example, an immediate deadline and that person is away.
  - Pull down their branch, make your commits, when you are done submit a pull request for anyone to review (you have implicitly approved of the code from the previous pull request so the author of that request may pull it in).

The above outlines a typical scenario involving a `feature/` or `bugfix/` branch.

#### Special rules apply to `release/` branches:

- Branched from `master` and then pulled into `master` when ready. Release branches must have the version number `X.Y.Z` in the branch name, this is what `master` will be tagged with upon completion.
- A development server will be used to review `release/` branches by the relevant parties.
- If, after reviewing the release branch, no further changes are necessary, the branch will be rebased on top of `master` and the last commit tagged accordingly. This tag will automatically deploy `master`.
- If further bugfixes are necessary, they will be added to the `release/` branch and then the process will be iterated until all bugfixes are satisfied.

#### Special rules apply to `hotfix/` branches:

- Branched from the **most recent tag** of `master`.
- Rebased on top of the **most recent tag** of `master`, inserting your commit after the most recent tag of `master`.
- Everything else is the same as `release/` branches

## <a name="rebasing">Rebasing</a>

Never rewrite history. If the code is in the master branch **DO NOT** attempt rewrite it in any way, shape or form.

Exception: commits after the latest tag when merging a `hotfix/` branch. This is a special circumstance where production code must be immediately fixed. In this circumstance a special hotfix commit will be inserted after the latest tag of master. This is the only trade off for not including a `develop` branch. Any commits after a tag without an enclosing tag (a tag coming later in the commit history) should be considered `develop` and are liable to be rewritten. Once the commits are enclosed by a tag they have been codified in our git history and will never be changed.

- Rebase all branches on top of `master` before pulling in.
- Squash/amend minor errors and syntax in commits locally before you push branches up. This makes your history more understandable.
- Most PRs should only be pulled in as one commit (handled automatically by Github's "Squash and merge functionality")
- If all commits in the branch are necessary and relevant, you should note this in the PR and the "Rebase and merge" option should be selected when pulling in, leaving the commits intact.
- See [Rewriting history - Atlassian](https://www.atlassian.com/git/tutorials/rewriting-history) and [squashing commits with rebase - Nick Quaranto (git ready)](http://gitready.com/advanced/2009/02/10/squashing-commits-with-rebase.html) for more details.

## Versioning

For versioning, we follow the [Semantic Versioning Specification](http://semver.org). Everything below overrides mentions in the article above, which are assumed understood. Anything not mentioned below is not to be strictly enforced:

- A normal version number MUST take the form X.Y.Z where X, Y, and Z are non-negative integers, and MUST NOT contain leading zeroes. X is the major version, Y is the minor version, and Z is the patch version. Each element MUST increase numerically. For instance: 1.9.0 -> 1.10.0 -> 1.11.0.
- Patch version Z (x.y.Z | x > 0) MUST be incremented if only backwards compatible bug fixes are introduced. A bug fix is defined as an internal change that fixes incorrect behavior.
- Minor version Y (x.Y.z | x > 0) MUST be incremented if new, backwards compatible functionality is introduced. It MUST be incremented if any public functionality is removed. It MAY be incremented if substantial new functionality or improvements are introduced within the private code. It MAY include patch level changes. Patch version MUST be reset to 0 when minor version is incremented.
- Major version X (X.y.z | X > 0) MUST be incremented if any backwards incompatible changes are introduced. It MAY include minor and patch level changes. Patch and minor version MUST be reset to 0 when major version is incremented.

## Tagging and Releases

All tags follow our above mentioned versioning system.

- When a new `release/` or `hotfix/` branch gets created the version number of the project should be bumped.
- After one of these branches gets pulled into `master` and the development server is approved, the final merge commit must be tagged with the appropriate version number (the same one that has been bumped when the branch was created).
- Content Standards
  - The title of releases will have the first character of each word capitalized.
  - Bullet points with further explanation will be provided. When in doubt about an explanation, use the commit messages from the commits between this release and the last.
    - Bullet points have one new line in between them, unless they are nested. There is no new line between nested bullets.
  - Release notes should be succinct and clear to both technical and non technical readers.