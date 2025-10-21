# Copilot Authoring Instructions for Meowcards

These instructions guide AI (and human) contributors to generate high-quality flashcard Markdown files compatible with the Meowmorize app.

## 1. Project Purpose
Create concise, consistent, recall-focused flashcards covering software engineering, programming languages, infrastructure, data, and related technical concepts.

## 2. Card Block Structure (MANDATORY)
Every flashcard MUST be wrapped with comment sentinels exactly like this:

```
<!-- Card Start -->
### Front
[Question | Prompt | Concept]

### Back
[Answer | Explanation]
<!-- Card End -->
```

Rules:
- Use `### Front` and `### Back` (H3). Never other heading levels for sides.
- One card per sentinel block.
- Blank line after `### Front` line and after `### Back` heading is recommended for readability.
- No extra `<!-- Card Start -->` / `<!-- Card End -->` inside a card.

## 3. File Conventions
- Location: place new topic files under `cards/<topic>/` (create folder if needed).
- File format: Markdown (`.md`).
- Optional top-of-file metadata comment: `<!-- title:Topic Name -->`.
- Prefer grouping related cards logically (e.g. docker basics, sql advanced) rather than huge monolithic files. Target 50–200 cards per file max; split beyond that.

## 4. Front Side Guidelines
Aim: trigger active recall.
- Be concise: 1 line question or short scenario. Max ~3 sentences.
- For multiple choice, list options A–D (or A–E) with aligned formatting. Randomize correct letter.
- Avoid embedding the answer hint directly.
- Use neutral phrasing, e.g. "What does ACID consistency guarantee?" not "Explain in extreme detail the exact definition of ACID consistency".
- For code prompts, show only the minimal stub or requirement—place full solution on Back.

## 5. Back Side Guidelines
Aim: reinforce, not overwhelm.
- Start with a bold key answer line when appropriate: `**Answer**: <concise core>` or `**Correct Answer**: X` followed by explanation.
- Use bullet lists for enumerations (principles, steps, comparisons).
- Include short code examples inside fenced blocks with language tag (` ```go`, ` ```sql`, ` ```python`, etc.).
- Keep each explanation focused. If > 10 lines or covering >1 distinct concept—split into multiple cards.
- You may add a small "Related" section at the end (bullets or inline) if it aids memory.

## 6. Supported Card Types
1. Standard Q&A
2. Multiple Choice
3. Code Prompt → Solution
4. Comparison (Front: "X vs Y"; Back: table or bullets)
5. Definition / Term Drill
6. Scenario / Troubleshooting (Front: scenario; Back: reasoning + resolution)

## 7. Style & Formatting
- Consistent capitalization for headings and terms.
- Use **bold** for key terms, *italic* for emphasis.
- Prefer tables for structured contrasts (e.g. SQL isolation levels vs phenomena).
- Avoid overly academic prose—keep direct and instructional.
- Do not introduce external links unless essential; prefer self-contained explanations.

## 8. Multiple Choice Formatting
Front example:
```
### Front
Which AWS service provides fully managed message queuing?

- A. Amazon SNS
- B. Amazon SQS
- C. AWS Lambda
- D. Amazon Kinesis
```
Back example:
```
### Back
**Correct Answer**: B

**Explanation**: Amazon SQS provides fully managed message queues. SNS is pub/sub notifications, Lambda is compute, Kinesis handles streaming data.
```

## 9. Code Blocks
- Always specify language for syntax highlighting.
- Keep to minimal illustrative code; avoid long boilerplate.
- Show input/output if clarifies learning.

## 10. Tables (Optional)
Use Markdown tables for comparisons. Example Back:
```
| Pattern | Intent | Example |
|---------|--------|---------|
| Singleton | One instance | DB connection |
| Strategy | Vary algorithm | Sort comparator |
```

## 11. Prohibited / Avoid
- No duplicated cards (exact or trivially rephrased) within same file.
- No trailing spaces inside sentinel lines.
- Avoid vendor marketing fluff; keep technical.
- Do not exceed ~120 characters per line when feasible.
- Avoid speculative or unverifiable claims.

## 12. Quality Checklist (Per Card)
- [ ] Has sentinel start & end
- [ ] Uses `### Front` / `### Back`
- [ ] Front concise & answer NOT leaked
- [ ] Back starts with clear answer (when applicable)
- [ ] Formatting: bullets / code / table used appropriately
- [ ] Not excessively long (>10 lines Back body)
- [ ] No duplication detected

## 13. File-Level Checklist
- [ ] Logical topic grouping
- [ ] Optional `<!-- title:... -->` for topic
- [ ] Reasonable size (< ~200 cards)
- [ ] Consistent style across cards

## 14. Extending Topics
When adding a new topic folder:
```
cards/<domain>/
  README.md  (brief scope + subtopics)
  <domain>-cards.md (or segmented files)
```
The README should define target audience and coverage boundaries.

## 15. Difficulty Tagging (Optional)
Add a tag inline on Front first line: `[Basic]`, `[Intermediate]`, `[Advanced]`.
Example:
```
### Front
[Intermediate] What does the Go `select` statement do?
```

## 16. AI Prompting Guidance
When prompting AI to generate new cards:
- Provide topic scope + desired count.
- Request strict adherence to sentinel structure.
- Ask for variety of question types.
- If output violates structure, instruct regeneration focusing on the missed rule.

## 17. Common Pitfalls
| Pitfall | Fix |
|---------|-----|
| Missing sentinel comments | Add `<!-- Card Start -->` / `<!-- Card End -->` | 
| Wrong heading level | Use only `###` for sides |
| Overlong Back | Split into smaller cards |
| Mixed multiple questions in one Front | Split per question |
| Repeated answer letter in MC set | Randomize letters |

## 18. Example Composite File Snippet
````markdown
<!-- title:Docker Basics -->

<!-- Card Start -->
### Front
What is a Docker Image?

### Back
A **Docker Image** is an immutable template containing application code, dependencies, and metadata used to create containers.
<!-- Card End -->

<!-- Card Start -->
### Front
Which command builds a Docker image from a Dockerfile in the current directory?

- A. docker create .
- B. docker build .
- C. docker image run .
- D. docker compose build .

### Back
**Correct Answer**: B

**Explanation**: `docker build .` reads the Dockerfile in the current directory to create a new image layer stack.
<!-- Card End -->
````

## 19. Contribution Workflow
1. Create branch: `feature/<topic>-cards`.
2. Add / update card file(s) following this spec.
3. Run personal validation (scan for sentinels & headings).
4. Open PR referencing guidelines; ensure diff is only new/changed cards.
5. Address review feedback.

## 20. Validation Script (Future Idea)
A lightweight script could verify:
- Count of `<!-- Card Start -->` equals `<!-- Card End -->`.
- All `### Front` followed by a `### Back` before next sentinel end.
- No nested sentinels.

(Feel free to implement in a future enhancement.)

---
Adhere to these rules to keep Meowcards high-quality, uniform, and effective for spaced repetition learning.
