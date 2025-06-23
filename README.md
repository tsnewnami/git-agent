# Git Agent

This is a minimal and lean example (uses minimal libraries and a custom agent loop (not via SDK)) of an Agent for the sake of learning. This agent is a git agent which can execute git commands inside a local container, such as creating a new github repository.

## Requirements

- Docker
- A GH personal access token set in the environent to be used inside the docker container

## Improvements

This code is not optimal and could be improved such as:

- Using SDKs, e.g. for the agent loop
- Using logging
- More robust error handling when container exec commands fail
- Using a better sandboxed environment such as e2b
