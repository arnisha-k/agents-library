Perform a comprehensive thematic analysis of the employee survey responses in the "Raw Comments Cleaned" worksheet.

Use the "Category Dictionary" worksheet as the authoritative classification guide, including its definitions, inclusion criteria, exclusion criteria, and suggested subtopics.

**Objective:** Replicate the existing manual employee survey comment coding process by breaking each original comment into distinct feedback statements and assigning each statement to one of the 15 predefined topic categories.

### Instructions

For every original comment:

1. Read the entire comment carefully, regardless of its length.

2. Identify all distinct, meaningful feedback ideas, including concerns, suggestions, appreciation, and observations.

3. Create a separate row for each distinct idea. A single comment may generate multiple rows across different topic categories. Retain the same original Comment ID for all extracted ideas.

4. Write a concise, specific summary of each extracted idea under "Comment Edited". Preserve the employee's intended meaning, including the actual concern, suggestion, or positive observation.

5. Assign exactly one "Topic" to each extracted idea using only the 15 categories in "Category Dictionary". Use the definitions, inclusion criteria, and exclusion criteria to determine the best category. Suggested Subtopics are supporting guidance only; do not create a separate Subtopic output column.

6. Extract an "Evidence Excerpt" containing the exact supporting wording from the original comment. The excerpt must directly justify both the extracted idea and its assigned category.

7. Classify each extracted idea's "Sentiment" as Positive, Negative, Neutral, or Mixed based on the meaning of that specific statement, not the overall comment. Do not automatically treat improvement suggestions as negative.

8. Set "Count" = 1 for every coded row.

9. Set "Negative Comment?" = Y when Sentiment is Negative; otherwise N. Preserve Mixed as a distinct sentiment rather than automatically treating it as negative.

10. Assess "Serious Risk?" as follows:
   - Y: The statement explicitly raises a potentially serious employee safety, health, harassment, discrimination, ethical, compliance, or operational risk.
   - N: No potentially serious risk is clearly expressed.
   - Review: The statement may raise a serious risk, but the wording or severity requires human judgment.

11. Include a brief "Risk Type" when Serious Risk? is Y or Review. Otherwise leave it blank.

12. Set "Review Required" = Y whenever the category assignment is ambiguous, the evidence is insufficient, or a potential serious risk needs human assessment. Otherwise N.

### Output

Create a new worksheet named "AI Comment Coding" and format the results as a structured Excel Table.

Use these columns in this exact order:

1. Comment ID
2. Full Comment
3. Comment Edited
4. Topic
5. Evidence Excerpt
6. Sentiment
7. Count
8. Negative Comment?
9. Serious Risk?
10. Risk Type
11. Review Required

### Quality requirements

- Preserve the original full comment text without modification.
- Every original Comment ID must appear in the coded output at least once.
- Each extracted idea must be supported by its Evidence Excerpt.
- Do not repeat generic category definitions in Comment Edited.
- Do not invent concerns, experiences, intentions, or supporting evidence.
- Do not omit meaningful feedback from long or complex comments.
- Avoid duplicate coding of the same idea.
- Multiple genuinely distinct ideas may be assigned to the same Topic.
- Distinguish employee perceptions and allegations from verified facts.
- Do not infer employee identities.
- Do not add or rename categories.
- Do not modify the original source data or Category Dictionary.

### Initial validation

First, process only the first 20 nonblank comments, including any long comments that contain multiple topics.

Create the output table for these 20 comments so I can review extraction accuracy, category assignments, and completeness.

Do not process the remaining comments until this initial sample has been validated.

Report the number of original comments processed, the number of extracted ideas, and any comments requiring manual review.
