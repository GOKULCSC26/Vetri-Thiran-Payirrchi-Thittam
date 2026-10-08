# Phase 5: Project Development Phase

**Project:** LegalEase – AI-Powered Legal Document Generator

---

## Development Flow

1. The user opens the Streamlit app, enters the document type, parties, terms and effective date, and clicks **Generate Document**.
2. The frontend sends a POST request with a JSON payload to the FastAPI `/generate` endpoint.
3. `routes.py` validates the data with the `DocumentRequest` model and calls `GeminiDocumentGenerator.generate_document(...)`.
4. The generator sends the structured prompt to Gemini 1.5 Pro and returns the response text.
5. The text is sanitized and shown as a dark-themed, scrollable HTML preview.
6. The user can click **Click to Edit Document** to modify the text, then download it as `.TXT`, `.DOCX` or `.PDF`.

## Core Functions

| Function | Description |
|---|---|
| `generate_document(...)` | Builds the prompt and calls Gemini 1.5 Pro to produce the legal document |
| `sanitize_text(text)` | Removes special characters and typographic quotes for clean formatting |
| `format_docx(text, doc_type)` | python-docx: embeds the logo, adds title and paragraph formatting (Times New Roman), auto-generates a Terms table from semicolon-separated input, adds a footer |
| `format_pdf(text, doc_type)` | FPDF with custom header/footer: centered logo, bold section headings, bullet-style terms |
| `format_html_preview(text)` | Converts output to styled HTML blocks for inline display |

## Frontend

- Streamlit page configured with `st.set_page_config` (centered layout); logo centered using a three-column layout; subtle centered title "AI Legal Document Generator".
- Input fields: Document Type, Parties Involved, Terms & Conditions (semicolons for bullet points) and Effective Date.
- Dark-themed preview card, an editable text area (height 300) and three download buttons with auto-generated file names.

## Technology Stack

| Layer | Technology |
|---|---|
| Language / Backend | Python 3.10+, FastAPI, Uvicorn, Pydantic |
| Frontend | Streamlit |
| AI | Google Gemini 1.5 Pro (`google-generativeai` SDK, API key via `.env`) |
| Document export | python-docx, FPDF, Pillow |

## How to Run

```bash
pip install -r requirements.txt
# add your Gemini API key to the .env file
uvicorn legalEaseAPI.main:app --reload   # backend,  http://127.0.0.1:8000
streamlit run frontend/app.py            # frontend, http://localhost:8501
```
