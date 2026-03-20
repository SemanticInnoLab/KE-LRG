# Outline Extraction Prompt

## Purpose
Extract primary (level 1) and secondary (level 2) section titles from survey papers, including brief descriptions.

## Prompt Template

Extract the primary (level 1) and secondary (level 2) section structure from the following survey paper.

Paper Title: $title
Paper Abstract: $abstract

Paper Content:
$content

Output Requirements:
1. Extract ONLY primary sections (level 1) and secondary sections (level 2). Do NOT extract level 3 or deeper sections.
2. Output in JSON format only, no additional text or explanations.
3. Section numbering: primary sections use numbers (e.g., "1", "2"), secondary sections use "number.number" (e.g., "1.1", "1.2").
4. Include a brief description for each section (1-2 sentences, maximum 200 characters). The description should summarize the main content or purpose of that section.
5. If a section has no subsections, set subsections to an empty array.

Output JSON Format:
{{
  "title": "Paper Title",
  "sections": [
    {{
      "section_number": "1",
      "title": "Introduction",
      "description": "Brief description of the introduction section (1-2 sentences, max 200 chars)",
      "subsections": [
        {{
          "section_number": "1.1",
          "title": "Background",
          "description": "Brief description of the background subsection (1-2 sentences, max 200 chars)",
          "subsections": []
        }},
        {{
          "section_number": "1.2",
          "title": "Motivation",
          "description": "Brief description of the motivation subsection (1-2 sentences, max 200 chars)",
          "subsections": []
        }}
      ]
    }},
    {{
      "section_number": "2",
      "title": "Methods",
      "description": "Brief description of the methods section (1-2 sentences, max 200 chars)",
      "subsections": [
        {{
          "section_number": "2.1",
          "title": "Method A",
          "description": "Brief description of method A (1-2 sentences, max 200 chars)",
          "subsections": []
        }}
      ]
    }}
  ]
}}

