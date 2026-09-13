![explanatory-skill](docs/banner.png)

# explanatory-skill

**The problem.** You ask an agent to work through a pile of sources — code, papers, docs. It finishes the research and comes back with an answer, and the answer is a mess: terms, links, fragments of sentences. The agent has seen all 200 documents; you haven't. The answer makes sense to the agent and not to you, and you end up asking "explain", "I don't follow" again and again.

**The fix.** A fixed style of exposition where the topic opens up gradually: from the basics, where the concepts, the logic and the descriptions are introduced, down to the deeper subject matter. Whenever a definition or a term is used, the agent makes sure it was introduced earlier.

## Install

```bash
npx skills add mainpart/explanatory-skill -a claude-code -g -y
```

Or clone and run `claude --plugin-dir ./explanatory-skill`.

## Example

> Do research on how MCP servers are written and what the good ones do differently.

**Before:**

> The dominant finding is description smells: 97.1% of tools in the 856-tool sample have at least one, official and community servers are indistinguishable (adjusted p = 1.00). Augmentation helps only selectively — full augmentation is +5.85 pp at +67% steps. STRAP-style cursors and progressive disclosure beat `$defs` inlining, and `x-priority` hints improve routing when the tool count exceeds ~20.

What is a smell? Augmentation of what? What are STRAP, a cursor, `$defs`, `x-priority`, routing? The reader is handed the conclusions of five papers with none of the vocabulary they were written in.

**After:**

> When an agent is connected to an MCP server, it never reads the server's code. It sees three things per tool: a name, a short **description**, and a **schema** — the list of parameters with their types. From that text alone it decides which tool to call and with what. So the description isn't documentation for a human; it's the contract the agent executes.
>
> Because it's written last and in a hurry, that contract is usually flawed. Researchers borrowed a word from code review for this — a **smell**: a description that is vague, contradicts the schema, or leaves a parameter unexplained. On a sample of 856 public tools almost every description had at least one, and teams at large companies did no better than solo authors — the gap between them was too small to be **statistically significant**, meaning it could be chance.
>
> The obvious cure is to rewrite descriptions in full detail — the papers call this **augmentation**. Tested, it turned out to be a poor trade: accuracy rose by about six points, but the agent took half again as many steps to get there.
>
> The better-performing servers do something else. First, they shape their responses by a small set of conventions known as **STRAP** — one of which is that a tool returning a long list hands back a **cursor**, a token the agent passes to the next call to get the next page, instead of dumping everything at once. Second, they keep the first-level text short and reveal detail only when a tool is actually chosen — **progressive disclosure** — instead of expanding every nested type inline, the **`$defs` inlining** that bloats a schema. Third, once a server exposes more than about twenty tools, choosing the right one becomes a problem of its own, which the papers call **routing**; a marker in the tool's metadata saying which tools matter most — an **`x-priority`** hint — measurably helps.

Same papers, same numbers, much easier to read.
