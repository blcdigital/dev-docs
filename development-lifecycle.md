# Development lifecycle

## Goals

- **To be able to cut a release from `main` whenever we want.** We want to have the confidence in our work and in our process that a release can be made at any time.
- **Automate all the things 🤖.** By leveraging automation for code quality checks, E2E, and regression testing (both visual and functional) we can take the pressure of QA teams and release faster and with more confidence.

## Development

This lifecycle is based on a flavour of Trunk Based Development[1] called "Scaled Trunk Based Development". The key difference is developers use short-lived feature branches in a similar fashion to GitFlow[2] instead of merging their code directly into the trunk.

### Workflow

1. Create a new branch from `main`
    - Recommended naming convention: `[TASK_TYPE]/[TICKET-NUMBER]-[SHORT_TICKET_DESCRIPTION]` e.g. `feature/ABC-123-user-login`;
1. Write code
1. Peer review and automated testing
    - Each PR must pass all automated tests before being merged;
1. QA (optional)
    - If the work is a new feature or too complex for automated testing then it should be manually QA'd;
1. Amends from peer review and manual QA
1. Merge into `main`
    - Before merging the branch should pass all of the automated tests and have at least one approval. If more than one developer has left comments then these should also be addressed and approved before merging;
    - The source branch should be up to date with the target branch;
    - The recommended merging strategy is "Squash and merge". We care about the task in its entirety but we should ne be concerned about the individual steps taken at this stage;

## Releasing a new version

![normal-development](https://user-images.githubusercontent.com/835629/119111937-77b27700-ba1b-11eb-84ab-0d21fb9bcc22.png)

The release process should also be automated based on a fixed trigger, for example creating a "Release" in Github.

Release notes detailing everything included in the release must be added here too. The use of Gitmoji[3] is encouraged.

## Hot fixes

Once a production issue has been reported it should be replicated on both the production and staging environments. The reason for additional replication on the staging environment is to confirm any changes waiting to go to production have not already fixed the issue.

### Fixing the bug

The process is identical to the usual development flow outlined above with the `[TICKET-TYPE]` being set to `bugfix`. This makes it easier to identify when looking at the commit logs for the `main` branch.

### Releasing the hotfix

![hotfixes-to-a-release](https://user-images.githubusercontent.com/835629/119111970-80a34880-ba1b-11eb-90cf-f9d20b3f58a0.png)

Once the fix has been merged it can be release in isolation.

1. Create a `hotfix` branch from the tag of the last release using the recommended naming convention
    - ```bash
      git checkout -b hotfix hotfix/[TICKET-NUMBER]-[SHORT_TICKET_DESCRIPTION] [TAG]
      ```
1. Cherry-pick the bugfix from `main`
    - As the PR is squashed and merged it should only be a single commit that needs to be cherry-picked;
    - To find the hash you can obtain it from the UI of you code repository or use the following command to on your development machine:
      ```bash
      git log --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
      ```
      **Note:** You will need to be on the `main` branch and have pulled the latest from the `origin`.
    - Once you have the commit hash you can switch back to the hotfix branch and cherry-pick:
      ```bash
      git cherry-pick [COMMIT_HASH]
      ```
1. Push the hotfix branch
1. Create a new release as detailed in the "Releasing a new version" section but using the newly pushed hotfix branch instead of `main`
    - You could push more than one hotfix at a time if you need to;
1. Verify the fix on production

## Environments

### PR previews

These should be created when a PR into `main` is opened or when a hotfix branch is first pushed to the repository.

Updates should occur when the PR source branch is updated or the hotfix branch is updated respectively.

### Staging

This should be continuously deployed from `main`. It is a constant view of what will be deployed in the next release.

### Production

The live environment which is updated as described above.

## FAQs

#### What do we do with stale hotfix branches?

These should be cleaned up periodically. It should be up to the team to decide when as it needs to fit their cadence but at the end of a sprint could be a good point.

#### Why does the source branch need to be up to date with the target?

It's implicit integration testing.

By making sure the code is up to date and having all of the automated tasks pass it gives us confidence that the addition of the changes will still be a deployable version.

#### Why not release the `main` branch when the hotfix is complete?

## References

1. Trunk Based Development: https://trunkbaseddevelopment.com/
1. A successful Git branching model: https://nvie.com/posts/a-successful-git-branching-model/
1. Gitmoji: https://gitmoji.dev/
