# Requirements documentation - CD

This document is a guideline and requirements list for the _Continuos Development_ (CD) of all applications attached to the Microservice group or Monolith. 

> For *humans*: Face the entirity of the following text as a suggestion. This has been structured for a fast and organized development flow of a one person / small team. You should refine and change it with what works for yourself and/or your team. 

# Git flow / Development pipeline:

## Branch types
- main: the production application/server will be built from this branch on every new commit via a *deploy.yml* workflow.
- develop: the staging applicataion/server that replicates production is built from this branch on every commit via a *deploy.staging.yml" workflow.
- feat/feat_title: no server is deployed from this branch, it can only be merged into the develop branch if it builds and passes the _Testing_(testing.md) requirements.

## Commit types
- (fix):message [ Bug fix / minor adjustment that doesnt impact other domains of the application, this commits should never touch any thing outside of its context scope ]
- (chore):message [ Commits that affect multiple scopes or integration related code, internal or external]
- (refactor):message [ Code refactors]
- (feat/feat_title):message

## Rule set:
- Each commit must never, under any circunstance be sent directly to the "main" branch, it must always go through the staging phase on the "develop" branch. 
- Fix,chore and refactor commits can be pushed directly to develop as long as it builds and passes the _Testing_(testing.md) requirement.
- Feat commits can only be generated through a own separated branch before being merged to develop.
- A feature branch must always come with a documented specs and plan document stored in "docs/specs/features". A Feature is not only contained to a new functionality, it can have a macro or micro refactor built around a feature change, creation or even removal. 
-  All changes in any commit type that might affect the integration/compatibility between microservices must always be backwards compabitle or have as a clear part of the plan a compatibility fix/update on the affected service (if applicable)
