---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/writing/shareable/context-window-is-not-memory"
doc_type: "essay"
doc_status: "draft"
title: "The Context Window Is Not Your Memory"
description: "A short piece on why tree-structured files, agent specs, logs, and git"
memory_eligible: false
memory_priority: "low"
doc_tags:
  - "domain:writing"
  - "visibility:public"
  - "type:essay"
---
# The Context Window Is Not Your Memory

Most AI workflows still rely on an illusion: if you stuff enough text into the
prompt, the model will somehow remember your system.

That works for a demo. It does not work for a life.

A context window is a working set, not a durable memory layer. It is useful
because it gives the model a temporary view of the problem in front of it. It
is not useful as the primary place where your operating system lives. The
moment the session ends, or the prompt gets too large, or the next task pulls
in different context, that "memory" is gone.

That is the reason I care so much about file structure.

If your system lives in a tree of files, an agent can recover the right context
without reloading your whole life. The folder structure does part of the
routing. `health/` is different from `journal/`. `memory/` is different from
`writing/`. A root `AGENT.md` defines the broad contract, and local
`AGENT-*.md` files narrow the task. Instead of one giant immortal prompt, you
get a layered system that can load only what matters.

That structure matters because retrieval quality is not just about search. It
is about scope. Good context loading means the assistant can start from the
general rules, walk down the tree, and stop before the window fills with junk.
The hierarchy is doing real work. It reduces ambiguity, keeps the active
context tight, and makes the next action more predictable.

The second piece is persistence.

Prompts are cheap. Logs are memory.

If a useful decision only lives in chat, it may as well not exist next week.
So the system needs places where the AI writes things back out: daily summaries,
conversation milestones, agent-managed memory notes, implementation plans,
reference docs, and other markdown artifacts that survive the session. The
point is not to save everything. The point is to save the parts that should
compound.

Git finishes the loop.

I usually commit and push the prompt scaffolding, the agent files, and the
derived notes because that is what turns a one-off chat into durable operating
state. Version control gives the memory layer history. You can inspect why a
prompt changed, when a workflow tightened up, or how a domain contract evolved.
Without that, prompt engineering is mostly theater. You have text, but not a
system.

This is also why I think "memory" in AI is often underspecified. People talk
about vector databases, summaries, and long context as if they are substitutes.
They are useful tools, but they do not replace a legible filesystem and a
habit of writing important state back to files. The model still needs a stable
place to stand.

My current view is simple:

- the context window is for active work
- the file tree is for routing and boundaries
- memory logs are for durable state
- git is for history and trust

Once you treat those as different layers, the whole system gets more reliable.
The assistant stops feeling like a chatbot with amnesia and starts feeling more
like software that can pick up where it left off.
