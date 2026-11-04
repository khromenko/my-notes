---
name: product-knowledge-base
description: Use when building product handbooks and onboarding docs.
---

# Product Knowledge Base Workflow

This skill governs the process of transforming raw product information (usually from a corporate website) into a structured, interlinked knowledge base for employees or clients, including training and verification materials.

## Procedure

1. **Source Mapping**
   - Analyze the official website or documentation to identify the full list of product categories and individual products.
   - Establish the hierarchy (e.g., Retail $\rightarrow$ Deposits $\rightarrow$ specific deposit types).

2. **Hub Creation**
   - Create or update a main index file (Hub) in the target directory.
   - For each product category, provide a one-sentence summary and a wikilink to the detailed article.

3. **Detailed Article Authoring**
   - For each product category, create a separate markdown file.
   - **Extraction Strategy**:
     - Start with the official source.
     - If the official site is unstable (502/403/bot-walled), use `web_search` and third-party financial aggregators/review sites to reconstruct the terms.
     - Format: Tabular data for conditions/rates, citations of sources.
   - **Content Structure**:
     - **Summary Table**: Compare products within the category (Symmetry: Currency, Term, Min Sum, Rate, Features).
     - **Detailed Breakdown**: Sections for each product containing specific conditions, restrictions, and calculation examples.
     - **Citations**: List all source URLs used for the specific page.

4. **Training Material Generation**
   - Create a `Tests/` subfolder within the product directory.
   - For each category, produce two files:
     - `Product_Test.md`: 
       - **Section 1 (Basic)**: 30-50 factual questions (e.g., \"What is the minimum sum?\").
       - **Section 2 (Cases)**: Practical scenarios requiring the application of rules (e.g., \"Client X has Y status, calculate the rate\").
     - `Product_Answers.md`: A clean, numbered key corresponding exactly to the test.

5. **Final Verification**
   - Verify all wikilinks in the Hub lead to existing files.
   - Ensure all test answers are verifiable using the detailed articles.

## Pitfalls & Rules

- **Flaky Corporate Sites**: Do not treat a 502 or 403 error as \"information not available.\" Corporate sites often have strict bot protection. Always fall back to `web_search` and trusted aggregators to find the actual product terms.
- **Test Separation**: Never put answers in the same file as the test. Employees must have a clean assessment sheet and a separate key for the trainer.
- **Case-Based Testing**: Case questions must provide enough variables (e.g., client status, amount, term) to force the agent/employee to look up multiple rules in the documentation.
- **Tabular Priority**: Use tables for all rate grids and condition comparisons; prose is for exceptions and nuances.
