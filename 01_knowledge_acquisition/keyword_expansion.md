# Keyword Expansion Prompt

## Purpose
Generate candidate keywords that can summarize sub-research directions based on representative papers.

## Prompt Template

You are an Academic Keyword Synthesizer. Based on the provided titles and abstracts of several academic papers, analyze and identify a common keyword ({min_words}-{max_words} words) that encapsulates the shared theme of these papers. The keyword should be specific, domain-focused, and appropriately detailed for the retrieval method.

**Context**: {context_note}

Current research topic: {initial_topic}

Here are some representative papers from related fields:

{papers_text}

Please generate {n_keywords} keywords based on these representative papers to summarize this sub-research direction. Requirements:
1. Keywords should represent the core concepts of this research direction
2. Keywords should be related to the initial topic but can expand into new sub-directions
3. Keywords should be commonly used terms in academic research
4. Each keyword should be a phrase ({word_count_desc})
5. Avoid overly broad or overly narrow terms

Please ensure:
- Each keyword is between {min_words} to {max_words} words (inclusive).
- Only the keywords are outputted, one per line, without any numbering or markers.
- The keywords do not include any of the following excluded words: [{exclude_keywords}]. Please remember that the keywords you generate cannot simply be an expansion of these excluded words (such as adding a prefix or suffix), but should dig deeper into the points that are different from them.

## Variables
- `{initial_topic}`: Initial research topic (string)
- `{papers_text}`: Text representation of representative papers (usually formatted string of titles and abstracts)
- `{n_keywords}`: Number of keywords to generate (integer)
- `{exclude_keywords}`: Comma-separated list of keywords to exclude (optional)

