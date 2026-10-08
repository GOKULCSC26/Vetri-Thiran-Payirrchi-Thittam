# Phase 6: Project Testing Phase

**Project:** LegalEase – AI-Powered Legal Document Generator

---

## Test Approach

The backend was started with Uvicorn and the frontend with Streamlit, and every feature was tested through the browser at `http://localhost:8501` using a sample **Freelance Work Contract** between Jane Doe (Service Provider) and TechNova Inc. (Client), effective April 15, 2025.

## Functional Test Cases

| No. | Test | Steps | Expected Result |
|---|---|---|---|
| 1 | Application loads | Open `http://localhost:8501` | Logo, title and the four input fields are shown |
| 2 | Generate document | Enter document type, parties, terms and date; click **Generate Document** | Success message and a generated legal document in the preview card |
| 3 | Edit document | Click **Click to Edit Document** and change the text | Editable text area opens; changes are carried into the downloads |
| 4 | Download TXT | Click **Download as .TXT** | Plain-text file with the document content |
| 5 | Download DOCX | Click **Download as .DOCX** | Word file with logo on the front page, headings, terms table and footer on the last page |
| 6 | Download PDF | Click **Download as .PDF** | Branded PDF with logo and footer on all pages |
| 7 | Error handling | Stop the backend or use an invalid API key | A helpful error message is shown without crashing |

## Manual Testing Checklist

### Input and Generation
- [ ] All four input fields accept text; semicolons in terms create bullet points.
- [ ] Generate Document returns a structured document with multiple sections and clauses.

### Preview, Editing and Export
- [ ] Dark-mode HTML preview is scrollable and readable.
- [ ] Edited text appears in the .TXT, .DOCX and .PDF downloads.
- [ ] Layout shows the logo and footer; bullet points and the terms table are formatted cleanly.

### Errors
- [ ] A missing or invalid API key produces a handled error message.
