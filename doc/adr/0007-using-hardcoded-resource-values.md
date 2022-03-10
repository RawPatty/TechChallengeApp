# 6. environment variables overrides config file

Date: 2022-03-10

## Status

Accepted

## Context

To speed up delivery of this proof of concept, hard-coded resource values were used in situations where non-sensitive values were required.
For sensitive values such as subscriptionID, passwords, etc. I used secrets in the workflow, but where possible I hardcoded variables to speed up delivery.

This is my first time using github actions, and my objective was to deliver a proof of concept, so speed of delivery was prioritised over quality.

## Decision

Use hardcoded variable in a non-sensitive context

## Consequences

Certain variables can be seen externally, exposing this data provides an avenue for a malicious operative to set up a potential intrusion to the system