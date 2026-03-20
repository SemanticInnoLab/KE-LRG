# 提示词目录整理

本文档按功能对项目中的提示词模板进行整理，便于在 GitHub 中快速定位相关文件。

## 一、对比实验提示词

这组提示词用于基线实验，不属于 full 工作流主链路。

### 1. Direct-Gen / AutoGen

- 路径：`prompt_package/00_baselines/baseline_direct_gen_latex.md`
- 作用：不依赖分阶段知识组织与治理链路，直接生成整篇综述正文。

### 2. RAG-Gen / RAGBase

- 路径：`prompt_package/00_baselines/baseline_rag_gen_latex.md`
- 作用：基于检索材料直接生成整篇综述正文，用于与 full 工作流比较。

## 二、知识获取类智能体提示词

### 1. 检索与查询扩展

- `prompt_package/01_knowledge_acquisition/keyword_generation.md`
  - 根据主题生成检索关键词。
- `prompt_package/01_knowledge_acquisition/keyword_expansion.md`
  - 根据论文簇扩展关键词。
- `prompt_package/01_knowledge_acquisition/keyword_explanation.md`
  - 将关键词扩展为更可检索的自然语言解释。
- `prompt_package/01_knowledge_acquisition/gap_driven_keyword_extraction.md`
  - 基于覆盖缺口生成补检索关键词。
- `prompt_package/01_knowledge_acquisition/topic_description_generation.md`
  - 生成主题描述，辅助后续检索与组织。

### 2. 论文识别与内容抽取

- `prompt_package/01_knowledge_acquisition/paper_type_classification.md`
  - 识别论文类型。
- `prompt_package/01_knowledge_acquisition/paper_summary.md`
  - 生成论文摘要或中间表征。
- `prompt_package/01_knowledge_acquisition/method_attribute_tree.md`
  - 抽取方法类论文的属性树。
- `prompt_package/01_knowledge_acquisition/theory_attribute_tree.md`
  - 抽取理论类论文的属性树。
- `prompt_package/01_knowledge_acquisition/benchmark_attribute_tree.md`
  - 抽取 benchmark 类论文的属性树。
- `prompt_package/01_knowledge_acquisition/survey_attribute_tree.md`
  - 抽取综述论文的属性树。

### 3. 写作规范库与章节画像抽取

- `prompt_package/01_knowledge_acquisition/detect_section_boundaries.md`
  - 识别综述中的一级章节边界。
- `prompt_package/01_knowledge_acquisition/extract_section_profile.md`
  - 抽取章节画像与写作行为特征。
- `prompt_package/01_knowledge_acquisition/canonicalize_section_types.md`
  - 将章节类型归一化为统一类别。
- `prompt_package/01_knowledge_acquisition/structure_norm.md`
  - 抽取章节结构规范。
- `prompt_package/01_knowledge_acquisition/mounting_norm.md`
  - 抽取章节挂载规范。
- `prompt_package/01_knowledge_acquisition/extract_claim_templates.md`
  - 抽取典型论断表达模板。
- `prompt_package/01_knowledge_acquisition/extract_citation_policy.md`
  - 抽取引用策略与引用要求。
- `prompt_package/01_knowledge_acquisition/clean_text.md`
  - 对综述文本进行规范化清洗。
- `prompt_package/01_knowledge_acquisition/norm_repair.md`
  - 修复或补全规范抽取结果。
- `prompt_package/01_knowledge_acquisition/map_section_to_norm.md`
  - 将当前大纲映射到规范库中的章节类型。

## 三、知识组织类智能体提示词

### 1. 一级大纲生成与合并

- `prompt_package/02_knowledge_organization/rough_outline_generation.md`
  - 生成候选一级大纲。
- `prompt_package/02_knowledge_organization/outline_merging.md`
  - 合并多个候选一级大纲。

### 2. 一级挂载

- `prompt_package/02_knowledge_organization/mount_paper_on_outline.md`
  - 将论文挂载到一级大纲章节。

### 3. 二级大纲与二级挂载

- `prompt_package/02_knowledge_organization/secondary_outline_generation.md`
  - 生成二级大纲。
- `prompt_package/02_knowledge_organization/mount_paper_on_secondary_outline.md`
  - 将论文挂载到二级大纲。

### 4. 其他组织类辅助模板

- `prompt_package/02_knowledge_organization/outline_extraction.md`
  - 从文本中抽取大纲结构。
- `prompt_package/02_knowledge_organization/outline_extraction_continue.md`
  - 在长文本场景下继续抽取大纲。
- `prompt_package/02_knowledge_organization/literature_review.md`
  - 面向综述结构整理的通用模板。
- `prompt_package/02_knowledge_organization/survey_classification.md`
  - 对综述类型进行分类。
- `prompt_package/02_knowledge_organization/cluster_analysis.md`
  - 对检索结果或论文簇进行结构化分析。

## 四、内容生成类智能体提示词

### 1. 正文生成

- `prompt_package/03_content_generation/fulfill_content_iteratively.md`
  - 按小节逐步生成综述正文。
- `prompt_package/03_content_generation/write_section_words.md`
  - 生成章节衔接或章节性文字。
- `prompt_package/03_content_generation/write_abstract.md`
  - 生成摘要。

### 2. 正文精炼

- `prompt_package/03_content_generation/lce_refine.md`
  - 对正文进行 LCE 精炼。

## 五、知识治理类智能体提示词

### 1. 论断核查

- `prompt_package/04_knowledge_governance/claim_decomposition.md`
  - 将句子分解为可核查的 atomic claims。
- `prompt_package/04_knowledge_governance/evidence_verification.md`
  - 检查论断与证据是否匹配。

### 2. 补引与改写

- `prompt_package/04_knowledge_governance/add_cite_from_rag.md`
  - 基于检索证据补充引用。
- `prompt_package/04_knowledge_governance/add_cite_for_claim.md`
  - 面向具体 claim 补充引用。
- `prompt_package/04_knowledge_governance/rewrite_unsupported.md`
  - 对证据不足但可修复的表述进行改写。
- `prompt_package/04_knowledge_governance/rewrite_unsupported_no_evidence.md`
  - 对缺少充分证据的表述进行更保守的改写。

## 六、阅读建议

如果希望快速理解整套提示词系统，建议按以下顺序阅读：

1. 先读 `paper_project/docs/prompt_system_overview.md`
2. 再读本文档，了解各模板的路径与功能
3. 若需要论文附录材料，再查看完整的附录式整理文件
