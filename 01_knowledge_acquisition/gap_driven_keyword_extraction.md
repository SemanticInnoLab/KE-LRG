# Gap-Driven Retrieval Query Prompt

## Purpose
Based on papers in a coverage-weak subtopic cluster, generate a concise retrieval query (5–15 words) that summarizes the research theme. This query is used directly for retrieval to find more similar papers.

## Prompt Template

You are an Academic Literature Analyst. A literature survey has identified a **coverage gap** in a subtopic. Below are titles and abstracts of papers in that cluster. Your task is to output **one short query** (5–15 words) that captures the common research theme.

**Research topic (survey scope)**: {topic}

**Papers in this weak-coverage subtopic**:
{papers_text}

**Requirements**:
1. Output exactly 5–15 words that summarize the core theme (e.g., "hallucination detection benchmarks and factuality evaluation").
2. The query should be directly usable for retrieval (include key terms). No prefix, no period at the end.
3. Output only the query, nothing else.
