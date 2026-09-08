# Intent: Agentic Multimodal RAG for Long Documents

## Problem

One-shot RAG retrieves a fixed set of pages before generation.
For long multimodal documents, the initial retrieval may provide
incomplete evidence.

We want to investigate whether an agent can actively search,
inspect retrieved pages using a VLM, identify missing evidence,
reformulate its search, and retrieve again before answering.

## Goal

Build and evaluate an agent that controls retrieval over long
multimodal documents.

The agent can:

- SEARCH(query)
- INSPECT(page_id)
- ANSWER(answer, citations)
- ABSTAIN(reason)

OCR text is used for retrieval.
Page images + OCR are used for multimodal inspection.

## Dataset

MMLongBench-Doc.

## Primary experiment

Compare:

1. one-shot multimodal RAG
2. agentic iterative multimodal RAG

Primary question:

Can agent-initiated follow-up searches recover gold evidence pages
missed by the initial retrieval?

## Constraints

V1:
- page-level retrieval
- OCR retained
- VLM retained
- simple Python agent loop
- no SFT/RL
- no multi-agent
- no GraphRAG
- no production UI
- no production vector database

## Success Criteria

We can run both systems on the same benchmark subset and measure:

- evidence Recall@K
- answer correctness
- citation correctness
- retrieval recovery rate
- searches per question
- pages inspected per question

## Open Questions

- OCR implementation
- sparse/dense retrieval models
- fusion method
- reranker choice
- VLM choice
- exact subset of MMLongBench-Doc
- answer evaluator