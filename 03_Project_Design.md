# Phase 3: Project Design Phase

**Project:** LegalEase – AI-Powered Legal Document Generator

---

## System Architecture

LegalEase has three main parts: the **Frontend** (Streamlit), the **Backend** (FastAPI application) and the **AI layer** (Google Gemini API), followed by formatting modules for DOCX, PDF and TXT.

### Request Flow

```
User Interface (Streamlit)
 -> FastAPI Backend (main.py, routes.py)
 -> Document Generator (ai_core/gemini_generator.py)
 -> Gemini 1.5 Pro (Google API)
 -> Formatted Output (.txt, .docx, .pdf)
```

## Model Selection

| Model | Used For | Benefits |
|---|---|---|
| Gemini 1.5 Pro (via Google Generative AI SDK) | Legal document generation | Long context window (up to 1 million tokens), structured multi-part prompting, strong formatting and reasoning for formal documents and clauses |

## Module Design

| Module | Responsibility |
|---|---|
| `legalEaseAPI/main.py` | FastAPI app, root (`/`) health endpoint, includes router |
| `legalEaseAPI/routes.py` | `DocumentRequest` Pydantic model and `POST /generate` endpoint |
| `ai_core/gemini_generator.py` | `GeminiDocumentGenerator`: builds the prompt and calls Gemini |
| `ai_core/generator.py` | Formatting helpers for document output |
| `frontend/app.py` | Streamlit interface: inputs, preview, editing, downloads |
| `Image/` | `Logo.png` and `inverseLogo.png` branding assets |
| `config.py`, `.env`, `requirements.txt`, `run.sh` | Configuration, API key, dependencies and startup script |

## API Endpoint Design

| Endpoint | Purpose |
|---|---|
| `GET /` | Health check; confirms the service is running |
| `POST /generate` | Accepts `document_type`, `parties`, `terms`, dates and returns the generated document text |

## AI Design

- `GeminiDocumentGenerator` forms a structured prompt (document title, involved parties, effective date, terms and conditions) and sends it to Gemini via `generate_content`.
- The prompt instructs the model to ensure formal legal structure with multiple sections and legal clauses.
- The generated text is returned to FastAPI as `{"document": ...}`, then sanitized by the frontend before display and export.
