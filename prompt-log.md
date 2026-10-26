# Prompt Log & Session History

## 2026-09-22: Stage 0 Workspace Setup & Portfolio Optimization
- **Prompt / Request**: Asked AI assistants (Gemini Notebook and ChatGPT) how to fix Stage 0 feedback, generate folder READMEs, and structure the repository according to course standards.
- **AI Output Provided**: Suggested specific one-line descriptions for 8 skeleton folders (`analysis/`, `docs/`, `data/`, etc.), the need for a prompt-log entry, and instructions for adding an engagement index.
- **My Revisions / Verification**: I compared the suggestions with the professor's feedback and created the required files manually in GitHub.

## 2026-09-28: Stage 0 Feedback Resolution & Git Commit Standards
- **Prompt / Request**: Consulted AI on how to resolve the remaining items from the professor's Stage 0 feedback (updating `docs/decisions/README.md`, adding links to Stage 0 & 1 in the Engagement Index, and understanding the Git commit message requirement).
- **AI Output Provided**: Explained the required file edits, clarified that past commit history does not need editing, and provided the convention for descriptive commit messages using explicit action verbs (`Add ...`, `Update ...`).
- **My Revisions / Verification**: Updated `docs/decisions/README.md` with a single-line explanation, added working markdown links for Stage 0 and Stage 1 in `README.md`, and adopted descriptive commit messages on GitHub Web.

## 2026-09-29: Stage 1 Brief Critique Session
- **Prompt / Request**: Submitted my self-written Stage 1 brief for an AI Critique Attack (Genimi Notebook) to identify implicit assumptions, unsupported claims, and verify hypothesis falsiability without allowing prose rewrites.
- **AI Output Provided**: AI identified implicit assumptions regarding labor budget availability and $P=MC$ crossovers, highlighted unsupported claims regarding gross vs. net profitability, and confirmed that my 20/20/24 bed hypothesis is strictly falsifiable by Stage 2 modeling.
- **My Revisions / Verification**: Verified that my brief fulfills all Stage 1 requirements and that the hypothesis is ready for Stage 2 Excel Solver testing.

## 2026-09-29: Stage 0 README Index Cleanup
- **Prompt / Request**: Asked AI (Genimi Notebook) for the precise markdown formatting fix for nested bullet points in the root README index based on instructor feedback.
- **AI Output Provided**: AI identified the stray asterisks in the index list and provided clean markdown syntax along with a descriptive commit message.
- **My Revisions / Verification**: Removed stray asterisks from `README.md`, verified the index rendering on GitHub, and committed with `Fix bullet syntax in README index`.

## 2026-09-30: Stage 1 Brief Critique Finding Based on Instructor Feedback
- **Critique Finding 1 (Case Numbers)**: Added explicit parameters (64 beds, 36 weeks, $20,000 fixed cost, labor limits) to "The problem".
- **Critique Finding 2 (Fact Correction & Logic)**: Corrected crop facts and incorporated carrot fertilizer cost ($440) into "Hypothesis".
- **Critique Finding 3 (Falsification Threshold)**: Set numerical thresholds (>24 mesclun beds or <20 tomato/carrot beds) in "How I would know I was wrong".

## 2026-09-30: Stage 1 Brief Revisions Based on Instructor Feedback
- **Prompt / Request**: Asked AI to translate and explain the instructor's feedback on the Stage 1 brief.
- **AI Output Provided**: Translation and detailed explanation of the instructor's critique points.
- **My Revisions / Verification**: Revised "The problem", "Hypothesis", and "How I would know I was wrong" in accordance with the instructor's critique, and documented responses for each critique finding

## 2026-10-06: Stage 1 Brief Revisions Based on Instructor Feedback
- **Prompt / Request**: Asked AI(Genimi Notebook) to translate and explain the instructor's feedback on the Stage 1 brief.
- **AI Output Provided**: Translation and detailed explanation of the instructor's critique points.
- **My Revisions / Verification**: Revised the Stage 1 Brief in accordance with the instructor's critique and documented responses to each critique point.

## 2026-10-06: Stage 1 Brief Critique Response
- **Critique Finding**: The AI critique pointed out that labor hours and exponential diminishing returns (10% penalty per tomato bed) were not fully quantified in my initial draft.
- **My Decision / Response**: I acknowledged the critique and calculated the exact marginal labor requirement for the 20th tomato bed (1,651.3 field hours, costing $28,666.57). However, I **kept the prediction** of 20 tomato, 20 carrot, and 24 mesclun beds in my initial brief to serve as an intuitive baseline to compare directly against the optimal solution from Excel Solver in Stage 1.2.

