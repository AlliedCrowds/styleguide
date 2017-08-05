# AlliedCrowds General Standards
> Let's play Russian Roulette:
> `[ $[ $RANDOM % 6 ] == 0 ] && rm -rf / || echo *Click*`

## "AlliedCrowds"

AlliedCrowds should always be styled "AlliedCrowds"

## Content

* Capitalize only the first word in buttons, texts, descriptions, placeholders, table headers, etc.
* If the word/phrase is a title, capitalize all words.
* Acronyms such as URL should be all capitalized, no periods (e.g. UNDP not U.N.D.P. or undp).
* The case of database records  should be preserved, respect the entity's capitalization standards, e.g., "GlobalGiving"
* References to methods, functions, database tables and any code should be written exactly as specified in the code and should be referenced using backticks ``.

## Tests

* All new features, releases, hotfixes, and bug fixes must have associated tests or they will not be merged in.

* Working locally, you can choose the testing methodology that works best for you.

  ### Travis Builds

  - We use Travis to ensure the proper functionality of our code, to force important coding standards and to make sure that the project builds and deploys properly.
  - No code is pulled into `master` unless the Travis builds pass.
  - Travis Builds will vary by project.
