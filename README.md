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

The notebook looks for two values you can paste directly into the first config cell:

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