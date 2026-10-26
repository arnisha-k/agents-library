# <Agent name> instructions

Replace the placeholders with this agent's actual instructions.

## Role

You are <agent name>. Help <intended users> with <main purpose>.

## Responsibilities

- <Primary task>
- <Another supported task>

## How to work

1. Understand what the user wants.
2. Ask a focused question if required information is missing.
3. Follow <the appropriate task procedure> using <available sources or tools>.
4. Give the user <the expected answer or output>.

## Response style

Use <tone and level of detail>. Format responses as <preferred structure>.

## Boundaries

- Stay within <the agent's scope>.
- Use <approved sources> for factual answers. Explain what is missing if those sources do not support an answer.
- Do not invent missing facts or claim an action succeeded without a successful result.
- For <unsupported requests or unresolved issues>, <explain the limit or direct the user to the right person>

Looking at your latest Copilot output, I think you're quite close to building something genuinely useful for leadership. But I would make a few important changes before proceeding with the entire dataset.  
The biggest issue I see in your screenshot is category accuracy and evidence traceability.  
For example, one row has:  
* Topic Summary: Comments on remote, hybrid, in-office, or flexible work arrangements.    
* Evidence Excerpt: A paragraph about unsustainable workloads, staffing shortages, burnout, and backlogs.    
* Sentiment: Negative.    
Unless there's additional text outside the screenshot supporting the work-arrangements classification, this appears to be a mismatch.  
Also, your current Topic Summary seems to be repeating category definitions rather than summarizing what the employee actually said.  
I would fix this before moving forward.  
**My recommended end-to-end workflow**  
STEP 1  
Prepare raw comments  
Remove blanks from working data, assign IDs  
  
STEP 2  
Build the category dictionary  
Define topics, sentiment, and risk criteria  
  
STEP 3  
Extract and classify ideas  
One row per distinct meaningful idea  
  
STEP 4  
Validate the AI coding  
Check accuracy, duplicates, and completeness  
  
STEP 5  
Build the analysis and dashboard  
Summarize themes, sentiment, and risks  
I'd aim for an output that does three things: accurately represents employee voices, makes recurring organizational issues easy to identify, and gives leadership clear areas for action.  
**Step 1 — Prepare the raw comments**  
First, preserve your original survey worksheet exactly as it is.  
Then have Copilot create a clean working table. Do not delete the original blank rows or change the original row numbering.  
Create a new worksheet named "Raw Comments Cleaned" using the "Comment Box" worksheet.  
1. Extract every nonblank employee comment from the original comment column.  
2. Exclude blank cells, whitespace-only cells, and survey instructions or headings.  
3. Preserve each comment's full original text, wording, punctuation, and paragraph breaks.  
4. Create a stable Comment ID using the original worksheet row number, for example C0018 for row 18.  
5. Include the original source row number.  
6. Do not paraphrase, summarize, merge, or split comments.  
7. Do not remove identical comments unless they are verified duplicate source records.  
8. Create an Excel Table named tblRawComments with columns: Comment ID, Source Row, Full Comment.  
Create a separate "Data Quality" summary showing:  
* Total source rows  
* Nonblank employee comments  
* Blank rows excluded  
* Potential duplicate comments  
Do not modify the original source worksheet.  
Why this matters: Once you start splitting comments into multiple themes, you need to be able to trace every extracted statement back to a single original response.  
**Step 2 — Define your classification rules**  
Keep your existing 15 categories. However, add a definition, inclusion criteria, exclusion criteria, and examples for each.  
For instance:  

| Category | Include | Exclude |
| ----------------------------- | --------------------------------------------------- | ------------------------------------- |
| Workload | Overtime, understaffing, excess work, backlogs | Flexible work preferences |
| Work Styles | Remote work, hybrid arrangements, office attendance | General workload pressure |
| Compensation & Benefits | Pay, raises, insurance, vision benefits | General leadership communication |
| Communication from Leadership | Transparency, explanations, messaging | Manager-specific performance concerns |
| Professional Development | Training, mentorship, internal career advancement | General recruitment concerns |
  
This distinction would help prevent the classification mismatch visible in your screenshot.  
**Prompt 2: Improve the dictionary**  
Review the existing 15 topic categories in the "Category Dictionary" worksheet.  
Preserve all 15 categories and their names.  
For each category, create:  
* Category Name  
* Definition  
* Inclusion Criteria  
* Exclusion Criteria  
* Example Employee Feedback  
* Potential Subtopics  
Make the categories as distinct and consistently interpretable as possible.  
Pay special attention to commonly confused categories:  
* Workload versus Work Styles  
* Management versus Communication from Leadership  
* Department versus Workload  
* Compensation & Benefits versus Recognition  
* Professional Development versus Onboarding/Training  
Do not classify the actual employee comments yet.  
Create the enhanced dictionary in a separate worksheet named "Coding Rules" for my review.  
**Step 3 — Extract and classify the comments**  
This is your main AI prompt.  
I'd include the following fields:  

