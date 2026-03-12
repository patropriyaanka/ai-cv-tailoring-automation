# 🤖 AI-Powered CV Tailoring Automation
> Paste a job description into a Google Sheet — get a tailored, ATS-optimised CV in your inbox in under 3 minutes. No code required.

---

![Made with Make.com](https://img.shields.io/badge/Made%20with-Make.com-6d4aff?style=for-the-badge&logo=data:image/png;base64,iVBORw0KGgo=)
![Powered by Gemini AI](https://img.shields.io/badge/Powered%20by-Gemini%20AI-4285F4?style=for-the-badge&logo=google&logoColor=white)
![No-Code](https://img.shields.io/badge/No--Code-✓-brightgreen?style=for-the-badge)
![Google Sheets Triggered](https://img.shields.io/badge/Triggered%20by-Google%20Sheets-34A853?style=for-the-badge&logo=googlesheets&logoColor=white)
![Status](https://img.shields.io/badge/Project%20Status-Active-success?style=for-the-badge)

---

## 📋 What This Does

This workflow automates the most time-consuming part of job searching — tailoring your CV to each job description. You paste a job description into a Google Sheet, and the automation handles everything: retrieving your master CV, sending it to Gemini AI with a structured prompt, generating a tailored and ATS-optimised version, creating a formatted Google Doc, and emailing the finished CV directly to you. The entire process runs without any manual intervention, reducing CV tailoring time from 45 minutes to under 3 minutes per application.

---

## 🏗️ Workflow Architecture

```
[Google Sheets — New Row Added with Job Description]
                        ↓
          [Make.com — Trigger Detected]
                        ↓
     [Google Drive — Retrieve Master CV Document]
                        ↓
  [Google Gemini AI — Generate Tailored, ATS-Optimised CV]
                        ↓
    [Google Docs — Create Formatted CV Document]
     

---

## 🛠️ Tech Stack

| Tool | Purpose | Free Tier Available |
|---|---|---|
| **Make.com** | Workflow automation — orchestrates all steps end-to-end | ✅ Yes (1,000 ops/month) |
| **Google Gemini AI** | LLM — generates the tailored CV from JD + master CV | ✅ Yes (via Google AI Studio) |
| **Google Sheets** | Trigger input — job seeker pastes JD to start workflow | ✅ Yes |
| **Google Drive** | Stores and retrieves the master CV document | ✅ Yes |
| **Google Docs** | Creates the formatted, tailored CV output and upload it in the drive| ✅ Yes |


---

## 🧠 Key AI Concepts Demonstrated

| Concept | How It Applies in This Project |
|---|---|
| **LLM Orchestration** | Make.com sequences the workflow — Gemini AI is called at the right step with the right inputs, and its output is routed to the next module automatically |
| **Prompt Engineering** | A structured system prompt instructs Gemini to analyse the JD, extract keywords, match them against the master CV, and output a tailored, ATS-optimised document in plain text format |
| **Spreadsheet-Triggered Automation** | Make.com watches the Google Sheet for new rows — when a JD is added, the entire downstream workflow fires automatically without any manual action |
| **API Integration Without Code** | Google Drive, Gemini AI, Google Docs, and Gmail are all connected via Make.com's native connectors — no coding required to pass data between services |
| **AI Output Quality Management** | The Gemini prompt includes explicit formatting rules and constraints — no Markdown asterisks, plain text only, structured section order — to ensure the output is clean and usable |
| **No-Code AI Tooling** | The entire solution is built and maintained without writing a single line of code, demonstrating that AI automation is accessible beyond traditional engineering roles |

---

## 📈 Business Impact

| Metric | Before Automation | After Automation |
|---|---|---|
| ⏱️ Time per CV tailored | 45 minutes | Under 3 minutes |
| 📄 CVs tailored per hour | 1–2 | 20+ |
| 🎯 ATS keyword alignment | Manual, inconsistent | Systematic, prompt-driven |
| 🔁 Human effort required | High — full rewrite each time | Low — paste JD, receive CV |
| 📬 Output delivery | Saved to the drive |

> **Net result:** A job seeker applying to 10 roles per week saves approximately 7 hours of manual CV tailoring work — time redirected to interview preparation and networking.

---

## 🚀 How to Use This

### Prerequisites
- A Make.com account (free tier is sufficient)
- A Google account (Sheets, Drive, Docs, Gmail)
- A Google AI Studio API key for Gemini (free at [aistudio.google.com](https://aistudio.google.com))

### Step-by-Step Setup

**Step 1 — Copy the Make.com Blueprint**
- Download the `cv_automation.json` file from the `/make-blueprint` folder in this repository
- Log in to Make.com → Scenarios → Create a new scenario
- Click the three dots (⋯) → Import Blueprint → upload the `.json` file

**Step 2 — Set Up Your Google Sheet**
- Create a new Google Sheet using the column structure in the [Google Sheet Setup](#-google-sheet-setup) section below
- In Make.com, open the Google Sheets trigger module and connect it to your sheet

**Step 3 — Connect Your Google Drive Master CV**
- Upload your master CV as a Google Doc to your Google Drive
- In Make.com, open the Google Drive module and select your master CV file by its file ID

**Step 4 — Add Your Gemini API Key**
- Go to [aistudio.google.com](https://aistudio.google.com) → Get API Key → Create API Key
- In Make.com, open the Google Gemini AI module → Add a new connection → paste your API key

**Step 5 — Activate and Test the Workflow**
- Click "Run once" in Make.com to test with a sample row in your Google Sheet
- Check your Gmail inbox for the tailored CV output
- Once confirmed working, toggle the scenario to "ON" for automatic triggering

---

## 📊 Google Sheet Setup

Create your Google Sheet with the following exact column headers in Row 1:

| Column | Header | Description |
|---|---|---|
| **A** | `Job Title` | The title of the role you are applying for |
| **B** | `Company Name` | The name of the hiring company |
| **C** | `Job Description` | Full job description text — paste the entire JD here |


> 💡 **Tip:** Leave Row 1 as headers. Add each new application as a new row from Row 2 onwards. The Make.com trigger watches for new rows and fires automatically.

<img width="1440" height="900" alt="Screenshot 2026-03-12 at 4 25 17 PM" src="https://github.com/user-attachments/assets/3eb6084e-3273-4425-ba3c-d20db901785d" />

---

## 💡 What I Learned

- **LLM prompt engineering is everything** — the quality of Gemini's CV output changed dramatically based on how the prompt was structured. Adding explicit constraints (no Markdown, plain text, section order, word limits) was as important as the core instruction itself.

- **Spreadsheet-triggered automation is more powerful than form-based triggers** — using Google Sheets as the input layer means the workflow also writes back to the sheet (Column E status update), creating a two-way data flow that a simple form cannot achieve.

- **API integration without code is entirely achievable** — connecting four Google services plus an AI model through Make.com's visual interface required zero coding, but demanded the same systems thinking as a traditional integration project: understanding inputs, outputs, data formats, and error states.

- **AI output quality management is a distinct skill** — getting a clean, usable CV out of an LLM is not just about writing a good prompt. It involves testing edge cases, handling formatting inconsistencies, and iterating on constraints — skills directly transferable to enterprise AI product delivery.

---

## 🔮 Future Enhancements

- **Add an automatic ATS scoring module** — after CV generation, send both the CV and JD to a second AI call that scores keyword match percentage and flags gaps before the CV is emailed
- **Build a Lovable front-end dashboard** — replace the Google Sheet input with a clean web interface built in Lovable, giving a full application tracker with status, ATS score, and CV preview in one place

---

## 👩‍💻 About the Author

**Priyanka Patro** — Technical AI Business Analyst with hands-on experience in GenAI enablement, LLM orchestration, workflow automation, and no-code AI tooling. Currently working at Saga PLC, where AI-enabled solutions have improved delivery efficiency by 20–30%.

This project was built as part of a self-directed AI learning portfolio — demonstrating that business analysts can design, build, and deploy applied AI solutions without an engineering background.

🔗 [Connect on LinkedIn](https://linkedin.com/in/priyankapatro)

---

## 📄 Licence

This project is licensed under the MIT Licence — feel free to fork, adapt, and build on it for your own job search.

---

*Built with curiosity, Make.com, and a lot of job applications* 🚀
