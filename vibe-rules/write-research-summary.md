---
description: Guide for writing a summary of technical or market research
globs:
alwaysApply: false
---

# Rule: Writing a Research Summary (Technical/Market Research)

## Goal

To guide an AI assistant in producing a clear and organized **Research Summary** document in Markdown, which distills the findings from technical or market research on a given topic. The summary should highlight key insights, comparisons, and conclusions so that the reader (solo founder or team) can quickly grasp the essential information without reading through all the original research materials. The document should be structured for easy scanning, often with headings for different sub-topics or criteria.

## Process

1. **Clarify Research Scope:** Determine the exact topic and goals of the research. Is this technical research (e.g., comparing programming frameworks or investigating a technical solution) or market research (e.g., competitor analysis, user research feedback)? Ask the user for specifics if not provided: “What was the main question or objective of this research? Were you comparing options or gathering general insights?”
2. **Collect Key Points:** Go through the research material provided (this might be notes, articles, data, etc.). Extract the most important points:
   - For technical research: note important findings like performance benchmarks, feature differences, pros/cons of each option, expert recommendations, etc.
   - For market research: note competitor offerings, user preferences/trends, market size figures, etc.
   While collecting, ignore extraneous info and focus on insights that aid decision-making or understanding.
3. **Organize by Themes or Questions:** Structure the summary logically. Common approaches:
   - By subtopic or category (e.g., if researching frameworks, categories might be “Performance”, “Ease of Use”, “Community Support”, etc.; if market research on competitors, categories might be “Pricing”, “Features”, “Market Share”).
   - By option (e.g., discuss Tech A and Tech B separately then compare, or list each competitor and their highlights).
   - Chronologically only if the research is timeline-based (less common).
   Decide on major sections and create headings for them.
4. **Write the Summary Sections:** For each section or theme:
   - Present the key findings in a clear, concise manner. Use bullet points for lists of facts or comparisons, which makes it easy to read.
   - If comparing multiple items, you can use tables or side-by-side bullet points for clarity (for example, a Markdown table comparing features of two products).
   - Highlight any significant numbers or metrics (e.g., "X has 50% market share, whereas Y has 30%").
   - Keep language neutral and factual when presenting research data. If interpretation is needed, mark it as such (e.g., “This suggests that ...”).
5. **Add Recommendations or Conclusions:** After presenting the facts, include a section for **Conclusion** or **Recommendation** (if the goal of the research is to make a decision). Here, synthesize what the findings mean. For instance: “Based on the above, Framework A might be more suitable due to its smaller learning curve and strong community, despite Framework B having slightly better performance on large data sets.” Or for market: “The research indicates a gap in the market for low-cost alternatives, which our product could fill.”
   - If the user specifically asked for recommendations, clearly call them out (even in a bullet list form, like "Recommendation: Proceed with X because ...").
   - If the research is purely informational, a conclusion can simply summarize the most important insight.
6. **Cite Sources (if needed):** If the summary includes specific data or quotes from sources, it’s good practice to mention where they came from (e.g., "According to Gartner’s 2024 report,..."). In a Markdown doc, you might include footnotes or inline links. If the user has the source materials, referencing them by name or number is helpful.
7. **Review for Bias and Completeness:** Ensure the summary objectively represents the research. Check if any important finding was omitted. Also ensure it doesn’t read as an opinion piece (unless specifically intended); it should reflect the research content.
8. **Format for Readability:** Use Markdown features to improve readability:
   - Headings and subheadings to break up sections.
   - Bullet lists or numbered lists for enumerating points.
   - Bold or italic to emphasize critical insights or highlight the option that is recommended.
   - Tables, if comparing multiple items on several criteria.
   - Quotations for any direct quotes from research sources (using `>` for blockquote).
9. **Keep it Succinct:** The goal is summarization. Don’t include long paragraphs of text. Each point should be as brief as possible without losing meaning. Aim for a document that can be read in a few minutes to get the gist.

## Suggested Structure

A research summary could look like this:

- **Introduction:** A brief intro stating what was researched and why. For example: “This document summarizes research on database solutions for our app, specifically comparing PostgreSQL, MongoDB, and DynamoDB, to inform our decision on which to use.”
- **Section 1: [Topic or Option A]** – Present findings related to a specific aspect or a specific option.
  - Important point 1 (could be a bullet or a short paragraph).
  - Important point 2, etc.
- **Section 2: [Topic or Option B]** – Another aspect or option.
  - (and so on for all major sections)
- **Comparison/Analysis:** (If not already integrated above) Possibly have a section directly comparing options or summarizing differences, e.g., a table:
| Criterion  | PostgreSQL                                    | MongoDB                                  | DynamoDB                           |
| ---------- | --------------------------------------------- | ---------------------------------------- | ---------------------------------- |
| Data Model | Relational (SQL)                              | Document (NoSQL)                         | Key-Value/Document (NoSQL)         |
| Strengths  | ACID compliance, strong SQL support           | Flexible schema, easy to scale out       | Fully managed, high scalability    |
| Weaknesses | Harder to scale horizontally without sharding | No SQL joins (harder relational queries) | Proprietary to AWS, vendor lock-in |

- **Key Insights:** Bullet list of the most critical takeaways (e.g., "Relational DB might be better for complex queries, but requires more upfront schema design.").
- **Conclusion/Recommendation:** Summarize what the research implies and any recommendation as described in step 5.

## Target Audience

Assume the reader is the solo founder or a small team who needs to make decisions based on this research. They might not have time to go through all raw data, so:
- The summary should be accessible to someone with general knowledge. If technical terms are used, ensure they are explained or are commonly understood.
- It should be factual and unbiased; the reader will trust it as an accurate distillation of the sources.
- If it’s market research, ensure any business or marketing terms are clarified (e.g., TAM - Total Addressable Market).
- The tone should be professional and informative. It can have a slight advisory tone in the conclusion if recommendations are given.

## Output

- **Format:** Markdown (`.md`), with proper usage of headings, lists, etc.
- **Location:** Possibly a `/docs/` or `/research/` directory. E.g., `research-summary-[topic].md` or if for a meeting, maybe attached to a notion or something. But as a file, likely in docs.
- **Filename:** e.g., `research-summary-database-options.md` or `market-research-competitors.md`.
- **Length:** As long as needed to cover key points but aim to keep it reasonably short by focusing on core insights (maybe 1-3 pages of content in markdown).

## Final Instructions

1. **Attribution:** If the research summary draws directly from specific sources, include references (inline links or footnotes) so the user can follow up for more detail if needed. Do not plagiarize text; paraphrase findings in a clear way.
2. **No Personal Opinion (unless asked):** Stick to what the research indicates. If a recommendation is made, base it on the data (“Given X and Y, it might be best to choose Z”). Avoid unsupported claims.
3. **Double-Check Data:** If numbers or facts are provided, ensure they are accurately transcribed from the source material.
4. **Confidentiality:** If any research info is sensitive or from internal data, treat it appropriately (the user should guide on this, but as an AI, just be mindful to not reveal anything not meant for the summary).
5. **Update-ability:** Write the summary such that it could be updated with new findings if needed. For example, structuring by criteria means if a new option is researched later, it can be added easily.
6. **Clarity:** The end result should give the user (solo founder) a solid understanding of the topic’s landscape and a basis for decision, all in a format that's easy to read quickly.
