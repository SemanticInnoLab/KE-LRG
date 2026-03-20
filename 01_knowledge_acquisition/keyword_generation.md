# Keyword Generation Prompt

## Purpose 1: Generate Initial Keywords from Topic

Generate initial keywords from a research topic. The keywords will be used for {retrieval_method_desc}.

### Input Variables
- `{topic}`: Research topic (e.g., "Large Language Models for Code Generation")
- `{num_keywords}`: Number of keywords to generate (default: 2)

### Prompt Template

- Background: {context_note}
- Skills: You have the ability to analyze research topics, understand their core themes, and generate keywords that are both specific enough to be meaningful and appropriately detailed for the retrieval method.
- Goals: Generate {num_keywords} keywords that together accurately represent the research topic and are suitable for {retrieval_method_desc}.

**Critical Requirements:**
1. Generate exactly {num_keywords} keywords
2. **MANDATORY - Word Count**: Each keyword MUST be between {min_words}-{max_words} words (inclusive). Keywords with fewer than {min_words} words or more than {max_words} words are INVALID. {word_count_preference}
3. **Keyword Coherence**: ALL keywords must be tightly related to the core research theme. They should form a coherent set that together accurately represents the topic.
4. **Appropriate Detail Level**: {detail_level_note}
5. **Avoid Generic Terms**: Do NOT include overly broad or generic terms (e.g., "artificial intelligence", "machine learning", "deep learning") unless they are essential and directly related to the specific topic.
6. **Thematic Consistency**: If the topic involves a specific problem, ensure ALL keywords relate to that problem in the context of the main subject.
7. Use lowercase letters and separate words with spaces.
8. Return only the keywords, one per line, without numbering, bullets, or any additional text.

**Examples:**
- Topic: "Hallucination in Large Language Models"
  - GOOD (for keyword retrieval): "large language model", "hallucination detection method", "factual accuracy evaluation"
  - GOOD (for hybrid retrieval): "large language model hallucination detection", "factual accuracy evaluation method", "false information generation prevention"
  - BAD: "large language model" (only 3 words, too concise for hybrid), "hallucination detection" (only 2 words), "artificial intelligence" (too broad)

- Topic: "LLM for Code Generation"
  - GOOD (for keyword retrieval): "large language model", "code generation system", "program synthesis method"
  - GOOD (for hybrid retrieval): "large language model code generation system", "program synthesis using neural networks", "automated software development with AI"
  - BAD: "large language model" (only 3 words, too concise for hybrid), "code generation" (only 2 words), "natural language processing" (too broad)

Topic: {topic}

Keywords:

---

## Purpose 2: Generate Keywords from Clustered Papers (Used in Iterative Retrieval)

Generate new keywords based on clustered papers during iterative retrieval. The keywords will be used for {retrieval_method_desc}.

### Input Variables
- `{exclude_keywords}`: Comma-separated list of existing keywords to exclude
- `{papers_text}`: Formatted text containing titles and abstracts of sampled papers from the cluster

### Prompt Template

You are an Academic Keyword Synthesizer. Based on the provided titles and abstracts 
of several academic papers, analyze and identify a common keyword ({min_words}-{max_words} words) that 
encapsulates the shared theme of these papers.

**Context**: {context_note}

The keyword should:
1. Represent the core concept of this research direction
2. Be a phrase ({word_count_desc})
3. Use commonly used academic terminology
4. Capture the shared research theme across the provided papers
5. {detail_level_note}

Important constraints:
- The keyword should NOT include any of the following excluded words: {exclude_keywords}
- The keyword you generate cannot simply be an expansion of these excluded words
- The keyword should provide a distinct perspective or sub-direction
- The keyword MUST be between {min_words} to {max_words} words (inclusive)

Here are the titles and abstracts of the papers:

{papers_text}

Please provide ONLY the keyword phrase ({min_words}-{max_words} words), without any additional explanation, numbering, or formatting.
