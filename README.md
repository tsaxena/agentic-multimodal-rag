# Agentic Multimodal RAG for Long Documents

Research project exploring **agentic retrieval over long multimodal documents**.

The system uses OCR-based retrieval to search long documents and a vision-language model to inspect candidate pages. Unlike one-shot RAG, the agent can iteratively search, inspect evidence, reformulate queries, and decide when to answer or abstain.

## Research Question

Can an agent that actively searches and inspects long documents recover evidence missed by one-shot RAG and produce more grounded answers?

## Agent Actions

The initial agent exposes four actions:

* `SEARCH(query)` — retrieve candidate pages using OCR/text
* `INSPECT(page_id)` — inspect a page using its image and OCR text
* `ANSWER(answer, citations)` — return a grounded answer with page citations
* `ABSTAIN(reason)` — stop when sufficient evidence cannot be found

## Dataset

Initial evaluation will use **MMLongBench-Doc**, which contains long multimodal documents with question-answer pairs and gold evidence-page annotations.

## Initial Experiment

Compare:

1. **One-shot multimodal RAG**

   `question → retrieve top-k pages → VLM → answer`

2. **Agentic multimodal RAG**

   `search → inspect → assess evidence → reformulate/search again → answer`

The main metric of interest is whether agent-initiated follow-up searches recover gold evidence pages missed during initial retrieval.

## Status

Early research prototype.

See [`intent.md`](./intent.md) for goals, constraints, success criteria, and open questions.
