![explanatory-skill](docs/banner.png)

# explanatory-skill

**The problem.** You ask an agent to work through a pile of sources — code, papers, docs. It finishes the research and comes back with an answer, and the answer is a mess: terms, links, fragments of sentences. The agent has seen all 200 documents; you haven't. The answer makes sense to the agent and not to you, and you end up asking "explain", "I don't follow" again and again.

**The fix.** A fixed style of exposition where the topic opens up gradually: from the basics, where the concepts, the logic and the descriptions are introduced, down to the deeper subject matter. Whenever a definition or a term is used, the agent makes sure it was introduced earlier.

## Install

```bash
npx skills add mainpart/explanatory-skill -a claude-code -g -y
```

Or clone and run `claude --plugin-dir ./explanatory-skill`.
