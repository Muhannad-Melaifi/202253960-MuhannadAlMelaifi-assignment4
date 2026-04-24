# AI Usage Report (Assignment 3)

## 1) AI Tools Used

- ChatGPT (design discussion, JavaScript logic suggestions, documentation refinement)
- GitHub Copilot Chat (code refactoring support, debugging checks, and rubric-aligned documentation edits)

## 2) Why AI Was Used

AI was used to speed up ideation, compare implementation options, and improve clarity in both code behavior and written documentation. AI support was focused on:

- Dynamic content behavior (project search/filter)
- Data handling flow (API fetch states: loading/success/error)
- User feedback patterns (empty states, toast messages, validation hints)
- Report quality improvements (clearer structure and grading-aligned explanations)

## 3) Where AI Contributed in the Project

### A) Feature Planning

AI was used to evaluate which interactions best match assignment requirements. The selected scope prioritized:

- One dynamic content feature
- One public API data feature
- Consistent user feedback for normal and failure paths

### B) JavaScript Logic Refinement

AI provided draft logic and pseudocode for:

- Live filtering with input events
- Empty-state visibility logic when no project cards match
- Async API handling with try/catch
- Refresh action behavior and fallback messaging
- Combined filtering and sorting logic for projects
- Visitor state storage and session timer structure

### C) UX Wording and Messaging

AI helped improve microcopy for:

- Error states
- Empty states
- Success confirmations
- Loading status text

### D) Documentation Quality

AI was used to reorganize project documentation so each section maps to rubric criteria (functionality, UX clarity, and effective AI use evidence).

## 4) Example Prompt Patterns

Below are representative prompt types used during development (paraphrased):

- "Suggest a clean DOM-based live filter for project cards with an empty-state message."
- "Improve this fetch flow to show loading, success, and friendly error states."
- "Review this form validation logic and suggest clearer user feedback copy."
- "Rewrite this README section with step-by-step user guidance for navigation and interaction."

## 5) Human Verification and Changes Made

All AI-generated suggestions were manually reviewed and edited before final use.

- I adjusted variable names and logic structure for readability.
- I removed unnecessary complexity from draft snippets.
- I tested each feature directly in the browser.
- I verified behavior for both success and failure scenarios.
- I ensured the final code aligns with assignment constraints.
- I rejected suggestions that introduced unnecessary complexity.
- I rewrote parts of generated text to match my own writing style.

## 6) Benefits Observed

- Faster iteration when comparing implementation choices
- Better coverage of edge cases (especially API failures)
- Improved wording consistency for user-facing messages
- Higher documentation clarity and stronger traceability of decisions

## 7) Challenges and Mitigation

- Challenge: Some AI suggestions were too generic.
  - Mitigation: Narrow prompts using exact IDs, required behaviors, and expected UI outputs.
- Challenge: API reliability/rate limits can affect demonstration.
  - Mitigation: Added caching/fallback behavior and explicit user-facing error text.

## 8) Responsible and Ethical AI Use

- AI was used as an assistant, not as an automatic replacement for understanding.
- I validated all output and kept only code I can explain.
- Final decisions, debugging, and testing remained my responsibility.
- Documentation explicitly discloses where AI contributed.

## 9) Learning Outcomes

Using AI in a controlled way improved my practical skills in:

- DOM querying and event-driven updates
- Async JavaScript with fetch and error handling
- Designing user feedback for edge cases
- Structuring technical documentation for rubric alignment

## 10) Conclusion

AI support was used intentionally for planning, refinement, and documentation. The final submission reflects human-reviewed implementation choices, tested behaviors, and transparent reporting of AI involvement.


