# scrub.bot

Deterministic data cleaning for records, text, documents and more. Same input, same output; every edit logged, anything uncertain flagged.

ScrubBot trims and fixes casing, standardizes dates and phone numbers, repairs broken encoding, strips HTML, masks PII, validates emails and removes duplicates using fixed rules. It never invents a value: anything it cannot fix with certainty is left as it was and flagged with a reason. Every run returns the cleaned data, a log of every change, and a list of what it could not resolve.

## Try it

- **In the browser:** [www.scrub.bot/play](https://www.scrub.bot/play). Drop in a CSV, no account, nothing saved.
- **Worked examples:** [www.scrub.bot/examples](https://www.scrub.bot/examples)
- **Docs:** [www.scrub.bot/docs](https://www.scrub.bot/docs)

## Install

```bash
pip install scrub.bot
```

Requires Python 3.12 or newer. If pip reports "No matching distribution found" (older Python, such as the 3.9 that ships with macOS) or "externally-managed-environment" (Homebrew or system Python), install it as an isolated tool instead:

```bash
uv tool install scrub.bot      # or: pipx install scrub.bot
```

## Run it on your machine

```bash
scrub serve                    # the whole engine locally, SQLite, nothing leaves your computer
```

In a second terminal:

```bash
export SCRUBBOT_API_URL=http://127.0.0.1:8000
curl -sO https://www.scrub.bot/demo/contacts.csv
scrub clean/text/whitespace contacts.csv -o contacts.clean.csv
scrub handlers pii             # find handlers
```

The same engine is available as a REST API and as an MCP server for Claude and other agents. See [the MCP guide](https://www.scrub.bot/docs/mcp).

## Report a bug or ask for a feature

Open an [issue](https://github.com/scrubbot/scrub.bot/issues/new/choose). Please do not attach real personal data; a few made-up rows that show the problem are perfect.

Security problems: see [www.scrub.bot/security](https://www.scrub.bot/security) instead of opening a public issue.

## About this repository

This repository holds the public README and the issue tracker. The package on [PyPI](https://pypi.org/project/scrub.bot/) contains the full engine.

## License

Business Source License 1.1 (source-available, not open source). Internal use is allowed; offering ScrubBot as a hosted service to third parties needs a commercial license. Each version converts to the Apache License 2.0 on 2030-01-01. See [LICENSE](LICENSE).
