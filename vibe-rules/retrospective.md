---
description: Guide for writing a sprint retrospective summary
globs:
alwaysApply: false
---

# Rule: Writing a Sprint Retrospective Summary

## Goal

To guide an AI assistant in creating a concise and insightful **Sprint Retrospective** document in Markdown. The retrospective should summarize what went well during the sprint, what did not go well, and propose actions for improvement. This is intended for a solo founder or a small team to reflect on the sprint and capture learnings in a structured way.

## Process

1. **Gather Sprint Information:** Collect details about the sprint in question: its goals, which features or tasks were completed, which were not, any notable issues (e.g., major bugs, scope changes), and any relevant metrics (velocity, number of bugs, etc.). If the user hasn't provided these, prompt them for highlights: “What were the key accomplishments of this sprint? Any major challenges or blockers encountered?”
2. **Identify Highlights (What Went Well):** Determine the successes of the sprint. This can include completed features, ahead-of-schedule deliveries, positive feedback received, improvements in process, good teamwork, etc. These will form the "What Went Well" section. Aim to list concrete examples (e.g., “Implemented feature X which received good feedback from beta users” or “Team communication on Slack was very responsive”).
3. **Identify Challenges (What Didn’t Go Well):** Determine the problems or things that failed or could have been better. Examples: tasks that took longer than expected, goals that weren’t met, bugs introduced, communication issues, etc. These will form the "What Didn't Go Well" section. Be honest but objective — the goal is to learn, not to blame.
4. **Extract Lessons Learned:** For each of the above successes and challenges, consider what the team (or solo founder) learned. This might be patterns observed (e.g., “We tend to underestimate testing time”), insights gained (e.g., “Users found value in simpler features vs complex ones”), or confirmations of what worked (e.g., “Daily stand-ups kept us on track, we should continue them”). These will populate a "Lessons Learned" or "Insights" section.
5. **Propose Action Items:** Based on the challenges and lessons, formulate concrete actions to improve future sprints. These go in an "Action Items" or "Recommendations" section. Each action item should be specific and achievable in upcoming sprints. (e.g., “Allocate at least 2 days for testing in each sprint,” or “Streamline the code review process by using automated linting.”). If the user is solo, action items can still be process changes or tooling improvements.
6. **Organize the Retrospective Document:** Structure the document with clear sections for **What Went Well**, **What Didn't Go Well**, **Lessons Learned** (if separate from the first two, or integrated within them), and **Action Items**. Optionally, start with a brief **Sprint Summary** or **Overview** stating the sprint name/number and duration, and overall outcome (e.g., “Sprint 5 (Jan 1 - Jan 14, 2025): Completed 8 out of 10 planned tasks, delivered Feature X, faced delay in API deployment.”).
7. **Write Clearly and Concisely:** In each section, use bullet points for individual items so it’s easy to scan. Each point should be a single thought or observation. For example, under "What Went Well": "*The new automated test suite reduced regression bugs significantly (only 1 minor bug slipped through).*"
8. **Tone and Perspective:** Maintain a positive, constructive tone. Even for "What didn't go well", phrase things in a way that focuses on improvement. Instead of "X was a disaster", say "We faced challenges with X and need to improve Y." Since it's a solo founder usage, it can be slightly informal or personal, but staying professional is fine too. Write in first person plural (“we”) if the context is a team, or first person singular if it's truly just the founder (“I”). Typically retrospectives use "we" even for small teams.
9. **Review and Edit:** Ensure the points are accurate according to the sprint data. Remove any overly specific blame (e.g., don't single out a person; focus on processes or outcomes). Check that each action item has a corresponding issue from the "didn't go well" or "lesson" that it addresses.

## Retrospective Structure

A typical sprint retrospective Markdown document might be structured like:

- **Sprint Overview:** *Summary of sprint context and overall outcome.* (Optional but useful for context, especially if someone reads this later. E.g., "Sprint 5 (Aug 1-15, 2025) aimed to implement the initial version of the Analytics Dashboard. We completed 3 out of 4 stories. One story was postponed due to unexpected production bug fixes.")
- **What Went Well:** (Bullet points)
  - *Point 1: Description of a positive thing.* (e.g., "Feature X was delivered on time and received positive initial user feedback.")
  - *Point 2: Another positive.* (e.g., "Code refactoring improved performance by 20% on the homepage.")
- **What Didn’t Go Well:** (Bullet points)
  - *Point 1: Description of an issue or challenge.* (e.g., "Integration with payment gateway was delayed due to unforeseen API limitations.")
  - *Point 2: Another challenge.* (e.g., "We had poor task estimation; some tasks took significantly longer than expected, causing spillover.")
- **Lessons Learned:** (Bullet points, optional separate section – or you can integrate a lesson after each above point, but separating can be clearer)
  - *Lesson 1:* (e.g., "We need to allocate more buffer time for third-party integration tasks in planning.")
  - *Lesson 2:* (e.g., "Regular check-ins might have caught the API issue earlier.")
- **Action Items for Improvement:** (Bullet or numbered list of concrete actions)
  1. *Action 1:* (e.g., "Before next sprint, research the third-party APIs more thoroughly to uncover potential issues ahead of time.")
  2. *Action 2:* (e.g., "Adopt a new estimation technique (planning poker) to improve estimate accuracy.")
  3. *Action 3:* (e.g., "Set up a mid-sprint review meeting to surface blockers earlier.")
- **Acknowledgements (Optional):** If a team, you might thank or call out any team member achievements or efforts. As a solo founder, this might not apply, but you might write a brief morale note like "Overall, despite the challenges, this sprint moved us closer to launch and the groundwork is set for Feature Y."

Formatting tips: Use past tense for describing what happened. Action items can be imperative or future tense since they are tasks to do.

## Target Audience

The primary audience is internal — the solo founder themselves and possibly any team members or advisors. It’s basically for the record and continuous improvement. So:
- It should be honest and self-reflective.
- It should also be digestible; someone else (like a future hire or an investor interested in progress) could read it to get an idea of how the development process is going.
- No need for overly formal language; it can be straightforward. But maintain professionalism and a solutions-oriented tone.

## Output

- **Format:** Markdown (`.md`) document.
- **Location:** Perhaps in a `/docs/` or `/retrospectives/` folder, or even within a project management tool. As a file, maybe `/docs/sprint-retrospective-[number].md` or dated file.
- **Filename:** For example, `retrospective-sprint-5.md` or `sprint-2025-08-retro.md`.
- The document will be text with headings and lists, no special output beyond standard Markdown.

## Final Instructions

1. **Keep it Constructive:** Always frame “What didn’t go well” and criticism in a constructive manner. The goal is improvement, not blame. For example, prefer “We didn’t meet the deadline due to underestimating task complexity; next time we should refine our estimation process” over “X caused us to miss the deadline.”
2. **Be Specific but Brief:** Each point should be specific enough to be meaningful, but not a long-winded story. If more detail is needed for context, you can add a sentence or sub-bullet for clarification.
3. **Follow Up on Action Items:** Ensure that each action item is actionable. In future retrospectives, it’s often good to check if these actions were implemented and if they helped. (You could even include a note in the next retrospective to track which actions from the last retro were done.)
4. **Tone:** It's fine to celebrate wins in a positive tone (“Great job on X!”) and to acknowledge challenges in a neutral tone. The overall retrospective should end on an optimistic note that with the action items, the next sprint will be better.
5. **No Code, Just Reflection:** This document is not for code or technical specs (though it might reference technical events, like "the deployment script failed"). Keep the focus on process and outcome, not implementation details.
