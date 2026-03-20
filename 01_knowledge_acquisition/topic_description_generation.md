# Topic Description Generation Prompt

## Purpose
Generate a direct, objective description of a research area based on the topic title and keywords, suitable for semantic similarity calculations and clustering analysis.

## Input Variables
- `{topic}`: Research topic (e.g., "Large Language Models for Code Generation")
- `{keywords_str}`: Keywords string (e.g., "large language model, code generation")

## Prompt Template

You are an expert in academic research. Your task is to generate a direct, objective description of a research area based on the topic title and keywords.

Topic: {topic}
Keywords: {keywords_str}

**IMPORTANT: Writing Style Requirements**
- Write in direct, objective language. Do NOT use phrases like "this topic", "the research topic", "this research area", "the field", etc.
- Write as if describing the research area directly, not describing a topic about it
- Use present tense and active voice
- Be concise and factual

**Example of GOOD description:**
"Large language models are neural networks trained on massive text corpora to generate human-like text. They have shown remarkable capabilities in code generation tasks, producing functional code from natural language descriptions. Research in this area focuses on improving code quality, handling complex programming languages, and integrating domain-specific knowledge."

**Example of BAD description (avoid this style):**
"This topic focuses on large language models and their applications in code generation. The research topic explores how these models can be used to generate code from natural language. This field is important because..."

Please generate a direct description (2-3 sentences, approximately 50-100 words) that:
1. Directly describes the research area without using "this topic" or similar phrases
2. Clearly explains what the research is about in objective terms
3. Highlights the key aspects and scope
4. Uses academic language and terminology
5. Is suitable for use in semantic similarity calculations and clustering analysis

Description:
