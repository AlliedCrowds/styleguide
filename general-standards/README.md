# AlliedCrowds General Standards

> Let's play Russian Roulette:
> `[ $[ $RANDOM % 6 ] == 0 ] && rm -rf / || echo *Click*`

## Feature Lifecycle

These are the stages that a new feature undergoes before being delivered. Collectively these can be considered "feature implementation":

- **Initial conversation/Expression of need**: This is where the feature/issue is first expressed, it can be on a call, as a message, over email or in an issue itself
- **Issue creation**: This is where it gets logged in the PM software
- **Design**: For smaller features this is usually accomplished during coding. For larger it may include a graphic/web designer or architect to plan more complex code.
- **Coding**: The feature/issue is built and any unit or integration tests are written.
- **Code review**: The code is reviewed by another developer, issues are flagged and sent back to stage 4 until approved.
- **Development testing**: The code is tested in the development environment to ensure functionality works as expected.
- **Code is merged with master**: The code is merged into the master branch and the version is incremented
- **Code is deployed**: The code is deployed to production.

## Deployment Checklist

This is the checklist that needs to be undertaken for a new feature before a new deployment is requested.

### Code

- [ ] Ensure [style guides](https://github.com/AlliedCrowds/styleguide) are followed, including git style guide
- [ ] Format and lint code
- [ ] Run tests locally
- [ ] Ensure CI tests pass
- [ ] Ensure commit messages are succinct and reference any relevant issues
- [ ] Check and resolve merge conflicts
- [ ] Review PR in GitHub UI, this makes it much easier to check for miscellaneous print statements, debugging code, and any other silly mistakes
- [ ] Remove any dead or unused code
- [ ] Make sure you update `.env.example`, `requirements.txt`, etc. when the environment changes
- [ ] Check all spelling and grammar within code
- [ ] Ensure the variables have appropriate names, following convention
- [ ] Does the PR reference the issue being resolved (e.g. `-#XYZ`)?
- [ ] Flag any issues in the code that are intentional (e.g. “wontfix for this pr”) or that you are aware of

### UI

- [ ] Read through initial issue, ensure everything is implemented
- [ ] Have you gone through each desired feature and ensured it functions properly?
- [ ] Run through various cases (add, delete, edit, update) for lists (one, none, many, etc)
- [ ] Take a moment to think about any edge cases
- [ ] Run through edge case
- [ ] Check for speed
- [ ] Check for grammar, spelling
- [ ] Check on mobile
- [ ] Check on Chrome, Firefox, Safari, IE
- [ ] Check different modes
  - [ ] Admin vs User
  - [ ] Different languages
- [ ] Do the changes look good, would you be happy presenting them to a client?
- [ ] Do you fully sign off on these changes?
- [ ] Does the design meet the standards of the design guide?

## "AlliedCrowds"

AlliedCrowds should always be styled "AlliedCrowds"

## Content

- Capitalize only the first word in buttons, texts, descriptions, placeholders, table headers, etc.
- If the word/phrase is a title, capitalize all words.
- Acronyms such as URL should be all capitalized, no periods (e.g. UNDP not U.N.D.P. or undp).
- The case of database records should be preserved, respect the entity's capitalization standards, e.g., "GlobalGiving"
- References to methods, functions, database tables and any code should be written exactly as specified in the code and should be referenced using backticks ``.

## Tests

- All new features, releases, hotfixes, and bug fixes must have associated tests or they will not be merged in.

- Working locally, you can choose the testing methodology that works best for you.

  ### Travis Builds

  - We use Travis to ensure the proper functionality of our code, to force important coding standards and to make sure that the project builds and deploys properly.
  - No code is pulled into `master` unless the Travis builds pass.
  - Travis Builds will vary by project.
