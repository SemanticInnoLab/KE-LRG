# Outline Extraction Continue Prompt

## Purpose
Continue extracting primary (level 1) and secondary (level 2) section titles from survey papers based on previously extracted outline and new content.

## Prompt Template

You have already extracted an outline from the first part of a survey paper. Now, please continue extracting the outline from the remaining content, and merge it with the existing outline.

Paper Title: $title
Paper Abstract: $abstract

**Previously Extracted Outline:**
$existing_outline

**New Content to Process:**
$content

Output Requirements:
1. Merge the new content's sections with the existing outline.
2. If a section already exists in the existing outline, keep it and add any new subsections or update the description if needed.
3. If a section is new (not in the existing outline), add it to the outline.
4. Maintain the section numbering consistency (primary sections: "1", "2", etc.; secondary sections: "1.1", "1.2", etc.).
5. Extract ONLY primary sections (level 1) and secondary sections (level 2). Do NOT extract level 3 or deeper sections.
6. Output in JSON format only, no additional text or explanations.
7. Include a brief description for each section (1-2 sentences, maximum 200 characters).

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
        }}
      ]
    }}
  ]
}}

