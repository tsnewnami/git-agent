# Git Agent

This is a minimal and lean example (uses minimal libraries and a custom agent loop (not via SDK)) of an Agent for the sake of learning. This agent is a git agent which can execute git commands inside a local container, such as creating a new github repository.

This is a submission for part of [Production-Ready Agent Engineering: From MCP to RL](https://maven.com/will-brown-kyle-corbitt/agents-mcp-rl)

## Requirements

- Docker
- A GH personal access token set in the environent to be used inside the docker container

## Improvements

This code is not optimal and could be improved such as:

- Using SDKs, e.g. for the agent loop
- Using logging
- More robust error handling when container exec commands fail
- Using a better sandboxed environment such as e2b
- Could likely do chaining of tool calls using `&&` however this task was targetted at multi-turn tool use.

## Course questions

What approaches did you try?

- Used a basic and lean approach with minimal dependencies for the sake of education. The idea here was to expose the agent loop as much as possible for learnig and not rely on heavy abstractions.

What roadblocks did you run into?s

- Struggled to correctly to get the agent to end the loop when the task was complete, i.e. populate the `<answer></answer>` tags. The agent would continue running until the turns were exhausted.
- Had to do a hacky way to parse "completion token signals" from the thinking tags, like "finished", "complete" or "done". This is not robust.
- The model would also execute commands again redundantly, like calling `ls` to validate the existance of repo multiple times.

Which evaluation methods worked best for your task?

- Running unix commands against the artifacts output from the agent, this is objective verifability. E.g. `ls -a` to verify existance of `.git` file.

What's the smallest model that worked decently well?

- GPT-4.1
