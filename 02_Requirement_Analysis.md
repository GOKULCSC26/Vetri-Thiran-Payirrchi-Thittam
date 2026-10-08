# Phase 2: Requirement Analysis Phase

**Project:** LegalEase – AI-Powered Legal Document Generator

---

## Functional Requirements

- Provide a web form with inputs for document type, parties involved, terms and conditions (semicolon-separated) and effective date, plus a **Generate Document** button.
- Generate a structured legal document with multiple sections and clauses using Gemini 1.5 Pro.
- Show the generated document in a styled HTML preview below the form.
- Allow the user to edit the generated text through an editable text area (**Edit Document**).
- Export the document as:
  - `.TXT`
  - `.DOCX` (logo, headings, terms table, footer)
  - `.PDF` (logo, header/footer on every page)
- Sanitize AI output (special characters, typographic quotes) before formatting.

## Non-Functional Requirements

- Simple, clean and responsive interface built with Streamlit, with branding (logo and title).
- Modular code with separate modules for AI generation, API routes, formatting and frontend.
- Professional-grade formatting standards across all export formats.
- Gemini API key stored securely in a `.env` file and never shared in the code.
- Secure handling of sensitive user data.

## Inputs and Outputs

| Input | Description | Example |
|---|---|---|
| Document type | Type of legal document to generate | Freelance Work Contract |
| Parties involved | Names and roles of the individuals or entities | Jane Doe (Service Provider), TechNova Inc. (Client) |
| Terms & conditions | Specific clauses; semicolons create bullet points | Payment within 7 days of invoice; Work delivered by May 15, 2025 |
| Effective date | Date the agreement becomes legally valid | April 15, 2025 |

**Output:** an AI-generated legal document with preview and editing, downloadable as `.TXT`, `.DOCX` or `.PDF`.

## Pre-requisites

| Requirement | Details |
|---|---|
| Python 3.10+ | Installed with pip for dependency management |
| FastAPI & Uvicorn | Backend framework and ASGI server |
| Streamlit | Frontend UI framework |
| Google Gemini API | `google-generativeai` SDK and a Gemini API key |
| Supporting libraries | python-docx, fpdf, Pillow, requests, python-dotenv |

## Assumptions and Constraints

- Generation needs a valid Gemini API key and an internet connection.
- AI output may vary between runs and must be reviewed before use.
- This version runs locally; it has no user accounts or saved history.
