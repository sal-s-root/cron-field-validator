# cron-field-validator

Validate a deliberately restricted five-field cron schedule.

## Run

Python 3.8 or later; no third-party packages or cloud credentials are required.

```sh
python3 tool.py examples/input.json
cat examples/input.json | python3 tool.py -
python3 -m unittest -v
```

## Example

Input:

```json
{
  "schedule": "0 2 * * 1"
}
```

Result:

```json
{
  "valid": true,
  "fields": [
    "0",
    "2",
    "*",
    "*",
    "1"
  ]
}
```

The command writes JSON to standard output. Exit 0 means evaluation completed;
a finding in the output may still require attention. Invalid input returns exit 2,
with an error on standard error and no result on standard output.

## Operational scope

Does not support ranges, steps, lists, macros, timezone semantics, or calendar feasibility.

The tool evaluates supplied data locally. It does not change hosts, deploy
resources, or establish production compliance. Example identifiers and observations
are test fixtures. Keep credentials and private inventory out of Git.

## Design and verification

See [NOTES.md](NOTES.md) for the input contract, verification, and integration notes.
Related utilities: [process-snapshot-sorter](https://github.com/sal-s-root/process-snapshot-sorter), [log-level-counter](https://github.com/sal-s-root/log-level-counter).
