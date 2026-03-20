你是一个文献综述分析专家，负责识别文献综述中的主要章节边界。

## 任务

请分析以下文本，**只识别一级章节（主章节）**的标题和结尾标识。每个一级章节应包含其所有子章节的内容。

## 要求

1. **只识别一级章节**：
   - 只识别主要章节（如Introduction, Related Work, Methods, Results, Conclusion等）
   - **不要识别子章节**（如2.1, 2.2等），这些子章节的内容应该包含在对应的主章节中
   - 识别Abstract、References等特殊章节（这些也视为一级章节）
   - **重要**：**即使某一大章节没有子章节**（如 Introduction、Conclusion 可能没有 1.1、1.2 或 7.1、7.2），也**必须**识别其边界并输出。不能因为该章不含子章节而遗漏。

2. **章节识别方式**：
   - 对于每个一级章节，你需要提供：
     - **section_number**：章节编号（如"1", "2", "3"等，不包含小数点后的数字）
     - **title**：章节标题（完整的标题文本，尽量精确匹配文本中的实际标题）
     - **end_keywords**：章节结尾的连续3-5个单词（用于定位章节结束位置）
   
   - **重要**：不要提供字符位置，而是提供：
     - 精确的章节标题文本（用于正则表达式匹配）
     - 章节结尾的连续单词（用于定位章节结束）

3. **章节结尾标识（非常重要）**：
   - **关键要求**：每个一级章节包含其所有子章节（如2.1, 2.2, 2.3, 3.1.1, 3.2.2等）的完整内容；**若某章没有子章节**，则其结尾为下一个一级章节标题之前的最后几个连续单词
   - 例如：如果"2. DEFINITIONS"章节包含子章节2.1, 2.2, 2.3，那么章节2的结尾应该是2.3结束之后、下一个一级章节（如"3. HALLUCINATION CAUSES"）开始之前的最后几个单词
   - **如何确定章节结尾**：
     1. 找到该章节的所有子章节（如4.1, 4.1.1, 4.1.2, 4.2, 4.2.1等）
     2. 找到最后一个子章节的结束位置
     3. 从最后一个子章节结束到下一个一级章节开始之间的内容，选择最后几个连续单词作为end_keywords
     4. 这些单词应该在该章节的最后一个完整段落或句子中
   - **特别重要**：对于最后一个章节，必须提供该章节实际结束位置的连续单词（所有子章节之后），而不是文本的结尾。这些单词应该在该章节内容的最后几段中，用于精确截断章节内容。
   - **如何选择end_keywords**：
     - 仔细阅读每个章节的内容，确保已经包含了所有子章节（如4.1, 4.2等）
     - 找到该章节的最后一个完整段落或句子（在所有子章节之后）
     - 选择该段落或句子中的连续3-5个有意义的单词作为end_keywords
     - 这些单词应该能够唯一标识章节的结束位置，避免选择章节中间或子章节中重复出现的短语
     - 对于最后一个章节，选择该章节最后一个完整段落中的连续单词（所有子章节之后），而不是整个文档的结尾

4. **完整性要求**：
   - 必须识别文档中的**所有**一级章节，从开头到结尾，不可遗漏
   - 典型的综述结构：Abstract / Introduction → 若干主体章节 → Conclusion / Future Directions → References，每一类都应被识别

5. **标题匹配**：
   - 提供的标题应该与文本中的实际标题尽可能一致
   - 包括大小写、标点符号等细节
   - 例如：如果文本中是"2. DEFINITIONS"，不要写成"2. Definitions"或"Definitions"

## 输出格式

请以JSON数组格式返回结果，格式如下：

```json
[
  {
    "section_number": "Abstract",
    "title": "Abstract",
    "end_keywords": ["paradigm", "shift", "in", "information", "acquisition"]
  },
  {
    "section_number": "1",
    "title": "1. INTRODUCTION",
    "end_keywords": ["understanding", "hallucinations", "in", "large", "language"]
  },
  {
    "section_number": "2",
    "title": "2. DEFINITIONS",
    "end_keywords": ["hallucinations", "in", "large", "language", "models"]
  },
  {
    "section_number": "3",
    "title": "3. HALLUCINATION CAUSES",
    "end_keywords": ["hallucination", "detection", "methods", "and", "benchmarks"]
  },
  {
    "section_number": "4",
    "title": "4. HALLUCINATION DETECTION AND BENCHMARKS",
    "end_keywords": ["future", "research", "directions", "on", "hallucinations"]
  }
]
```

**重要说明**：
- 只返回一级章节，不要返回子章节（如2.1, 2.2等）
- **title字段**：必须与文本中的实际标题完全一致（包括大小写、标点、空格等）
- **end_keywords字段**：提供章节结尾的连续3-5个单词，用于在文本中定位章节结束位置
- 每个一级章节应该包含其所有子章节的内容，直到下一个一级章节开始
- **最后一个章节的特殊要求**：
  - 最后一个章节的end_keywords必须提供该章节实际结束位置的连续单词
  - 这些单词应该在该章节内容的最后几段中，用于精确截断
  - 不要使用文本结尾的单词，而要使用该章节内容结束时的单词
  - 例如：如果最后一章是"4. HALLUCINATION DETECTION AND BENCHMARKS"，它的end_keywords应该是该章节内容结束时的几个连续单词，而不是整个文档结尾的单词

## 输入文本

{text}

## 输出要求

请直接返回JSON数组，不要添加任何说明、注释或Markdown代码块标记。只返回JSON数组内容。

