# ttn-backend

Example repo of the imaginary app "Toad Town News." This repo would hold backend code for that application.

This repo's true purpose is to show how a reusable workflows (located in ttn-workflows TODO LINK!) can be called upon from caller workflows. 

# Workflows

This section describes the workflows used in this repository. Note several of these are caller workflows; the brunt of business logic may be in the reusable workflow called. These reusable workflows are located in the org-mushroom-kingdom/ttn-workflows repo TO DO LINK unless otherwise noted.

## Frontend Changelog Check (Exists/Naming)

Name: Backend Changelog Check (Exists/Naming)
Filename: `sc-changelog-check-exists-and-naming-caller.yml`
Reusable Workflow Filename: `org-mushroom-kingdom/ttn-workflows/.github/workflows/changelog-quality-checks.yml`

## Scenario

It's part of a greater example of how to checkout the reusable workflow's repository to access a script it has needed for certain work. 

See the ttn-workflows repo for much more detail.
