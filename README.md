![explanatory-skill](docs/banner.png)

# explanatory-skill

An agent skill that makes long answers start where the reader is, not where the agent ended up after reading forty files.

## Install

```bash
npx skills add mainpart/explanatory-skill -a claude-code -g -y
```

Works with any client that reads `SKILL.md` ([Agent Skills](https://agentskills.io/) format). Or clone and run `claude --plugin-dir ./explanatory-skill`.

## What it does

The agent applies it on its own before any research write-up, diagnosis, architecture review or answer longer than a few paragraphs.

- **One axis: reader immersion.** Every sentence may require only what the reader already knows by that line. Terms are explained on first use in one clause, numbers come after the thought they support, file paths and line numbers go to the bottom, headings never lean on text below them.
- **Every claim has an owner** (`references/attribution.md`): from a source, from the agent's reasoning on top of sources, or nowhere — and the third kind must not survive. Evaluative adjectives are swapped for the measurement behind them; "it is commonly held" gets a name; a heading may not claim more than its paragraph.
- **Not simplification.** The reader usually knows the field better than the agent; what they lack is the last hour. It orders, it doesn't dumb down.

Off for short replies, direct factual questions, and code edits against a specific request.

## Example

> Read these three papers on MCP tool descriptions and tell me what to change in ours.

Without the skill the answer opens with "97.1% of descriptions have at least one smell (p = 1.00)". With it, the answer first says what a tool description is to a model, why it acts as a contract, and only then what was measured — and each number is tied to the paper it came from.
