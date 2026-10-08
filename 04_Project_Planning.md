# Phase 4: Project Planning Phase

**Project:** LegalEase – AI-Powered Legal Document Generator

---

## Milestones

| Milestone | Title | Activities |
|---|---|---|
| Milestone 1 | Model Selection and Architecture | Select Gemini 1.5 Pro; define the architecture; set up the development environment and folder structure |
| Milestone 2 | Core Functionalities Development | Implement document generation, output formatting, editable preview and downloads; build the FastAPI backend |
| Milestone 3 | API Logic Integration | Create `main.py`; handle generation logic in `routes.py` with the `DocumentRequest` model and `/generate` endpoint |
| Milestone 4 | Frontend Development | Build the Streamlit interface, HTML preview, editing and multi-format downloads |
| Milestone 5 | Deployment | Run locally with Uvicorn and Streamlit; test all functionalities end to end |

## Team Details

| Role | Name |
|---|---|
| Team Leader | Gokul |
| Team Member | Mani |
| Team Member | Rajesh |
| Team Member | Veeramacikkam |

## Deliverables

- Source code (FastAPI backend, Gemini generator, Streamlit frontend).
- `requirements.txt`, `.env` template and `run.sh`.
- Logo assets and formatting modules for DOCX, PDF and TXT.
- Screenshots of every feature in action.
- Phase-wise project report.

## Risks and Mitigation

| Risk | Mitigation |
|---|---|
| Accuracy of AI-generated legal text | Structured prompts; editable preview so users review and correct the text before export |
| Special characters or typographic quotes breaking formatting | `sanitize_text` cleans the output before formatting |
| Inconsistent export formatting | Dedicated `format_docx`, `format_pdf` and `format_html_preview` functions; tested on all formats |
| Data privacy concerns | API key kept in `.env`; secure handling of sensitive user data |
| Backend not running when the UI is used | Documented start-up order: Uvicorn first, then Streamlit |
