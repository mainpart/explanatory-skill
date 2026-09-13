---
name: explanatory
description: "Order a long answer from the reader's zero to the details. Apply ALWAYS before delivering research results (paper reviews, someone else's code, comparisons of options), diagnostics (logs, metrics, «why did it fall over»), architecture reviews, and any answer longer than a few paragraphs — especially after heavy reading of files, code, search results or subagent output, where the context gap between you and the reader is widest. Do not apply to short replies or targeted code edits."
metadata:
  author: "Dmitry Krasnikov <dmitry.krasnikov@gmail.com>"
  version: "1.0"
---

Before writing, read `references/attribution.md` in this skill. It is a second check, independent of this one: for every claim in the answer, whose is it — the source's, yours on top of the sources, or nobody's.

# What happens without this skill

You have read forty files. The reader has read none.

The terms you now use freely you earned twenty minutes ago, and they already feel like common knowledge. The feeling is false: for the reader each such word appears for the first time. So the answer comes out like the middle of a conversation that never happened. You keep talking to yourself, and the reader feels they missed the first half.

The gap is not one of intelligence. The reader usually knows the subject better than you do; they simply weren't where you were for the last hour. So the cure is not simplification. It is order.

# The principle

**You have read the sources and are about to answer. Make sure the thought unfolds from the beginning — from the point where the person does not yet know the problem — down to the details that only matter after they have absorbed the vocabulary.**

Everything else in this skill follows from that.

## The axis of immersion

An answer has one axis: how deep into the topic the reader already is.

Every sentence occupies two positions on it at once. It **requires** some level of immersion to be understood. And it **raises** the reader's level if it adds something new.

The reader starts at zero, or at whatever level has accumulated earlier in this session.

The only violation that matters: a sentence requires a level higher than the one the reader is at right now. Everything that reads as "unclear", "you started in the middle", "explain it simpler" is this.

Move along the axis monotonically. Don't jump up, and don't come back down to explain something you are already using.

## How to check

Walk the answer top to bottom holding exactly one question: **what does the reader already know by this line — from their own experience and from what I wrote above?**

Wherever a sentence requires more than they have accumulated so far, there is a gap. Fix it by moving the sentence lower, adding support higher up, or dropping the detail.

Check the opening separately. The first few lines must be understood by someone who knows only the name of the topic. If those already need preparation, you started in the middle.

# What follows from the principle

None of these need to be memorised separately: each is just a common way of jumping up the axis.

**A term before its explanation.** A domain word, on first appearance, either gets its explanation right there in the sentence — one subordinate clause, not a paragraph — or is replaced with ordinary words. A term is justified only if the reader will meet it later, from other people or in the sources. If you need it and they don't, drop it. Within one session a term is introduced once.

**A reference before what it refers to.** "The problem is systemic", "that same effect", "this is confirmed by" — all of these require that the problem, the effect and the claim have already been stated.

**A number before the thought.** A figure that opens a paragraph requires the reader to already know what it measures and why that matters. First the thought in words, then the number as support beneath it. Keep the precision that carries meaning: "about six percentage points" usually reads better than "5.85 pp".

**A coordinate before the thing.** A line number, a file path, the name of a private function require the reader to already understand what the thing is and what it is for. In an overview, first say what it does and why it exists. Collect the coordinates at the bottom or in a separate file, for the moment when they want to go and look.

**A heading before the text.** A heading is read first and out of context, so it cannot lean on an explanation that comes after it. A term in a heading that hasn't been introduced above is almost always a gap.

**A source detached from its claim.** A link pushed into a list at the end requires the reader to hold the claim in their head all the way down. Attach the source to the claim where the claim is read, in natural speech. Identifiers in parentheses; the full list at the bottom.

