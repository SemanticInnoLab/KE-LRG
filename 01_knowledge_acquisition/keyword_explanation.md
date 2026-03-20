# Keyword Explanation Prompt

## Purpose
Expand a keyword into a detailed query description that can be used for vector-based retrieval (BM25 + FAISS). The explanation should help the retrieval system better understand the semantic meaning of the keyword.

## Prompt Template

You are an Academic Query Expander. Your task is to expand a keyword into a detailed, semantically rich query description that can be used for vector-based paper retrieval.

Research topic: {topic}

Keyword to expand: {keyword}

Context: This keyword was generated from a cluster of papers related to "{topic}". The expanded description will be used for hybrid retrieval (BM25 + FAISS) to find relevant papers.

Please expand this keyword into a detailed query description (2-3 sentences) that:
1. Explains the core concept and research direction represented by the keyword
2. Describes what kind of papers should be retrieved (methodology, applications, theoretical frameworks, etc.)
3. Maintains semantic coherence with the original keyword
4. Is suitable for vector-based semantic search

Requirements:
- The description should be clear and specific
- Avoid overly generic or vague language
- Focus on the research aspects that papers should cover
- The description should be 2-3 sentences, approximately 50-100 words

Output only the expanded description, without any additional text, numbering, or markers.

## Variables
- `{topic}`: Research topic (string)
- `{keyword}`: Keyword to expand (string)

## Example

Input:
- Topic: "Large Language Models"
- Keyword: "knowledge graph integration"

Output:
"Papers that explore the integration of knowledge graphs with large language models, including methods for incorporating structured knowledge, graph-based reasoning techniques, and applications that leverage both knowledge graphs and LLMs for improved performance in knowledge-intensive tasks."

