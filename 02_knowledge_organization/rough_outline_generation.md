# 粗糙大纲生成Prompt模板

You are an AI assistant tasked with creating a concise, high-level, comprehensive and original academic survey outline for $topic. This is a critical task, as the outline you generate will serve as the foundation for a high-quality, comprehensive academic survey paper suitable for submission to top-tier journals in the field. The structure and content you provide will directly influence the quality and coherence of the final paper, so your work here is of utmost importance.

You are provided with two sets of information:

1. Titles, abstracts, top-level outlines and publication dates of human-written surveys that may be related to $topic. Use these to understand the logical structure, style, and academic phrasing typical in this field.
   ---
   $survey_list
   ---

2. Titles, abstracts and publication dates of academic papers that may be related to $topic. Use these to identify key themes, recent developments, and research trends in the field.
   ---
   $paper_list
   ---

**Important Notes:**
- Concise Top-level Outline: The first-level outline should be highly condensed and abstract, representing high-level categories.
- Utilize Information Sources: Draw inspiration from the structure and style of the human-written surveys while incorporating the content and trends from the academic papers to create a comprehensive and up-to-date outline.
- Critical Importance of Descriptions: The descriptions you provide for each section are crucial. They will be used directly for retrieving relevant academic papers and generating more detailed second-level outlines in subsequent stages. Structure these descriptions as bullet points, each representing a key aspect or sub-domain to be explored.

**Main Task:**
Create a comprehensive, original, and academically rigorous survey outline for $topic. The outline should include a title and approximately $section_num high-level, abstract sections that encapsulate broad categories of the topic, following the structure typical of academic surveys in this field. Ensure your outline is both well-structured and current.

**Important Academic Guidelines:**
1. **Relevance and Focus**: Ensure every section directly relates to $topic, covering its breadth including recent developments and historical context.
2. **Originality and Critical Analysis**: Provide new perspectives that go beyond summarizing existing work. Draw inspiration from provided sources without directly copying their structure.
3. **Logical Structure**: Follow a typical academic survey progression: introduction, main body sections, and conclusion with future directions.

{NORM_PLACEHOLDER}

**Additional Guidelines:**
1. **Comprehensive Coverage and Gap Identification**: While being aware that the provided paper list is only a subset of the entire field, strive to cover all important aspects of $topic. At the end of your outline, include a section titled 'Potential Gaps and Future Research Directions' to address areas that might be underrepresented but could be important to the field.

**Your outline should contain a title and approximately $section_num sections.**

Each section should be followed by:
- A **Description** consisting of a informative description and **2-4** bullet points, the number of points per subsection does not need to be consistent, you can consider adding or reducing points. Each bullet point should represent a key aspect or sub-domain of the section, followed by a Informative description.
- It is important to note that there is no overlap between bullet points, which represent different aspects of the section
- **Do not use abbreviations or acronyms in the descriptions**. Always write out full terms to ensure clarity and aid in future retrieval processes
- Ensure all terms are fully written out without abbreviations or acronyms.

**Return in JSON format only, without any other text or explanations:**

```json
{
  "title": "Title of the survey on topic",
  "sections": [
    {
      "section_number": "1",
      "title": "Introduction",
      "description": "Informative description of Introduction",
      "key_points": [
        "Informative description of key aspect or sub-domain 1 of Introduction",
        "Informative description of key aspect or sub-domain 2 of Introduction"
      ]
    },
    {
      "section_number": "2",
      "title": "Name of Section 2",
      "description": "Informative description of Section 2",
      "key_points": [
        "Informative description of key aspect or sub-domain 1 of Section 2",
        "Informative description of key aspect or sub-domain 2 of Section 2"
      ]
    },
    ...
    {
      "section_number": "K",
      "title": "Conclusion",
      "description": "Informative description of Conclusion",
      "key_points": [
        "Informative description of key aspect or sub-domain 1 of Conclusion"
      ]
    },
    {
      "section_number": "K+1",
      "title": "Potential Gaps and Future Research Directions",
      "description": "Areas that might be underrepresented but could be important to the field",
      "key_points": [
        "Potential gap or future direction 1",
        "Potential gap or future direction 2"
      ]
    }
  ]
}
```

