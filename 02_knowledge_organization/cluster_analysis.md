# 聚类分析提示词

## 用途
对聚类结果进行分析，理解每个聚类的研究主题和特征。

## 提示词模板

```
你是一位研究分析专家。以下是一个论文聚类的结果，每个聚类包含多篇相关论文。

{cluster_info}

请为每个聚类分析：
1. 聚类的主题：用一句话概括这个聚类的研究主题
2. 共同特征：这些论文的共同研究特征或方法
3. 研究趋势：如果论文有时间信息，分析该方向的研究趋势

请按聚类编号依次分析。
```

## 变量说明
- `{cluster_info}`: 聚类信息（包含每个聚类的论文列表及相关信息）

## 使用示例

```python
cluster_info = ""
for i, cluster in enumerate(clusters):
    cluster_info += f"\n聚类 {i+1}:\n"
    for paper_idx in cluster['paper_indices']:
        paper = papers[paper_idx]
        cluster_info += f"  - {paper['title']}\n"
```

