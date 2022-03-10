# 6. environment variables overrides config file

Date: 2022-03-10

## Status

Accepted

## Context

Automated deployment pipeline that I've set up requires certain resources to work, a run-once workflow was set up to create the associated resources for the build and deploy pipeline.
The runonce registers container registry resource provider, creates the rg and ACR objects.


## Decision

Create a run-once workflow to set up the variables so as to cut down troubleshooting the effects of repeated script executions for creating resources

## Consequences

Run-once script must be run first to set up resources for the CI Pipeline
