\# Aspect-Based Sentiment Analysis of Online Education Reviews

\*\*Task:\*\* Aspect-Based Sentiment Analysis (ABSA)    
\*\*Language:\*\* Russian    
\*\*Domain:\*\* Online Education Reviews    
\*\*Annotation Scheme:\*\* Aspect Term – Aspect Category – Opinion – Sentiment    
\*\*Models:\*\* GPT-4.1 mini, DeepSeek V3.2, YandexGPT 5.1 Pro

\---

\#\# About the Project

This repository contains materials related to a study on \*\*aspect-based sentiment analysis (ABSA)\*\* of Russian-language reviews of online courses.

The task consists of extracting quadruples in the form of:

\> \*\*Aspect Term – Aspect Category – Opinion – Sentiment\*\*

from review texts using large language models (LLMs) and prompt engineering techniques.

\---

\#\# Repository Contents

This repository includes the part of the research related to automatic annotation and evaluation of annotation quality.

\#\#\# 1\. Automatic Annotation

Review texts are processed through LLM APIs to automatically extract quadruples consisting of:

\- aspect term;  
\- aspect category;  
\- opinion expression;  
\- sentiment polarity.

Code: \`notebooks/llm\_annotation.ipynb\`

\> Prompt templates used for LLM-based annotation are included in the notebook.

\#\#\# 2\. Annotation Quality Evaluation

Automatic annotations are compared against a manually created gold-standard annotation using two evaluation approaches:

\- exact and partial quadruple matching (precision, recall, F1-score) — \`notebooks/quadruple\_matching\_evaluation.ipynb\`;  
\- semantic similarity of extracted spans — \`notebooks/semantic\_similarity\_evaluation.ipynb\`.

\---

\#\# Data

\#\#\# Online Course Reviews Corpus

The \`data/\` directory contains the main corpus of Russian-language online course reviews collected from the review platforms \*\*Sravni.ru\*\* and \*\*Otzovik\*\*.

Files are numbered according to the processing workflow.

| File | Description | Reviews |  
|--------|-------------|:-------:|  
| \`01\_full\_corpus\_2400.csv\` | Complete corpus containing all collected reviews | 2,400 |  
| \`02\_annotation\_sample\_300.csv\` | Sample used for automatic annotation | 300 |  
| \`03\_evaluation\_sample\_100.csv\` | Sample used for evaluation | 100 |  
| \`04\_gold\_annotation\_100.csv\` | Gold-standard annotation | 100 |  
| \`05\_gpt41mini\_annotation\_100.csv\` | Automatic annotation produced by GPT-4.1 mini | 100 |  
| \`06\_deepseek\_v32\_annotation\_100.csv\` | Automatic annotation produced by DeepSeek V3.2 | 100 |  
| \`07\_yandexgpt\_51pro\_annotation\_100.csv\` | Automatic annotation produced by YandexGPT 5.1 Pro | 100 |

Files \`04–07\` contain annotations for the same set of 100 reviews, including one manual (gold-standard) annotation and three automatic annotations, enabling a comparison between different LLMs and expert annotation.

\---

\#\# Corpus Structure

\#\#\# Unannotated Files

| Column | Description |  
|----------|-------------|  
| \`review\_id\` | Unique review identifier |  
| \`review\_text\` | Full review text |  
| \`review\_url\` | URL of the review source |

\#\#\# Annotated Files

| Column | Description |  
|----------|-------------|  
| \`review\_id\` | Unique review identifier |  
| \`review\_text\` | Full review text |  
| \`aspect\_term\` | Aspect mention extracted from the review |  
| \`opinion\` | Opinion expression associated with the aspect |  
| \`aspect\` | Aspect category (e.g., Course Materials, Support Team) |  
| \`sentiment\` | Sentiment polarity (positive, negative, neutral) |  
| \`review\_url\` | URL of the review source |

\---

\#\# Code

The \`notebooks/\` directory contains Jupyter notebooks (developed in Google Colab) implementing the research stages presented in this repository.

| Notebook | Purpose |  
|-----------|---------|  
| \`llm\_annotation.ipynb\` | LLM API integration and automatic annotation of reviews |  
| \`quadruple\_matching\_evaluation.ipynb\` | Evaluation based on exact and partial quadruple matching (precision, recall, F1-score) |  
| \`semantic\_similarity\_evaluation.ipynb\` | Evaluation based on semantic similarity (cosine similarity) of extracted spans |

\---

\#\# Evaluation Methodology

The quality of automatic annotation is evaluated against the gold-standard annotation using two complementary approaches.

\#\#\# Exact and Partial Matching

Predicted and gold-standard quadruples are aligned and compared using strict and partial matching criteria.

Precision, recall, and F1-score are calculated for both settings.

\#\#\# Semantic Similarity

Cosine similarity is computed between vector representations of automatically extracted aspect terms and opinion expressions and their corresponding gold-standard annotations.

\---

\#\# Repository Structure

\`\`\`text  
absa-online-education-ru/  
│  
├── data/  
│   ├── 01\_full\_corpus\_2400.csv  
│   ├── 02\_annotation\_sample\_300.csv  
│   ├── 03\_evaluation\_sample\_100.csv  
│   ├── 04\_gold\_annotation\_100.csv  
│   ├── 05\_gpt41mini\_annotation\_100.csv  
│   ├── 06\_deepseek\_v32\_annotation\_100.csv  
│   └── 07\_yandexgpt\_51pro\_annotation\_100.csv  
│  
├── notebooks/  
│   ├── llm\_annotation.ipynb  
│   ├── quadruple\_matching\_evaluation.ipynb  
│   └── semantic\_similarity\_evaluation.ipynb  
│  
└── README.md  
\`\`\`  
