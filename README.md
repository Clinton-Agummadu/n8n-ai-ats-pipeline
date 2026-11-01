# Autonomous AI ATS & Recruitment Pipeline 🚀

An end-to-end, production-grade automated recruitment pipeline built using **n8n**, **Google Gemini AI**, **Google Sheets**, and **Zoho Mail SMTP** on a custom domain (`odogwu.site`). This system eliminates manual resume screening bottlenecks by parsing candidate submissions, evaluating technical competence against a defined 50-point benchmark, logging data instantly, and triggering conditional HTML email notifications.

---

## 🛠️ Tech Stack & Architecture
* **Workflow Automation:** n8n (Self-hosted)
* **AI Engine:** Google Gemini (Structured LLM parsing and resume evaluation)
* **Database & Logging:** Google Sheets
* **Email Infrastructure:** Zoho Mail via SMTP (`automationbot@odogwu.site`)
* **Frontend Trigger:** Web Form Submission / Netlify

---

## 🔄 Execution Flow
1. **Submission:** Candidates submit their application details and resume file.
2. **AI Evaluation:** Gemini AI parses the document, extracts core technical strengths, and calculates an overall score out of 100.
3. **Threshold Logic & Data Logging:** A custom JavaScript node validates the score against a **50-point passing threshold**:
   * **Score $\ge$ 50:** Categorized as *Proceed to Interview*.
   * **Score $<$ 50:** Categorized as *Reject*.
   All applicant data is simultaneously appended to a live Google Sheets tracker.
4. **Conditional Email Dispatch:** The workflow dynamically compiles a responsive HTML email via Zoho SMTP:
   * **Passing Candidates:** Receive an approval notice with their score, identified strengths, and a direct call-to-action button linking to the recruiter's professional LinkedIn profile for scheduling.
   * **Rejected Candidates:** Receive a polite, professional closure notice without interview scheduling links.

---

## 📂 Project Structure
```text
├── workflow.json          # Main n8n exported workflow template
├── email-template.html    # Responsive HTML template with inline conditional logic
└── README.md              # Project documentation
