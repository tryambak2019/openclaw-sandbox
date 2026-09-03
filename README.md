# openclaw-sandbox

Minimal target repository for the OpenClaw GitHub-operations demo. The deployed
bot resolves an omitted repository target to `tryambak2019/openclaw-sandbox`.

## Demo target

- `sample_target/calc.py` intentionally contains a bug in `add()`.
- `sample_target/tests/test_calc.py::test_add` fails before a corrective change.
- PR changes use `openclaw/<operation-id>` branches and target `main`.

## Main protection

The active `Protect main` repository ruleset has no bypass actors. It requires
pull requests for updates to `main` and blocks branch deletion and force pushes.
The bot may create a branch and pull request, but cannot push directly to
`main`.

The repository is a bounded demo target only. Supported bot operations are issue
creation and PR generation with an explicit permitted test command, such as:

`python -m pytest sample_target/tests/test_calc.py::test_add`