### The current development process:
- When we start a new version from the current stable (master), you create a new beta branch (v[version-code]-beta).
- Protect this branch from the direct merge without PR review.

- When you start a bug or feature, you branch out from the current beta.
- You develop
- You test by yourself
- If beta evolved, rebase
- Pull request to beta => This triggers a Jenkins build to run test cases and other checks.
- Code review by one/two of ourselves
- Merge to beta.
- This triggers a Jenkins build to run test cases, other checks, and then deploys this instance on WIP instances (Postgres-Wip is currently we consider as the WIP instance, we can configure more like our personal once, lohith-wip etc).
- We move JIRA ticket to QA.
- QA team then verifies this ticket/build.
- If the ticket is not good, QA kicks back (Open), otherwise set to resolved.
- These steps continue till we come to a state where beta looks good enough. (All tickets given for this release are implemented).

- We start releasing this beta version. (Merge beta into the development branch). The release process is here: https://gist.github.com/royalpinto/8c765adab6df417ab84d9afd30ced876
- We also release this on JIRA and get the tickets and update in the release notes on GitHub.
- Once this beta release is done (or RCs), builds will be available for the ops team to deploy on POC and Test instances (If they would like to).

- Then we start working on RC branches (rc1, rc2, rc3..) as mentioned in the beta release process link above and continue above steps.

- Once we get a go-ahead from QA team for the stable build, we start releasing the stable version. https://gist.github.com/royalpinto/5839eb473a0807879f7d4780cabadec9