| Field             | Purpose                               |
| ----------------- | ------------------------------------- |
| Comment ID        | Original response identifier          |
| Theme ID          | Unique identifier for each idea       |
| Full Comment      | Original employee response            |
| Comment Edited    | Concise statement of the idea         |
| Topic             | One of the 15 categories              |
| Subtopic          | Specific recurring issue              |
| Evidence Excerpt  | Exact supporting text                 |
| Sentiment         | Positive / Negative / Neutral / Mixed |
| Count             | Always 1                              |
| Negative Comment? | Y or N                                |
| Serious Risk?     | Y / N / Review                        |
| Risk Type         | Type of potential concern             |
| Review Required   | Y or N                                |
  
**Prompt 3: Main thematic coding**  
Perform a comprehensive thematic analysis of the employee survey responses in "Raw Comments Cleaned".  
Use the "Coding Rules" worksheet as the authoritative classification guide.  
For every original comment:  
1. Read the full comment and identify all distinct, meaningful feedback ideas.  
2. Create a separate row for each distinct idea. Multiple ideas from one comment must retain the same Comment ID.  
3. Summarize each idea in one concise sentence under "Comment Edited", preserving its meaning and specificity.  
4. Assign exactly one primary Topic from the 15 approved categories.  
5. Assign a short, specific Subtopic describing the actual issue.  
6. Extract an exact Evidence Excerpt from the original comment that directly supports the coded idea.  
7. Classify the sentiment of that specific idea as Positive, Negative, Neutral, or Mixed.  
8. Set Count = 1 for each coded idea.  
9. Set Negative Comment? = Y only when the coded idea has Negative sentiment.  
10. Assess Serious Risk? using the risk rules in the Coding Rules worksheet. Use Y, N, or Review. Do not treat ordinary negative comments as serious risks.  
11. Include a Risk Type only when a potential serious risk is identified.  
12. Mark Review Required = Y if the classification is ambiguous, the evidence is insufficient, or a serious risk needs human assessment.  
Important:  
* Each Topic must be supported by its Evidence Excerpt.  
* The Comment Edited column must describe the employee's specific feedback, not repeat a generic category definition.  
* Do not manufacture feedback, evidence, or additional concerns.  
* Avoid duplicating the same idea within a comment.  
* Distinguish between factual allegations, employee perceptions, and suggestions.  
* Use the original comment wording as the basis for classification.  
* Never infer employee identities.  
Output the results in a new worksheet named "AI Comment Coding".  
Maintain the columns in the order specified above and make the output an Excel Table.  
Process all nonblank comments, and verify that each original Comment ID appears in the coded output at least once.  
**Step 4 — Add serious-risk detection, but keep it separate from sentiment**  
Yes, I would absolutely include a Serious Risk? field, especially because some comments describe potential burnout, turnover, unfair treatment, or organizational risks.  
But I'd distinguish ordinary negative feedback from feedback that may warrant closer attention.  
Here's the classification framework I'd recommend:  

| Risk level | Meaning | Example |
| ---------------------- | --------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| None | No material risk raised | "I enjoy the hybrid model." |
| Emerging Concern | Operational or employee experience issue | "Workload has increased significantly." |
| Potential Serious Risk | Explicit serious harm, threat, or significant organizational exposure | "Staff are experiencing severe burnout and essential work is going uncompleted." |
| Review Required | Possible sensitive allegation requiring human assessment | Allegations of harassment, discrimination, retaliation, or unsafe practices |
  