## 2026-10-13: Stage 1 Brief Revisions Based on Instructor Feedback
- **Prompt / Request**: Asked AI(Genimi Notebook) to translate and explain the instructor's feedback on the Stage 1 brief.
- **AI Output Provided**: Translation and detailed explanation of the instructor's critique points.
- **My Revisions / Verification**: Revised the Stage 1 Brief in accordance with the instructor's critique and documented responses to each critique point.

## 2026-10-14: Stage 2 Spec, Build, Audit Created
- **Prompt / Request**: Asked AI(Genimi Notebook and ChatGPT) to tto help create and check my Stage 2 Excel model.
- **AI Output Provided**: Helped explain the requirements, create the Excel model, and check the calculations.
- **My Revisions / Verification**: Checked the formulas, ran Solver, fixed a missing labor constraint, and compared marginal costs with Farm Profit Lab.

## 2026-10-20: Stage 1 Brief Revisions Based on Instructor Feedback
- **Prompt / Request**: Asked AI(Genimi Notebook and ChatGPT) to translate and explain the instructor's feedback on the Stage 1 brief.
- **AI Output Provided**: Translation and detailed explanation of the instructor's critique points.
- **My Revisions / Verification**: Revised the Stage 1 Brief in accordance with the instructor's critique and documented responses to each critique point (in Hypothesis).

## 2026-10-20: Stage 2 Spec, Build, Audit Revisions Based on Instructor Feedback
- **Prompt / Request**: Asked AI(Genimi Notebook and ChatGPT) to translate and explain the instructor's feedback on the Stage 2 Spec, Build, Audit.
- **AI Output Provided**: Translation and detailed explanation of the instructor's critique points.
- **My Revisions / Verification**: Revised the Stage 2 in accordance with the instructor's critique, documented responses to each critique point (in Inputs, Crossing Rule, and Validation Rules), and creating new model.xlsx.

## 2026-10-22,23: Stage 3 Analysis + Prompt Log
- **Prompt / Request**: Asked AIs (ChatGPT and Gemini Notebook) to translate, help me understand marginal cost, check standalone profitability, test crop capacity limits using Excel Solver, and add charts to GitHub.
- **AI Output Provided**: Translation, explained the economic concepts and provided step-by-step instructions for checking Excel results, using Solver, and uploading figures.
My Revisions / Verification: checked the marginal costs in my Excel model, tested each crop separately, and used Solver to test 21 carrot beds and 31 mesclun beds. Also, created three charts in Excel and confirmed they displayed correctly on GitHub.

## Reflection — Stage 1.3

### Where AI Helped
AI helped me understand how to complete this work step by step. It was my first time using Excel Solver and GitHub, so I did not know how to use them at the beginning. AI explained each process in detail, which helped me complete all the tasks. Since I am an international student, AI also helped me with English expressions, grammar, and translation.

### Where It Was Wrong
The most important problem happened when I first used Excel Solver. Some conditions were missing, and the calculation settings were unclear, especially how decimal values should be handled. Because of this, I could not get the correct result. I could not solve this problem only with my own knowledge, and the professor's feedback helped me understand what was wrong and fix the model. Also, when I first worked on the assignment, Gemini Notebook did not always give accurate results, so I started using ChatGPT more often.

### How I Verified
I verified the results by running the Excel sheet by myself and changing the numbers of Tomatoes, Carrots, and Mesclun many times based on my predictions and the Solver results. This helped me check whether the results were reasonable. Creating charts also helped me understand the important points for maximizing profit. For example, I changed the carrot limit from 20 to 21 beds and confirmed that the profit increased by about **$353**. This helped me verify that the model was working correctly.

## 2026-10-26: Stage 2 Spec, Build, Audit Revisions Based on Instructor Feedback
- **Prompt / Request**: Asked AI(Genimi Notebook and ChatGPT) to translate and explain the instructor's feedback on the Stage 2 Spec, Build, Audit.
- **AI Output Provided**: Translation and detailed explanation of the instructor's critique points.
- **My Revisions / Verification**: Revised the Stage 2 creating new model.xlsx, and fixing spec.md.