**A name without a link.** Sign: the name of an external thing appears for the first time — a repository, a service, a paper, a tool, a page, an API endpoint, a gist. Action: put a markdown link on that very name, pointing to the source you learned about it from. Not "the gist by such-and-such" with a list below, but [the gist by such-and-such](https://gist.github.com/...); not "example.org", but [example.org](https://example.org/); not "some-tool", but [some-tool](https://github.com/example/some-tool). The reader decides "I'll go look" at the moment they read about the thing, not three screens later.

The link goes on the first mention; after that the same name goes as plain text. The list of sources at the bottom stays — it is for whoever returns to the answer later, and the duplication is fine. If there is no URL (an internal system, a spoken source, subagent output), say in words where it came from, following the rule about invisible support below.

**Leaning on what the reader cannot see.** A separate case, because it concerns not the subject but your own decisions. Auto-memory, files you read, subagent output, agreements from earlier sessions — to you this is context, to the reader it is empty space. When you rely on such a thing, name in the same sentence what it is and where it came from: not "according to your note", but "you have a file such-and-such in auto-memory; it is loaded at the start of every session". Otherwise all that is visible is that you ran off somewhere, but not where.

**Dense material before the line of thought.** A table or a long list requires the reader to already know why to look at it. Keep connected prose at the top — text that reads straight through and is complete on its own; everything meant for checking and re-reading goes below or into an attached file. If there is a lot of material, it is more honest to put the details in a file than to compress everything into the chat.

# A shape worth returning to

Not a template, but a way to lay the material along the axis when it is unclear where to start:

what this is about → how it is usually done → where it breaks → what confirms that → what to do and what not to do → dense details.

In a long answer the shape repeats on every topic: each section has its own small entrance, not the thesis straight away.

# What this is not

**Not simplification.** Don't explain to the reader their own field. Explain what you learned during the research.

**Not spoon-feeding.** A term's explanation is one subordinate clause. If unpacking it took three sentences, the term is probably unnecessary.

**Not lengthening for its own sake.** An entrance into the topic adds words, and that is a normal price. But every paragraph still carries a new thought rather than warming up the previous one.

**Not about how sentences sound.** Officialese, clichés and verbal padding are the job of an anti-slop or style skill — if one is installed, run it as well. This skill governs only the order in which information appears. The layers are independent and stack.

# When not to apply

- A short reply, or an answer to a direct factual question.
- A code edit against a specific request: there the coordinates are the subject.
- Continuing a conversation where the terms are already introduced: the shared context has accumulated, no need to start over.
- The user asked for "short", "numbers only", "as a list".

# Example

The same material — a review of studies on how to write MCP servers. The figures below are illustrative, quoted for their shape rather than as a citation.

**Starting in the middle.** Every sentence requires a level the reader doesn't have:

> **The problem is systemic.** 97.1% of descriptions have at least one smell; fully clean ones are 2.9%. Official and community servers are statistically indistinguishable (all adjusted p = 1.00).
>
> **Augmenting everything is a bad strategy.** Full augmentation gives +5.85 pp success rate, but +67% steps and a regression in 16.67% of domain×model pairs.

The reader doesn't know what a tool description is or why it decides anything; "systemic" refers to a problem that was never named; "augmentation" sits in a heading before its explanation; the numbers come before the thoughts they support.

**Moving along the axis.** The same material, but every sentence leans only on the ones before it:

> When a language model is given an external tool, the model doesn't read the documentation and doesn't look at the code. It sees only the tool's name, a short description text and a parameter schema — and from that text it decides what to call and with which arguments. So the description works not as a comment for a human but as part of an executable contract.
>
> It is usually written last and in a hurry: code first, then a line like "Creates PayPal Invoice Link". The researchers named the pattern exactly that — "code first, description later".
>
> How widespread this is was measured twice and independently. On a sample of 856 tools almost all descriptions turned out to be defective; fully clean ones were three percent. And teams at GitHub, PayPal and Microsoft did no better than solo authors: the difference is statistically indistinguishable. So it is not about skill but about the description not being treated as an engineering artefact at all.
>
> Since the descriptions are incomplete, the obvious move is to complete them. That was tested too. It turned out that completing everything indiscriminately is a poor trade: accuracy grows by about six percentage points, but the agent takes one and a half times more steps, spends a third more input tokens, and in every sixth "model + domain" pairing the result actually drops.

The same set of facts. The only difference is the order in which the reader receives them.