You could include a separate Risk Type for Workload/Burnout, Turnover/Retention, Operational/Service Delivery, Safety, Harassment/Discrimination, Compliance/Ethics, or Other.  
Importantly, an AI flag is an initial screening indicator, not a verified finding or a formal risk assessment.  
**Prompt 4: Risk classification**  
Review the completed "AI Comment Coding" worksheet for potential organizational and employee-related risks.  
Assess each coded idea independently using its Original Comment, Comment Edited, and Evidence Excerpt.  
Create or populate these fields:  
* Risk Level: None, Emerging Concern, Potential Serious Risk, or Review Required  
* Risk Type  
* Risk Rationale  
* Serious Risk?: Y, N, or Review  
Classification rules:  
None: No material workplace or organizational risk is expressed.  
Emerging Concern: A concern involving workload, compensation, morale, employee retention, work processes, communication, or similar matters without explicit evidence of severe impact.  
Potential Serious Risk: The comment explicitly describes serious harm, unsafe conditions, severe burnout, major service disruption, serious ethical concerns, or another potentially significant organizational risk.  
Review Required: A sensitive allegation or ambiguous situation that requires human judgment before assigning a risk level.  
Do not infer risks that are not supported by the text. Do not equate Negative sentiment with Serious Risk.  
For every flagged item, provide a short rationale and exact supporting evidence.  
Do not make legal conclusions, diagnose employees, or treat unverified allegations as established facts.  
Preserve all existing rows and coding. Output the risk review separately or add the results using Theme ID as the matching key.  
**Step 5 — Validate the output before building any dashboard**  
This is arguably the most important step.  
I would not use the initial Copilot results for leadership reporting until they've passed several checks.  
**Prompt 5: Quality assurance**  
Perform a quality assurance review of "AI Comment Coding" against "Raw Comments Cleaned" and "Coding Rules".  
Check the following:  
1. Completeness: Every nonblank original comment must have at least one coded theme.  
2. Traceability: Every Theme ID must map to a valid original Comment ID.  
3. Evidence accuracy: Every Evidence Excerpt must appear verbatim in the corresponding original comment.  
4. Category accuracy: The assigned Topic must accurately match the supporting evidence and the category definition.  
5. Summary accuracy: Comment Edited must faithfully summarize the supporting evidence.  
6. Sentiment accuracy: Sentiment must reflect the specific coded idea.  
7. Duplicates: Flag substantially duplicated themes within the same original comment.  
8. Risk accuracy: Serious Risk flags must follow the approved criteria and have clear supporting evidence.  
9. Counts: Every coded row must have Count = 1, and Theme IDs must be unique.  
10. Missing values: Flag missing Topic, Comment Edited, Sentiment, or Evidence Excerpt.  
Create a "QA Review" worksheet containing:  
* Theme ID  
* Comment ID  
* Issue Type  
* Current Value  
* Suggested Correction  
* Reason for Correction  
* Review Status  
Create a QA summary including:  
* Total original comments  
* Total coded themes  
* Uncoded comments  
* Missing or invalid evidence  
* Suspected classification errors  
* Duplicate themes  
* Items requiring manual review  
Do not silently modify questionable classifications. Flag them for review.  
If you cannot verify any check reliably, report that check as not verified rather than claiming it passed.  
I would also manually compare a representative sample against the original comments, including long multi-topic responses like the one in your screenshot. A Copilot self-check alone isn't enough to establish accuracy.  
**Step 6 — Produce the final leadership dashboard**  
This is where you can make the results understandable and useful to everyone, including people who will never look at the individual coded comments.  
I'd build a single-page dashboard with these elements.  
**Employee Voice | Survey Analysis**  
Illustrative dashboard layout — placeholder figures  
2026  
Comments  
**250**  
Coded themes  
**418**  
Risk flags  
**12**  
  
**Most discussed categories**  
Illustrative counts of distinct comments by category  
![Workload](Attachments/5E8831CD-AEC7-4E50-8726-91D4A0936C3C.png)  
  
  
**Sentiment across coded themes**  
**24%**  
Positive  
**61%**  
Negative  
**15%**  
Other  
  
Key findings  
Areas of concern  
Workload pressure, leadership communication, compensation  
Areas of appreciation  
Work flexibility and supportive management  
Items for human review  
Potential serious risks, with evidence linked to original comments  
**Prompt 6: Create the dashboard**  
Create an executive-level employee survey analysis dashboard using the validated data in "AI Comment Coding".  
Use PivotTables, charts, and summary tables linked to the coded data rather than manually entered totals.  
Include:  
1. Total number of distinct original comments analyzed.  
2. Total number of distinct coded themes.  
3. Number of distinct comments mentioning each topic category, ranked highest to lowest.  
4. Sentiment distribution for each category, displayed as a stacked bar chart.  
5. The top 10 recurring subtopics, including their frequency and dominant sentiment.  
6. Top positive themes and top negative themes.  
7. Counts of emerging concerns, potential serious risks, and items requiring human review.  
8. A concise executive summary of the most prominent findings, recurring concerns, employee appreciation, and actionable suggestions.  
Counting rules:  
* Use distinct Comment IDs for category-level comment counts.  
* Use Theme IDs for counts of distinct coded ideas.  
* Avoid double-counting repeated mentions of the same topic within one comment when reporting how many comments mention that topic.  
* State denominators clearly for percentages.  
* Do not interpret comment frequencies as the proportion of all employees holding a particular opinion.  
* Exclude unresolved or invalid coding from final reported metrics, and disclose the number excluded.  
Format the dashboard professionally with consistent colors, clear chart labels, and a separate section for flagged risks.  
Provide traceability from each summary category to the underlying coded comments.  
Create the dashboard in a new worksheet named "Survey Dashboard".  
Keep the existing source, coding, and validation worksheets intact.  
**7. Final workbook structure**  

| Worksheet | What it contains | Audience |
| -------------------- | --------------------------------------- | ------------------ |
| Raw Comments | Unmodified source | Analysts |
| Raw Comments Cleaned | Nonblank comments with IDs | Analysts |
| Coding Rules | Definitions and guidelines | Analysts/reviewers |
| AI Comment Coding | Extracted themes, categories, sentiment | Analysts |
| QA Review | Errors and items requiring review | Analysts |
| Comment Box Analysis | PivotTables and calculations | Analysts/managers |
| Survey Dashboard | Charts and executive takeaways | Leadership |
  


