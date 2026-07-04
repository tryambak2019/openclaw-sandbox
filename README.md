# openclaw-sandbox

Minimal target repo for the Slack `/fix-test` bounded showcase.

Seed failing test:
- `sample_target/calc.py` intentionally contains a bug in `add()`.
- `sample_target/tests/test_calc.py::test_add` is expected to fail before the bot runs.

Slack command example:
`/fix-test repo:tryambak2019/openclaw-sandbox test:sample_target/tests/test_calc.py::test_add`