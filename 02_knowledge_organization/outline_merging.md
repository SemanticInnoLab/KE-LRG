# 大纲合并Prompt模板

You are an AI assistant tasked with creating a concise, high-level, comprehensive and original academic survey outline for $topic. This is a critical task, as the outline you generate will serve as the foundation for a high-quality, comprehensive academic survey paper suitable for submission to top-tier journals in the field. The structure and content you provide will directly influence the quality and coherence of the final paper, so your work here is of utmost importance.

You are provided with two sets of information:

1. Titles, abstracts, top-level outlines and publication dates of human-written surveys that may be related to $topic. Use these to understand the logical structure, style, and academic phrasing typical of academic survey papers written by humans.
  
   ---
   $survey_list
   ---

2. AI-generated outlines from subsets of papers related to $topic, each containing:
   - Title
   - Sections 
   - Descriptions for each section (a informative description and some bullet points)
   - "Potential Gaps and Future Research Directions" section

   ---
   $outline_list
   ---

**Main Task:**
Generate a final, cohesive top-level outline for $topic by merging and refining the provided AI-generated outlines. Focus on creating an accurate structure with precise, informative section descriptions that will help the subsequent RAG (Retrieval-Augmented Generation) and second-level outline generation. Remember, this outline will be the backbone of a high-quality academic survey paper, so maintain the highest standards of academic rigor and comprehensiveness.
You need to generate a final outline based on these provided outlines to make the final outline show comprehensive insights of the topic and more logical.

**Instructions:**
1. Structure:
   - Start with an **Introduction** section
   - Include approximately **$section_num main body sections**
   - End with a **Conclusion** section
   - Ensure logical flow and comprehensive coverage of $topic

2. Content:
   - Prioritize and consolidate key themes from AI-generated outlines
   - Eliminate redundancies and overlaps between sections
   - Ensure each section has a distinct focus and purpose

3. Descriptions:
   - In general, for each section, provide a brief yet informative description and **several sub-domain points with informative sub-description**, the number of points per subsection does not need to be consistent. You can add or subtract according to the actual scope of the section
   - Each bullet point should represent a key aspect or sub-domain of the section, followed by a Informative description
   - Ensure descriptions are broad enough to cover the section topic but specific enough. It is important to avoid duplication in the description of sub-domains in each section
   - Avoid repetition of concepts across different sections

4. Precision and Academic Standards:
   - Ensure each section and description relates directly to $topic
   - Maintain a logical progression of ideas throughout the outline
   - Use academically appropriate terminology and phrasing
   - Avoid detailed content generation - focus on accurate structural representation and guiding descriptions
   - **Do not use abbreviations or acronyms in the descriptions**. Always write out full terms to ensure clarity and aid in future retrieval processes

5. Consistency and Coherence:
   - Create clear distinctions between sections to avoid overlap. It is important to note that there is no overlap between bullet points, which represent different aspects of the section
   - If a topic appears in more than one section or the descriptions of sub-domains, clearly distinguish the context and relevance of each section. If necessary, you can choose to remove or merge

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
      "section_number": "K-1",
      "title": "Name of Section K-1",
      "description": "Informative description of Section K-1",
      "key_points": [
        "Informative description of key aspect or sub-domain 1 of Section K-1",
        "Informative description of key aspect or sub-domain 2 of Section K-1"
      ]
    },
    {
      "section_number": "K",
      "title": "Conclusion",
      "description": "Informative description of Conclusion",
      "key_points": [
        "Informative description of key aspect or sub-domain 1 of Conclusion"
      ]
    }
  ]
}
```

