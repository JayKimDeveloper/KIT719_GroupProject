# KIT719 Group Project — Information Retrieval System

This repository contains the group project for **KIT719: Natural Language Processing and Generative AI** at the University of Tasmania.

The project implements an Information Retrieval (IR) system using the **NLTK Reuters Corpus**. It includes text preprocessing, document indexing, TF-IDF and BM25 ranking, query processing, and performance evaluation.

## Project Objectives

The project aims to:

- load and inspect the Reuters text collection;
- preprocess natural-language documents and queries;
- construct an inverted index and TF-IDF document matrix;
- retrieve and rank documents using TF-IDF cosine similarity and BM25;
- support spelling correction and query expansion;
- provide an interactive console-based search interface; and
- evaluate retrieval performance using standard IR metrics.

## Main Features

### 1. Dataset Selection

- Uses the Reuters Corpus provided by NLTK.
- Loads Reuters documents and category labels.
- Supports inspection of dataset size, categories, and document content.

### 2. Text Preprocessing

The preprocessing pipeline includes:

- lowercasing;
- tokenisation;
- punctuation and non-alphabetic token removal;
- stop-word removal;
- Porter stemming; and
- WordNet lemmatisation with part-of-speech information.

### 3. Document Indexing

The system constructs:

- an inverted index;
- a term vocabulary;
- a sparse TF-IDF document-term matrix; and
- document statistics required for BM25 ranking.

### 4. Retrieval and Ranking

Two ranking methods are implemented:

- **TF-IDF with cosine similarity**
- **BM25**

The system returns the highest-ranked Reuters documents for a user query.

### 5. Query Processing

The query processing module includes:

- query preprocessing;
- spelling correction;
- WordNet-based query expansion; and
- an interactive console search application.

### 6. Performance Evaluation

The evaluation module compares different combinations of:

- no stemming or lemmatisation;
- Porter stemming;
- WordNet lemmatisation;
- TF-IDF ranking; and
- BM25 ranking.

The implemented metrics include:

- Precision@K;
- Recall@K;
- F1@K; and
- Mean Average Precision (MAP).

Evaluation results can be presented using comparison tables and charts.

## Repository Structure

```text
KIT719_GroupProject/
├── LICENSE
├── README.md
└── notebook/
    ├── KIT719-Project1_Report.docx
    ├── KIT719_IR_System.ipynb
    └── Project1.ipynb
```

### Main Files

| File | Description |
|---|---|
| `notebook/Project1.ipynb` | Main project notebook containing the current Reuters IR implementation and evaluation |
| `notebook/KIT719_IR_System.ipynb` | Alternative or earlier IR system implementation |
| `notebook/KIT719-Project1_Report.docx` | Project report |
| `LICENSE` | Apache License 2.0 |

> Before final submission, the team should identify one notebook as the final implementation and ensure that all reported evaluation results match that notebook.

## Requirements

Recommended environment:

- Python 3.12
- Jupyter Notebook
- NLTK
- NumPy
- SciPy
- scikit-learn
- Matplotlib

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/JayKimDeveloper/KIT719_GroupProject.git
cd KIT719_GroupProject
```

To update an existing local copy:

```bash
git pull origin main
```

### 2. Create a Virtual Environment

#### macOS or Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
```

#### Windows PowerShell

```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
```

### 3. Install Python Packages

```bash
python -m pip install --upgrade pip
python -m pip install notebook ipykernel nltk numpy scipy scikit-learn matplotlib
```

On Homebrew-managed Python installations, install packages inside the virtual environment. Do not install project packages into the system Python environment.

### 4. Download Required NLTK Resources

Run:

```bash
python - <<'PY'
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

print("NLTK resources installed successfully.")
PY
```

### 5. Register the Jupyter Kernel

```bash
python -m ipykernel install \
  --user \
  --name kit719-ir \
  --display-name "Python 3.12 (KIT719)"
```

## Running the Project

Start Jupyter Notebook from the repository root:

```bash
python -m notebook
```

In the browser:

1. Open the `notebook` directory.
2. Open `Project1.ipynb`.
3. Select **Python 3.12 (KIT719)** as the kernel.
4. Run the notebook cells in order.

To run all cells:

```text
Kernel → Restart Kernel and Run All Cells
```

## Console Search Application

The notebook contains an interactive console application. When the following function is executed:

```python
run_console_app()
```

the notebook waits for a query:

```text
User Query:
```

Example:

```text
grain trade policy
```

Enter the following command to close the console application:

```text
exit
```

The notebook may appear to stop during **Run All** because the console application is waiting for keyboard input. To run the complete notebook without interaction, temporarily comment out the call:

```python
# run_console_app()
```

## Example Workflow

```text
Reuters documents
        ↓
Text preprocessing
        ↓
Inverted index and TF-IDF matrix
        ↓
Query preprocessing
        ↓
TF-IDF or BM25 ranking
        ↓
Top-ranked documents
        ↓
Performance evaluation
```

## Team Responsibilities

Update this table with the final team member names before submission.

| Team Member | Main Responsibilities |
|---|---|
| YoungHyun Kim | Dataset selection, data inspection, text preprocessing, report Sections 1, 2.1, and 3.1 |
| Member 2 | Document indexing, TF-IDF, BM25, retrieval and ranking, report Sections 2.2–2.3 and 3.2–3.3 |
| Member 3 | Query processing, spelling correction, query expansion, console application, evaluation, discussion, and report Sections 2.4, 3.4, 4, and 5 |

## Reproducibility Checklist

Before submission, confirm that:

- the notebook runs from a fresh kernel without unexpected errors;
- all required NLTK resources are documented;
- one notebook is clearly identified as the final implementation;
- TF-IDF evaluation uses the same cosine-similarity method as the search function;
- report tables and charts match the latest notebook output;
- interactive cells are clearly identified;
- team member names and student details are complete;
- generated result files are included where required; and
- AI-assisted work is acknowledged according to the unit requirements.

## Known Limitations

Potential limitations of the current implementation include:

- spelling correction may select an unintended word when several candidates have the same edit distance;
- WordNet query expansion may introduce terms that are not relevant to the original query context;
- evaluation results depend on the relevance definition derived from Reuters categories;
- an interactive input cell can interrupt automatic notebook execution; and
- the two notebooks may contain different implementation choices and should be consolidated before submission.

## Academic Use

This repository was created for a university assessment. Any use of this code should comply with the University of Tasmania's academic integrity requirements.

## License

This project is licensed under the **Apache License 2.0**. See the `LICENSE` file for details.
