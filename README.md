# Embeddings Quality Tests and Scoring

Notebook-driven utilities to explore and evaluate embeddings quality for content stored in Supabase tables or wherever for that matter.

## Prerequisites

- Python 3.9+ installed
- VS Code with the Jupyter extension (recommended), or Jupyter installed
- A Supabase project (optional for offline/synthetic checks)

## Setup (Windows PowerShell)

It’s best to use a virtual environment. If a `venv/` folder exists in the repo, you can use it, or create your own fresh environment (recommended):

```powershell
# From the repository root
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install --upgrade pip
pip install -r requirements.txt
```

## Supabase configuration (for online checks)

The `testEmbeddingQuality.ipynb` notebook looks for two values you can paste directly into the first config cell:

- `SUPABASE_URL`
- `SUPABASE_ANON_KEY`

Where to find them
- In your Supabase project settings, copy the Project URL and the anon public API key.
- Paste them in the designated cell at the top of the notebook (they’re initialized to empty strings).

No Supabase? No problem. Later cells include synthetic self-checks that run entirely offline.

## Running the notebook

In VS Code
1. Open the folder in VS Code.
2. Open `testEmbeddingQuality.ipynb`.
3. Select the `.venv` (or `venv`) kernel/interpreter when prompted.
4. If you have Supabase credentials, fill in the config cell and run the notebook top-to-bottom. Otherwise, skip to the synthetic self-checks section.

In Jupyter (classic/lab)
```powershell
jupyter notebook
# or
jupyter lab
```
Open `testEmbeddingQuality.ipynb`, select the `.venv` kernel, and Run All.

## Chunker benchmark (structure‑aware chunking)

If you’re experimenting with chunking strategies for RAG, this repo also includes `Chunker_benchmark.ipynb`.

What it does
- Loads and cleans OCR’d text from documents via Azure Document Intelligence (formerly Form Recognizer)
- Applies structure‑aware chunking using a combination of LangChain splitters (e.g., MarkdownHeaderTextSplitter, RecursiveCharacterTextSplitter)
- Optionally refines chunks semantically when an OpenAI API key is provided
- Provides interactive controls to tune chunk size/overlap and visualize performance (chunk counts, processing time, average sizes, simple importance scores)

Extra packages (only for this notebook)
- langchain, langchain-community, langchain-openai, langchain-experimental, langchain-text-splitters
- azure-ai-documentintelligence (and its dependencies)
- ipywidgets (for interactive controls)

Quick start
1. Ensure your virtual environment is active and base dependencies are installed (see Setup above).
2. Install the extra packages listed above. You can either:
	- Use the install cell inside the notebook, or
	- Install them in your environment.
3. Open `Chunker_benchmark.ipynb` and run the first cell to see the UI.
4. When prompted in the notebook UI:
	- Enter your Azure Document Intelligence endpoint and API key to process real documents
	- Optionally provide an OpenAI API key to enable semantic chunking; otherwise, the notebook will run without it
5. Use the “Configure Chunker” and “Performance Test” sections to compare different chunk sizes/overlaps and review the charts/tables.

Notes
- `Chunker_benchmark.ipynb` is self‑contained and can run without Supabase.
- Azure credentials are only needed if you want to process your own documents via Azure OCR; the sample text modes work without them.