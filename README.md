# KIT719 Group Project — RAG Chatbot with Graph-Based Reasoning

This repository contains **Project 2 for KIT719: Natural Language Processing and Generative AI** at the University of Tasmania.

The project implements a conversational **Retrieval-Augmented Generation (RAG) chatbot** using the NLTK Reuters Corpus and student-created local documents.

The system combines semantic retrieval, a knowledge graph, SPARQL, Personalised PageRank, and an open-source LLM to answer natural-language questions with supporting evidence.

---

## Main Features

- Reuters Corpus with additional local knowledge documents
- NLP preprocessing reused from Project 1
- TF-IDF lexical retrieval baseline
- MiniLM dense semantic retrieval
- RDF document-entity knowledge graph
- SPARQL graph queries
- Personalised PageRank for graph-assisted ranking
- Prompt-driven evidence selection
- Qwen2.5 answer generation
- Gradio chatbot interface
- Source/evidence display
- Graph ON/OFF comparison
- Evaluation of retrieval, grounding and answer correctness
- Graceful error handling

---

## System Specification

| Component | Configuration |
|---|---|
| Dataset | NLTK Reuters + 10 local documents |
| Total documents | 10,798 |
| Embedding model | `sentence-transformers/all-MiniLM-L6-v2` |
| Generator | `Qwen/Qwen2.5-0.5B-Instruct` |
| Chunk size | 180 tokens |
| Chunk overlap | 30 tokens |
| Dense retrieval | Cosine similarity |
| NER | spaCy `en_core_web_sm` |
| Entity types | ORG, PERSON, GPE, LOC |
| Graph format | RDF |
| Graph query | SPARQL |
| Graph analysis | Personalised PageRank |
| Graph weight | 0.15 |
| Evidence limit | 3 passages |
| Interface | Gradio |

The graph-enabled retrieval score is:

```text
combined score =
cosine similarity + 0.15 × normalised graph score
```

---

## Repository Structure

```text
KIT719_GroupProject/
├── README.md
├── LICENSE
├── notebook/
│   └── Project2_Colab.ipynb
├── local_documents/
├── evaluation_questions.json
├── results/
│   ├── evaluation.csv
│   ├── traces.json
│   └── graph_stats.json
└── knowledge_graph.ttl
```

> Student-created documents must remain local and must not be uploaded to a public website or public repository.

---

## Requirements

Recommended environment:

- Python 3.11 or later
- Jupyter Notebook
- NLTK
- spaCy
- sentence-transformers
- transformers
- PyTorch
- RDFLib
- NetworkX
- scikit-learn
- pandas
- NumPy
- Gradio
- Matplotlib

---

## Local Installation

### 1. Clone the repository

```bash
git clone https://github.com/JayKimDeveloper/KIT719_GroupProject.git
cd KIT719_GroupProject
```

To update an existing copy:

```bash
git pull origin main
```

### 2. Create a virtual environment

#### macOS / Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
```

#### Windows PowerShell

```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
python -m pip install notebook ipykernel nltk spacy sentence-transformers transformers torch rdflib networkx scikit-learn pandas numpy gradio matplotlib
```

### 4. Install the spaCy model

```bash
python -m spacy download en_core_web_sm
```

### 5. Download NLTK resources

```python
import nltk

resources = [
    "reuters",
    "punkt",
    "punkt_tab",
    "stopwords",
    "wordnet",
    "omw-1.4",
    "averaged_perceptron_tagger",
    "averaged_perceptron_tagger_eng",
]

for resource in resources:
    nltk.download(resource)
```

---

## Local Document Setup

Place the ten student-created text files inside:

```text
local_documents/
```

Also ensure that:

```text
evaluation_questions.json
```

is available in the location expected by the notebook.

The local documents must be processed together with the Reuters Corpus but must remain stored locally.

---

## Running the Project

Start Jupyter Notebook from the repository root:

```bash
python -m notebook
```

Then:

1. Open `Project2_Colab.ipynb`.
2. Select the correct Python environment/kernel.
3. Run the notebook cells in order.
4. Load the Reuters Corpus and local documents.
5. Run preprocessing and chunking.
6. Generate MiniLM embeddings.
7. Build the RDF knowledge graph.
8. Run SPARQL and Personalised PageRank components.
9. Load the Qwen model.
10. Launch the Gradio chatbot.

A successful document-loading stage should contain:

```text
Reuters documents: 10,788
Local documents: 10
Total documents: 10,798
```

---

## Using the Chatbot

The Gradio interface supports natural-language questions and includes a **Graph ON/OFF** option.

### Graph OFF

```text
Question
→ Dense Retrieval
→ Evidence Selection
→ Qwen
→ Answer
```

### Graph ON

```text
Question
→ Dense Retrieval
→ SPARQL Expansion
→ Personalised PageRank
→ Evidence Selection
→ Qwen
→ Answer
```

The interface also displays retrieved evidence and graph-tool execution information.

The required welcome message is:

```text
welcome to KIT719
```

---

## Evaluation

The system is evaluated using **12 prepared questions** under:

- Dense RAG
- Dense + Graph RAG

The evaluation considers:

- context recall;
- expected-document coverage;
- SPARQL execution;
- citation validity;
- answer groundedness;
- factual correctness; and
- response time.

Evaluation outputs are stored in:

```text
results/evaluation.csv
results/traces.json
results/graph_stats.json
```

Detailed evaluation results and failure analysis are provided in the **Project 2 report**.

---

## Troubleshooting

### Missing spaCy model

```bash
python -m spacy download en_core_web_sm
```

### Missing NLTK resource

```python
import nltk
nltk.download("RESOURCE_NAME")
```

### Local documents not found

Check that the ten `.txt` files are stored in:

```text
local_documents/
```

### Invalid model output

Qwen may occasionally return malformed JSON or invalid source labels. The application should display a warning rather than crash.

Check the evidence table and raw model output when debugging.

---

## Before Submission

Confirm that:

- the notebook runs from a fresh local environment;
- all ten local documents are available;
- local documents have not been uploaded publicly;
- SPARQL and graph retrieval run correctly;
- the Gradio interface works;
- the welcome message is exactly `welcome to KIT719`;
- all 12 evaluation questions can be executed; and
- evaluation outputs match the final report.

---

## Team Members

| Student ID | Name |
|---|---|
| 774353 | Younghyun Kim |
| 760308 | Mohammad Ammar Bin Hazrin Chong |
| 752937 | Rewadee Sirichaisuttikorn |

---

## Academic Use

This repository was created for a University of Tasmania assessment.

Use of the project must comply with the University's academic integrity requirements.

## License

See the `LICENSE` file for licence information.
