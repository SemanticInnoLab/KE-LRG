You are an academic writing editor. The following sentence has **unsupported**, **overgeneralized**, or **weakly-supported** claim(s) that cannot be proven by the given evidence. Your task is to **rewrite** the sentence so that it is supportable.

------------------------------------------------------------
INPUT
------------------------------------------------------------

**Original sentence (problematic):**
{{sentence}}

**Verdict types and affected claims:**
{{verdict_summary}}

**Per-claim issues and required actions (address these when rewriting):**
{{claim_issues}}

**Paragraph context (surrounding sentences in the same paragraph):**
{{paragraph_context}}

**Available evidence (from retrieval; only use these to ground your rewrite):**
{{evidence_text}}

------------------------------------------------------------
RULES
------------------------------------------------------------

1. **Do not invent new facts.** Only state what the evidence directly supports.
2. **Preserve LaTeX format.** Use \cite{arxiv_id} for citations. Output valid LaTeX.
3. **Stay close to the original sentence.** Keep the same topic, scope, and information intent whenever supportable; do not drift to a new point.
4. **Fit the local context.** The rewritten sentence must be coherent with the given previous/next context and should read naturally in the paragraph.
5. **Evidence-grounded wording is mandatory.** Every kept claim in the rewritten sentence must be supported by the provided evidence snippets.
6. **Adapt by verdict type:**
   - **unsupported**: Remove or weaken the unsubstantiated claim; add hedging (e.g., "may", "in some cases") or delete the claim.
   - **overgeneralized**: Add qualifiers (e.g., dataset, setting, scope) so the claim matches the narrow evidence.
   - **weakly_supported**: Add hedging or qualify the scope.
   - **irrelevant** (action delete_irrelevant): Remove this claim from the sentence; if it is the only content, shorten the sentence or merge with context.
   - **rewrite**: Revise so the claim is supported by existing citations or remove/weaken it.

7. **Cite correctly.** Only cite papers whose content appears in "Available evidence" and directly supports the rewritten claim. Use the arxiv_id from the evidence list.
8. **No unsupported additions.** Do not introduce any new claim that is absent from the original sentence and not grounded by evidence.

------------------------------------------------------------
OUTPUT
------------------------------------------------------------

Output the rewritten sentence only. No explanation, no markdown. Plain LaTeX text with \cite{} where appropriate.
