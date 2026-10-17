# Subagent Workspace

This directory stores reusable guidance for **bounded parallel workers** used by Codex or another runtime that supports subagents.

Important: repository files do not create runtime subagents. They define safe task shapes and handoff rules so parallel execution stays controlled.

## Use subagents when

- workstreams are independent;
- file ownership can be clearly separated;
- research/QA can run in parallel with implementation;
- multiple hypotheses can be investigated independently;
- waiting on one stream would leave useful capacity idle.

## Do not use subagents when

- two workers would edit the same files;
- architecture/contracts are still moving;
- the task is tiny or sequential;
- client feedback or missing inputs are the real bottleneck;
- orchestration overhead is larger than the expected time saved.

## Every subagent task must include

1. objective;
2. owned files / system boundary;
3. areas that must not be modified;
4. relevant source-of-truth files to read;
5. expected output;
6. required verification;
7. handoff back to the coordinator.

## Coordinator rule

The coordinator owns integration and final verification. A subagent result is evidence, not proof that the project is complete.

See `AI_ORCHESTRATION.md` for the full multi-agent policy.
