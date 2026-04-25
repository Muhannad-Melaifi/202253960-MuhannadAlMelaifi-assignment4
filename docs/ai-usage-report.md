# AI Usage Report — Assignment 4

---

## 1. Tools Used

| Tool | Primary Use Cases |
|---|---|
| Claude (Anthropic) | Feature planning, code generation, documentation drafting, code review |
| GitHub Copilot | In-editor code completion, boilerplate reduction |

---

## 2. How Each Tool Was Used

### Claude

Claude was used as the main development assistant throughout Assignment 4. Specific use cases:

**Feature design:**
Prompted Claude to suggest what features would best address the Assignment 4 rubric (polish, innovation, documentation quality). Claude proposed the scroll progress bar, Intersection Observer-based scroll reveal, animated stat counters, and the GitHub API stats widget. I evaluated each suggestion against the rubric criteria and chose the ones that added real value to the user experience.

**Code generation:**
Claude generated initial implementations for:
- The `initScrollProgress` function (scroll position percentage calculation)
- The `initScrollReveal` function (adding/removing `.reveal`/`.visible` classes via Intersection Observer)
- The `initStatCounters` function (ease-out quad animation with `requestAnimationFrame`)
- The `initGitHubStats` async fetch with error handling
- The `initCharCounter` function for the textarea

In all cases I reviewed the code, tested it in the browser, and made targeted edits before including it.

**Documentation:**
Claude drafted initial versions of the README, this AI usage report, and the technical documentation. I restructured sections, corrected factual details (file paths, function names), and rewrote explanations to match my own understanding and writing style.

**Code review:**
After writing CSS for the new components (badges, tech chips, social links), I asked Claude to review for accessibility issues and responsive behavior. This surfaced one issue: the contact grid needed an explicit `align-items: start` to prevent the social card from stretching to match the form's height.

### GitHub Copilot

Copilot was used for in-editor autocomplete while writing repetitive HTML structures (e.g., the three GitHub stat `<div>` elements, social link `<li>` items). It also autocompleted CSS property values for new rules. I accepted suggestions selectively and overrode them when they did not match the existing code style.

---

## 3. Example Prompt Patterns

Below are representative prompts used during development (paraphrased):

- "Given this assignment rubric, what new features would score highest on Innovation and Performance? Keep answers brief."
- "Write a scroll progress bar implementation that uses `{ passive: true }` event listeners and updates a CSS width property."
- "Write an Intersection Observer that adds a `.visible` class to `.card` elements when they enter the viewport. Cards should be unobserved after first trigger."
- "Write an animated counter that goes from 0 to a target number in ~1 second with ease-out, using requestAnimationFrame."
- "Review this CSS for the `.contact-grid`. What happens on mobile if I change it to 1.6fr 1fr?"
- "Draft a comprehensive README for a portfolio site. Sections needed: overview, features, setup instructions, file structure, browser compatibility, AI documentation."

---

## 4. How AI Output Was Verified and Modified

Every piece of AI-generated code was:

1. **Read and understood** before being used. I did not include code I could not explain.
2. **Tested in the browser** across dark mode, light mode, mobile size, and desktop size.
3. **Modified where needed:**
   - The scroll-reveal implementation originally applied the `.reveal` class in HTML. I changed it to apply via JavaScript so that users without JavaScript see cards normally (progressive enhancement).
   - The stat counter animation used a linear formula initially. I replaced it with ease-out quad for a more natural feel.
   - The GitHub stats widget originally showed a toast on failure; I removed this since the inline status message already communicates the error without being intrusive.
   - Documentation language was rewritten in my own voice throughout.

---

## 5. Benefits Observed

- Faster implementation of complex patterns (Intersection Observer, requestAnimationFrame animation)
- Better coverage of edge cases (API failures, rate limits, no-JS fallback for scroll reveal)
- Higher documentation quality — Claude's structured drafts gave me a clear outline to refine
- Identified an accessibility issue (missing `align-items` in grid) during code review

---

## 6. Challenges and Limitations

| Challenge | Mitigation |
|---|---|
| AI suggestions were sometimes overengineered (e.g., proposed a full scroll-spy sidebar with dots) | Used simpler active-link approach that is sufficient for this scale |
| Generated CSS did not always match the existing naming conventions | Manually renamed classes to follow the established pattern |
| AI-drafted documentation occasionally made false claims about file paths | Cross-checked every path against the actual directory before finalizing |
| GitHub API rate limit (60 req/hr unauthenticated) affects both widgets | Added independent error handling for each widget; they fail gracefully |

---

## 7. Responsible Use and Academic Integrity

- All AI-generated code was reviewed, tested, and understood before inclusion.
- No AI output was submitted verbatim without review and modification.
- This report transparently discloses every area where AI contributed.
- Final decisions, browser testing, debugging, and integration were done by me.
- AI was used as an accelerator, not as a replacement for understanding.

---

## 8. Learning Outcomes

Using AI tools in a disciplined way during this assignment improved my understanding of:

- **Intersection Observer API**: Understanding threshold, rootMargin, and when to unobserve was clarified by comparing AI-suggested code with MDN documentation.
- **requestAnimationFrame animation**: The ease-out formula and how animation progress is calculated gave me insight into how CSS transitions work internally.
- **API error handling patterns**: Seeing different fallback strategies helped me choose the right approach for each widget (cached fallback for quotes, inline status for GitHub stats).
- **Documentation writing**: AI drafts showed me how to structure technical writing, which I then refined to be more precise and match the project's actual behavior.

---

## 9. Conclusion

AI tools were used throughout Assignment 4 as a development and documentation accelerator. Every contribution was reviewed, tested, and adapted. The final submission reflects my own decisions, my own testing, and my own understanding of every feature included.
