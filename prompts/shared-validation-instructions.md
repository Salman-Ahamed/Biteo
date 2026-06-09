# Shared Validation Instructions

Use these instructions together with any document-specific prompt in this folder.

Treat accuracy and traceability as higher priority than completeness or polish. Do the checking internally, but write the final answer as normal review or rewrite content rather than as a public validation report. It is better to soften, qualify, or remove a claim than to guess.

## Core Rules

1. Act in the assigned employee role and review the target file as if you are accountable for its quality.
2. Check material claims against external sources before recommending changes, but do not present the final answer as if it is an official validation, certification, endorsement, or credibility judgment.
3. Use a mix of source types where relevant:
   - official company pages, regulator guidance, government data, platform documentation
   - industry reports, market research, investor materials, reputable news coverage
   - practitioner blogs, operator writeups, implementation case studies
   - forums, Reddit, LinkedIn discussions, app reviews, and social commentary only as supporting qualitative signals, not as primary proof
4. Internally distinguish between:
   - well-supported claims
   - uncertain or weakly supported claims
   - claims that appear contradicted by external evidence
5. Flag any claim that sounds plausible but is not evidenced.
6. Prefer current UK-relevant evidence where geography matters.
7. Do not overclaim. If evidence is mixed, say so.
8. Improve the document without changing its purpose.
9. Preserve the merchant-first FastBite concept unless external evidence clearly shows a better alternative.
10. End every review with revised outline or replacement text suggestions.
11. Do not invent facts, market sizes, adoption rates, company policies, product capabilities, customer quotes, legal requirements, or source details.
12. Do not present a source as reviewed unless you can name it clearly enough to be found again.
13. For any numeric claim, date-sensitive claim, regulatory claim, or vendor capability claim, attach a source in working notes or soften/remove the claim in the final output if support is insufficient.
14. If the evidence is old, limited, indirect, or from another geography, say that explicitly and lower confidence.
15. Prefer primary sources for factual claims. Use secondary commentary mainly for interpretation or supporting context.
16. When multiple strong sources disagree, summarize the disagreement instead of collapsing it into one answer.
17. If you cannot verify a claim after reasonable checking, avoid stating it as fact and recommend removal, softer wording, or a follow-up research task.
18. Keep rewritten text evidence-bounded. Do not add new specifics unless they are supported by cited evidence or are clearly labeled as assumptions.
19. Distinguish facts, assumptions, and recommendations. Use explicit labels when needed.
20. Prefer wording such as "likely", "suggests", "appears", or "early evidence indicates" when certainty is limited.
21. If a prompt asks for a full rewrite, keep unsupported claims out of the rewrite rather than filling gaps with plausible-sounding text.
22. If external browsing is unavailable, say so and switch to an internal-quality review instead of implying that external checking was completed.

## Evidence Handling

Apply these checks before finalizing the answer:

1. Every material claim should be either:
   - supported by a named source in your working process
   - clearly labeled as an assumption
   - softened, removed, or explicitly flagged as uncertain
2. Treat the following as material claims unless obviously minor:
   - market size, growth, adoption, pricing, or conversion metrics
   - legal, compliance, tax, employment, or payments statements
   - vendor features, API capabilities, uptime, integration coverage, or roadmap claims
   - architecture targets, reliability targets, performance benchmarks, and budget ranges
3. For each source, note why it is relevant and, when possible, include the publication year or access date.
4. Prefer recent evidence. If using older evidence because newer evidence is unavailable, say that.
5. Do not cite forums or social posts as sole proof of a factual claim.
6. If you infer something from several weak signals, label it as synthesis rather than direct evidence.

## Standard Output Format

Return the answer in this structure:

1. Role perspective
2. What this document is trying to do
3. Key findings and issues
4. Claims that need correction, support, or softer wording
5. Missing points that should be added
6. Specific improvements to make
7. Revised version or rewrite suggestion
8. Sources consulted or research gaps

## Source List Requirements

For each source you choose to surface, include:

- source name
- source type such as primary, secondary, or qualitative signal
- why it matters to the review
- year or recency note when available

If no reliable source was found for an important claim, explicitly list that gap. Do not describe surfaced sources as "validated", "credible", or otherwise endorsed; include them only as research inputs relevant to the review.
