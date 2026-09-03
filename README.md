# OpenClaw GitHub Operations Demo

This small repository demonstrates an OpenClaw assistant that can turn a Slack
request into a reviewable GitHub pull request. It is designed to show the full
workflow in a safe, easy-to-inspect setting rather than make changes directly to
a production codebase.

## What the demo shows

1. A requester asks the assistant to investigate a known failing test.
2. The assistant checks the code, prepares a focused fix, and runs the test.
3. It creates a separate `openclaw/<operation-id>` branch and opens a pull
	request with the proposed change and test evidence.
4. A person reviews the pull request and decides whether to merge it.

## The Example Problem

`sample_target/calc.py` intentionally has a bug in `add()`. Before a fix, this
check fails:

```sh
python -m pytest sample_target/tests/test_calc.py::test_add
```

The repository is the bot's default demo target when a requester does not name a
repository explicitly. It supports only bounded issue creation and pull-request
generation with a permitted test command.

## Built-In Safeguards

The `main` branch is protected by an active GitHub ruleset with no bypass
actors. Changes must arrive through a pull request, and GitHub blocks direct
updates, force pushes, and branch deletion. The assistant can create a proposed
change, but it cannot write directly to `main`.