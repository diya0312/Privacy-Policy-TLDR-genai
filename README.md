# LLM-Based Privacy Policy Analysis and TL;DR Generation

## Overview
This project is a **Generative AI (GenAI) application** that analyzes long privacy policy documents and generates a concise **TL;DR summary** explaining **what types of user data are collected** by a company.  
The goal is to make lengthy, complex privacy policies easier to understand for users by leveraging **LLM-based abstractive summarization**. The project focuses on real-world privacy documents from large organizations.

## Project Description
Privacy policies are often long (50–100+ pages), vague, and difficult for users to interpret. Simply reading them does not clearly answer the question:

> *“What data about me is actually being collected?”*

This project addresses that problem using a **two-stage GenAI pipeline**:

1. **Keyword-based Extraction**  
   Relevant privacy-related sections are first filtered using carefully selected keywords related to sensitive user data (e.g., device data, location, cookies, identifiers, third-party sharing, etc.). This reduces noise from irrelevant legal or compliance text.

2. **Abstractive Summarization using an LLM**  
   The extracted text is passed to an **LLM-based summarization model** (`facebook/bart-large-cnn`) which **generates new text** that condenses and paraphrases the information into a readable TL;DR summary.

Additionally, a **simple privacy risk indicator** (Low / Moderate / High) is computed using heuristic keyword analysis on the generated summary. This risk score is used only as an **informational aid**, not as a predictive model.


## Link with GenAI
This project qualifies as **Generative AI** because:

- It uses a **Large Language Model (LLM)** from Hugging Face.
- It performs **abstractive summarization**, generating **new human-readable text** rather than copying sentences.
- The primary output is **generated content**, not classification or prediction.

The rule-based privacy risk label is a secondary feature and does not replace the core generative task.


## Models and Tools Used
- **LLM Model:** `facebook/bart-large-cnn`
- **Framework:** Hugging Face Transformers
- **Environment:** Google Colab / Jupyter Notebook
- **Language:** Python
- **UI:** `ipywidgets` for interactive input and output

Initially, a faster summarization model (`distilbart-cnn-12-6`) was tested, but it produced lower-quality summaries. The final model was chosen to balance **summary quality and interpretability**.


## Repository Contents
- `Privacy_Policy.ipynb` – Main Notebook (core implementation)
- `Sample_Meta_Privacy_Policy.txt` – Text version of Meta’s privacy policy used for testing
- `Sample_Tata_Power_Policy.txt` – Text version of Tata Power’s privacy policy used for testing
- PDF versions of the policies – Included to show the original privacy policies.
- `Report.pdf` – Project report explaining methodology and results


## Running the Project

### Step 1: Clone or Download the Repository
### Step 2: Open the Notebook Privacy_Policy.ipynb
### Step 3: Install Dependencies
if running locally:
```
pip install transformers torch ipywidgets
```
### Step 4: Run the Notebook
Run all cells from top to bottom in order.

### Step 5: Provide Input

You can:
- Paste privacy policy text directly into the input area, OR
- Upload privacy policy of your choice in .txt format (can optionally use the sample .txt files provided)

The notebook processes large documents by extracting relevant sections before summarization.

### Step 6: Generate Output

Click Generate Summary to obtain:
- A TL;DR summary explaining collected user data
- A privacy risk indicator (Low / Moderate / High)

## Note on GitHub Notebook Preview

The last few cells in the notebook are not run in GitHub preview. GitHub is unable to properly render the notebook (Privacy_Policy.ipynb) due to the use of interactive ipywidgets, which can cause metadata rendering issues in GitHub’s notebook viewer. Hence only the first few cells are run and outputs are visible in the preview. Please download the notebook (.ipynb) and run it locally or in Google Colab to view the complete code, interactive UI, and outputs. The notebook runs correctly when executed locally.
