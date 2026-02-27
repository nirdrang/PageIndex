# AGENTS.md

## Cursor Cloud specific instructions

### Overview

PageIndex is a Python-based vectorless, reasoning-based RAG framework. It generates hierarchical tree structure indexes from PDF/Markdown documents and uses LLMs for agentic retrieval. See `README.md` for full documentation.

### Running the application

- **Markdown processing** (no OpenAI key needed when summaries disabled):
  `python3 run_pageindex.py --md_path <file.md> --if-add-node-summary no`
- **PDF processing** (requires `CHATGPT_API_KEY`):
  `python3 run_pageindex.py --pdf_path <file.pdf>`
- CLI options: `python3 run_pageindex.py --help`

### Key caveats

- The `CHATGPT_API_KEY` environment variable (set via `.env` file in repo root) is required for all PDF processing and any markdown processing with `--if-add-node-summary yes` or `--if-add-doc-description yes`. Without it, API calls will fail with retries.
- There is no formal test suite, linter, or build step. Validation is done by running `run_pageindex.py` and inspecting the JSON output in `./results/`.
- Test PDFs are in `tests/pdfs/` and reference tree structures in `tests/results/`.
- Output goes to `./results/` (JSON) and `./logs/` (processing logs).
- No Docker, Makefile, or CI/CD configuration exists in this repository.
