# ttn-backend

Example repo of the imaginary app "Toad Town News." This repo would hold backend code for that application.

This repo's true purpose is to show how a reusable workflows (located in ttn-workflows TODO LINK!) can be called upon from caller workflows. 

# Workflows

This section describes the workflows used in this repository. Note several of these are caller workflows; the brunt of business logic may be in the reusable workflow called. These reusable workflows are located in the org-mushroom-kingdom/ttn-workflows repo TO DO LINK unless otherwise noted.

## sc-changelog-check-exists-and-naming-caller.yml (Backend Changelog Check (Exists/Naming))

Name: Backend Changelog Check (Exists/Naming)
Filename: `sc-changelog-check-exists-and-naming-caller.yml`
Reusable Workflow Filename: `org-mushroom-kingdom/ttn-workflows/.github/workflows/changelog-quality-checks.yml`

### Scenario

In this scenario, a caller workflow in `ttn-backend` (and `ttn-frontend`) rely on the reusable workflow `changelog-quality-checks.yml` which checks for a changelog file (referred to hereon as a CHANGELOG file) when a pull request is made from a release branch to the main branch (See **__Triggers** for more details). The logic surrounding the CHANGELOG file is strict and the file must meet certain criteria before merging into the preprod or main branch is allowed (see **__Business Logic__** for details). 

This is an example of how a reusable workflow (`changelog-quality-checks.yml`) can be called upon from a caller workflow (`sc-changelog-check-exists-and-naming-caller.yml`), with the specific caveat that the reusable workflow needs to check out its own repository in order to run a script to perform the brunt of its logic. This requires passing a token present in the caller workflow repository to the reusable workflow repository.

Refer to the Medium Article [Github Actions: Checking Out And Utilizing a Reusable Workflow's Repository](https://blog.devops.dev/github-actions-checking-out-and-utilizing-a-reusable-workflows-repository-992adbe7b3ae) for more details on this scenario as well as the ttn-workflows README 

It's part of a greater example of how to checkout the reusable workflow's repository to access a script it has needed for certain work. See the ttn-workflows repo for much more detail regarding the .

### Triggers

The `sc-changelog-check-exists-and-naming-caller.yml` caller workflow will activate upon the following triggers:

`workflow_dispatch`: This workflow can be triggered manually. TODO SEE MANUAL TESTING?

`pull_request`: Triggered by a pull request being opened, synchronized, or reopened. This is <strong>in conjunction</strong> with the `branches` key
`branches`: `preprod`, `main` (only merges to these branches will trigger the workflow in this way)

Note: While this workflow will activate upon a proper pull_request/branches combo, it should be noted that the workflow will only perform actual work if the source branch is a release branch (begins with 'release'). Otherwise, all logic will be skipped.

### Business Logic

