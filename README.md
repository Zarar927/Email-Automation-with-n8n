# 📧 Email Automation with n8n — AI Job & Internship Email Assistant

An intelligent **email automation workflow built with n8n** that automatically monitors Gmail, identifies **job and internship opportunities using AI**, analyzes the email content with a text classifier, and uses **OpenAI to generate a professional reply**.

Instead of manually reading every email, deciding whether it is related to a job or internship, and writing a response, this workflow automates the entire process up to **creating a Gmail draft**.

> **Gmail → AI Classification → Job/Internship Detection → AI Reply Generation → Gmail Draft**

---

## 🚀 Project Overview

Searching for jobs and internships often means receiving a large number of emails every day. Important opportunities can easily get buried among newsletters, advertisements, notifications, and unrelated messages.

This project solves that problem using **n8n + Gmail + Groq AI + Text Classification + OpenAI**.

The workflow:

1. 📥 Reads incoming emails from Gmail.
2. 📄 Extracts the email subject, sender, and body.
3. 🤖 Sends the email content to **Groq AI** for fast AI-powered analysis.
4. 🏷️ Uses a **text classifier** to determine whether the email is related to:

   * Job
   * Internship
   * Other/Irrelevant
5. 🔎 Identifies relevant job/internship emails.
6. ✍️ Sends the relevant email to **OpenAI** to generate a professional reply.
7. 📝 Creates a **Gmail draft** containing the generated response.
8. 👤 The user can review and edit the draft before sending it.

---

# 🎯 Main Objective

The main objective of this project is to automate the repetitive process of handling career-related emails while keeping the final decision under the user's control.

### Without automation

```text
Receive Email
     ↓
Open Email
     ↓
Read Email
     ↓
Understand Email
     ↓
Decide if Job/Internship
     ↓
Write Reply
     ↓
Create Draft
```

### With this automation

```text
             ┌──────────────┐
             │    Gmail     │
             └──────┬───────┘
                    ↓
             ┌──────────────┐
             │  Read Email  │
             └──────┬───────┘
                    ↓
             ┌──────────────┐
             │   Groq AI    │
             │  Analysis    │
             └──────┬───────┘
                    ↓
             ┌──────────────┐
             │Text Classifier│
             └──────┬───────┘
                    ↓
          ┌─────────┴─────────┐
          ↓                   ↓
       Relevant           Irrelevant
     Job/Internship           │
          ↓                   ↓
   ┌──────────────┐         Stop
   │   OpenAI     │
   │ Reply Writer │
   └──────┬───────┘
          ↓
   ┌──────────────┐
   │ Gmail Draft  │
   └──────────────┘
```

---

# ✨ Features

## 📩 Gmail Integration

The workflow connects directly with Gmail to process incoming emails.

It can retrieve information such as:

* Sender
* Recipient
* Subject
* Email body
* Email ID
* Thread information
* Timestamp
* Email metadata

---

## 🤖 Groq AI Email Analysis

The project uses **Groq AI** for fast analysis of incoming email content.

Groq can analyze the email and identify important information such as:

* Email intent
* Job opportunity
* Internship opportunity
* Recruiter communication
* Interview invitation
* Application update
* Rejection
* Unrelated email

The AI analysis can also extract useful information from the email content.

Example:

```text
Position: AI/ML Intern
Company: ABC Technologies
Location: Lahore
Employment Type: Internship
Experience Required: 0–1 year
```

---

# 🏷️ Text Classification

After receiving the email, the workflow determines which category the email belongs to.

### Example categories

| Category             | Description                              |
| -------------------- | ---------------------------------------- |
| `JOB`                | Full-time or part-time job opportunity   |
| `INTERNSHIP`         | Internship or trainee opportunity        |
| `INTERVIEW`          | Interview invitation or scheduling email |
| `APPLICATION_UPDATE` | Update regarding an existing application |
| `REJECTION`          | Job/internship rejection                 |
| `OTHER`              | Unrelated or non-career email            |

The classifier prevents irrelevant emails from reaching the reply-generation stage.

---

# 🧠 AI Processing Pipeline

The project uses multiple AI components for different responsibilities.

### Groq AI

Used primarily for:

* Fast email analysis
* Understanding email context
* Extracting career-related information
* Supporting classification

### Text Classifier

Used to categorize the email.

```text
Email
 ↓
Text Processing
 ↓
Classification
 ↓
Job / Internship / Other
```

### OpenAI

Used for generating the final professional response.

```text
Relevant Email
      ↓
OpenAI
      ↓
Professional Reply
      ↓
Gmail Draft
```

Using separate AI components allows the workflow to keep **classification and response generation as separate stages**.

---

# ✍️ Automatic Reply Generation

For relevant job and internship emails, OpenAI generates a professional response based on the email content.

The generated response can include:

* Professional greeting
* Appreciation for contacting the candidate
* Confirmation of interest
* Relevant skills
* Relevant experience
* Availability
* Request for next steps
* Professional closing

### Example

Incoming email:

```text
Subject: AI/ML Internship Opportunity

Hello,

We are looking for an AI/ML Intern to join our team.
The internship is based in Lahore.

If interested, please reply to this email.
```

Generated draft:

```text
Dear Hiring Team,

Thank you for reaching out regarding the AI/ML Internship opportunity.

I am very interested in this position and would be glad to be considered for the role. My background includes Artificial Intelligence, Machine Learning, Deep Learning, Python, and related AI technologies.

I would appreciate the opportunity to discuss the position and learn more about the next steps in the recruitment process.

Please let me know if you require any additional information or documents from my side.

Best regards,
Zarar Ahmed
```

The message is created as a **draft**, rather than being sent automatically.

---

# 📝 Why Create a Draft Instead of Automatically Sending?

This project intentionally creates a **Gmail draft** instead of sending the response immediately.

This provides a human-in-the-loop workflow.

```text
AI generates response
        ↓
Gmail Draft
        ↓
User reviews response
        ↓
User edits if necessary
        ↓
User sends email
```

This approach helps prevent:

* Incorrect responses
* Unwanted emails
* Incorrect job information
* Incorrect personalization
* Accidental communication

The user always has the final control over the message.

---

# 🛠️ Technologies Used

| Technology               | Purpose                             |
| ------------------------ | ----------------------------------- |
| **n8n**                  | Workflow automation                 |
| **Gmail**                | Email integration                   |
| **Groq AI**              | Fast AI-powered email analysis      |
| **Text Classifier**      | Job/internship email classification |
| **OpenAI**               | Professional reply generation       |
| **LLM Prompting**        | Structured AI processing            |
| **Gmail Draft API/Node** | Creating email drafts               |

---

# 🏗️ System Architecture

```text
                         ┌─────────────────┐
                         │      Gmail      │
                         │ Incoming Emails │
                         └────────┬────────┘
                                  │
                                  ▼
                         ┌─────────────────┐
                         │   n8n Trigger   │
                         └────────┬────────┘
                                  │
                                  ▼
                         ┌─────────────────┐
                         │ Extract Email   │
                         │ Data & Content  │
                         └────────┬────────┘
                                  │
                                  ▼
                         ┌─────────────────┐
                         │    Groq AI      │
                         │ Email Analysis  │
                         └────────┬────────┘
                                  │
                                  ▼
                         ┌─────────────────┐
                         │ Text Classifier │
                         └────────┬────────┘
                                  │
                       ┌──────────┴──────────┐
                       │                     │
                       ▼                     ▼
                  Job/Internship          Other
                       │                     │
                       ▼                     ▼
                ┌──────────────┐           Stop
                │    OpenAI    │
                │ Reply Writer │
                └──────┬───────┘
                       │
                       ▼
                ┌──────────────┐
                │ Gmail Draft  │
                └──────────────┘
```

---

# 🔄 Complete Workflow

## Step 1 — Gmail Trigger

The workflow starts when a new email is received in Gmail.

```text
Gmail
  ↓
New Email
```

The workflow retrieves the relevant email information.

---

## Step 2 — Extract Email Information

The workflow extracts:

```text
From
To
Subject
Body
Email ID
Thread ID
Date
```

The email body becomes the primary input for AI processing.

---

## Step 3 — AI Email Analysis

The email is sent to Groq AI.

The model analyzes the content and determines what type of email it is.

Example:

```json
{
  "category": "INTERNSHIP",
  "relevant": true,
  "position": "AI/ML Intern",
  "company": "ABC Technologies",
  "location": "Lahore"
}
```

Structured output makes it easier for n8n to process the result.

---

# Step 4 — Classification

The workflow checks the classifier result.

Example:

```text
IF category == JOB
        ↓
Continue

IF category == INTERNSHIP
        ↓
Continue

IF category == OTHER
        ↓
Stop
```

Only relevant career emails proceed to the next stage.

---

# Step 5 — Generate Reply

The relevant email is sent to OpenAI along with instructions for generating the response.

The AI considers:

* Original email
* Subject
* Sender
* Job/internship information
* Candidate profile
* Skills
* Experience
* Availability
* Professional tone

---

# Step 6 — Create Gmail Draft

The generated response is sent back to Gmail.

Instead of sending it directly:

```text
Create Draft
```

The final email becomes available in the Gmail Drafts folder.

---

# 📂 Suggested Project Structure

```text
Email-Automation-with-n8n/
│
├── README.md
│
├── workflow/
│   └── email-automation.json
│
├── prompts/
│   ├── classifier-prompt.txt
│   └── reply-generator-prompt.txt
│
├── docs/
│   └── workflow-diagram.png
│
└── .gitignore
```

> If your n8n workflow is stored under a different filename, update the structure above accordingly.

---

# ⚙️ Prerequisites

Before running the project, make sure you have:

* n8n installed or access to n8n Cloud
* Gmail account
* Gmail OAuth credentials
* Groq API key
* OpenAI API key
* Internet connection
* Basic knowledge of n8n workflows

---

# 🔐 Environment Variables

API keys and credentials should **never be hard-coded** into the workflow or committed to GitHub.

Example:

```env
GROQ_API_KEY=your_groq_api_key
OPENAI_API_KEY=your_openai_api_key
```

Use n8n's credential management system whenever possible.

### ⚠️ Important

Never upload:

```text
.env
API keys
OAuth tokens
Client secrets
Passwords
Private credentials
```

to a public GitHub repository.

---

# 🔑 Gmail Authentication

The Gmail integration requires OAuth authentication.

Typical setup:

```text
Google Cloud
     ↓
Create Project
     ↓
Enable Gmail API
     ↓
Configure OAuth Consent
     ↓
Create OAuth Credentials
     ↓
Connect Gmail with n8n
```

Once authentication is configured, n8n can access the authorized Gmail account according to the granted permissions.

---

# 🧩 n8n Workflow Nodes

A typical implementation can contain nodes similar to:

```text
Gmail Trigger
     ↓
Get Email
     ↓
Extract / Clean Email
     ↓
Groq AI
     ↓
Text Classifier
     ↓
IF / Switch
     ↓
OpenAI
     ↓
Gmail - Create Draft
```

The exact node names may differ depending on the n8n version and the implementation.

---

# 🧹 Email Text Preprocessing

Before sending the email to an AI model, unnecessary content can be removed.

Possible preprocessing includes:

* Removing excessive HTML
* Removing email signatures
* Removing tracking text
* Cleaning whitespace
* Extracting plain text
* Removing repeated quoted messages

Example:

```text
Raw Email
   ↓
HTML Cleaning
   ↓
Text Extraction
   ↓
Whitespace Cleanup
   ↓
AI Processing
```

This can improve the quality and consistency of classification.

---

# 🧠 Classification Logic

A simple classification strategy can be:

```text
                    Incoming Email
                           │
                           ▼
                     AI Analysis
                           │
                           ▼
                    Text Classifier
                           │
          ┌────────────────┼────────────────┐
          │                │                │
          ▼                ▼                ▼
        JOB          INTERNSHIP           OTHER
          │                │                │
          └────────┬───────┘                │
                   ▼                       STOP
              OpenAI Reply
                   │
                   ▼
             Gmail Draft
```

---

# 📝 Example Classifier Prompt

The classifier can be instructed to return structured information.

Example:

```text
You are an email classification assistant.

Analyze the following email and determine whether it is related to:

1. JOB
2. INTERNSHIP
3. INTERVIEW
4. APPLICATION_UPDATE
5. REJECTION
6. OTHER

Return a structured response containing:

- category
- relevant
- position
- company
- location
- reason

Do not invent information that is not present in the email.

Email:
{{email_body}}
```

---

# ✍️ Example Reply Generation Prompt

Example OpenAI prompt:

```text
You are a professional career email assistant.

Generate a concise and professional reply to the email below.

Requirements:

- Maintain a professional tone.
- Show interest only when appropriate.
- Do not invent qualifications, experience, companies, dates, or other facts.
- Use information provided in the candidate profile.
- Keep the response concise.
- Do not mention that AI generated the response.
- Do not send the email; generate only the draft content.
- Address the sender professionally.
- End with the candidate's name.

Original Email:
{{email_body}}

Candidate Profile:
{{candidate_profile}}
```

---

# 👤 Candidate Profile

The reply-generation stage can be personalized using a candidate profile.

Example:

```text
Name: Zarar Ahmed

Field:
Artificial Intelligence

Skills:
Python
Machine Learning
Deep Learning
Computer Vision
NLP
FastAPI
Django
TensorFlow
PyTorch
LangChain
Generative AI
RAG

Experience:
AI/ML Internship
Teaching Experience
Software/AI Projects

Career Interests:
AI Engineer
Machine Learning Engineer
Computer Vision
Healthcare AI
Generative AI
```

You should replace this information with the actual profile you want the workflow to use.

---

# 📊 Example Workflow Input

```text
From:
hr@company.com

Subject:
AI Engineer Intern – Lahore

Body:

Hello,

We are hiring an AI Engineer Intern for our Lahore office.

Candidates with knowledge of Python, Machine Learning and Deep Learning
are encouraged to apply.

If interested, please reply to this email.
```

---

# 📊 Example AI Classification

```json
{
  "category": "INTERNSHIP",
  "relevant": true,
  "position": "AI Engineer Intern",
  "company": "Unknown",
  "location": "Lahore"
}
```

---

# 📧 Example Generated Draft

```text
Dear Hiring Team,

Thank you for reaching out regarding the AI Engineer Intern opportunity.

I am interested in the position and would be glad to be considered. My background includes Artificial Intelligence, Python, Machine Learning, Deep Learning, and related AI technologies.

I would appreciate the opportunity to discuss the role and learn more about the next steps in the recruitment process.

Please let me know if you require any additional information or documents.

Best regards,
Zarar Ahmed
```

The message is then stored in Gmail as a draft.

---

# 🛡️ Safety & Reliability

Because the workflow processes real emails and generates responses, several safeguards are recommended.

## Human Approval

The system should create drafts rather than automatically sending emails.

```text
AI
 ↓
Draft
 ↓
Human Review
 ↓
Send
```

---

## No Hallucinated Information

The reply-generation prompt should explicitly instruct the AI not to invent:

* Job experience
* Education
* Certifications
* Skills
* Company names
* Dates
* Salary expectations
* Availability
* Personal information

---

## Structured AI Output

Where possible, use structured JSON output.

Example:

```json
{
  "category": "JOB",
  "relevant": true,
  "confidence": 0.94,
  "position": "AI Engineer",
  "company": "ABC Technologies"
}
```

Structured data makes downstream n8n logic easier to maintain.

---

# 🔒 Security Considerations

This workflow processes potentially sensitive email information.

Recommended practices:

### 1. Protect API Keys

Never commit API keys to GitHub.

### 2. Use OAuth

Use Gmail OAuth rather than storing Gmail passwords.

### 3. Limit Permissions

Grant only the Gmail permissions required by the workflow.

### 4. Avoid Unnecessary Data

Only send the email information required for AI processing.

### 5. Review Generated Emails

Always review AI-generated drafts before sending.

### 6. Protect Candidate Information

Avoid placing sensitive personal information into prompts unless it is necessary.

---

# ⚡ Performance

The workflow separates the AI tasks based on their purpose.

```text
Groq
 ↓
Fast Analysis / Classification
 ↓
OpenAI
 ↓
Higher-level Response Generation
```

This separation can make the workflow easier to maintain and modify.

---

# 💰 Cost Considerations

The total cost depends on:

* Number of emails processed
* Groq model used
* OpenAI model used
* Token usage
* n8n hosting method
* Gmail/API usage

To reduce unnecessary AI usage:

```text
Gmail
 ↓
Basic filtering
 ↓
AI classification
 ↓
Only relevant emails
 ↓
OpenAI reply generation
```

This prevents every email from reaching the reply-generation stage.

---

# 🔧 Possible Gmail Filters

You can optionally filter emails before AI processing.

Examples:

```text
job
jobs
intern
internship
career
hiring
recruitment
interview
application
```

However, keyword filtering should be treated as an optimization rather than the only classification mechanism because relevant emails may use different wording.

---

# 🧪 Testing

Before deploying the workflow for real email processing, test it using different email categories.

### Test Case 1 — Job

```text
Subject:
AI Engineer Position

Expected:
JOB
```

### Test Case 2 — Internship

```text
Subject:
Machine Learning Internship

Expected:
INTERNSHIP
```

### Test Case 3 — Interview

```text
Subject:
Interview Invitation – AI Intern

Expected:
INTERVIEW
```

### Test Case 4 — Newsletter

```text
Subject:
Weekly Technology Newsletter

Expected:
OTHER
```

### Test Case 5 — Marketing

```text
Subject:
50% Discount on Software

Expected:
OTHER
```

### Test Case 6 — Application Update

```text
Subject:
Update Regarding Your Application

Expected:
APPLICATION_UPDATE
```

---

# 🐛 Troubleshooting

## Gmail authentication fails

Check:

* Google Cloud project
* Gmail API
* OAuth configuration
* Redirect URI
* n8n Gmail credentials

---

## AI classification is incorrect

Improve the classifier prompt and provide more examples.

You can also introduce:

```text
confidence threshold
```

For example:

```text
confidence < threshold
        ↓
Do not generate reply
```

---

## Generated reply contains incorrect information

Strengthen the prompt:

```text
Do not invent information.
Use only information provided in the candidate profile
and original email.
```

---

## Draft is not created

Check:

* Gmail credentials
* Gmail permissions
* Recipient email
* Subject field
* Generated response
* n8n execution logs

---

# 📈 Future Improvements

This project can be extended into a complete AI-powered career assistant.

## 🔹 Automatic Job Information Extraction

Extract:

```text
Company
Position
Location
Salary
Experience
Skills
Deadline
Employment Type
Remote/Onsite
```

---

## 🔹 Job Database

Store classified opportunities in:

* PostgreSQL
* MySQL
* MongoDB
* Supabase
* Google Sheets
* Airtable

Example:

```text
Company | Position | Location | Type | Date | Status
```

---

## 🔹 Automatic Labeling

Automatically apply Gmail labels:

```text
AI/JOBS
AI/INTERNSHIPS
AI/INTERVIEWS
AI/APPLICATION-UPDATES
AI/REJECTIONS
```

---

## 🔹 Priority Scoring

The system could identify emails requiring faster attention based on configurable rules such as:

```text
Interview Invitation → High Priority
Application Deadline → High Priority
Job Opportunity → Normal Priority
Newsletter → Low Priority
```

---

## 🔹 Resume Matching

The workflow could compare the job description with the candidate's resume.

```text
Job Description
       +
Candidate Resume
       ↓
AI Matching
       ↓
Relevant Skills
       ↓
Missing Skills
```

---

## 🔹 Automated Application Tracking

Create a complete application tracker:

```text
Company
Position
Application Date
Status
Interview Date
Response
Follow-up Date
```

---

## 🔹 Follow-up Automation

A future version could remind the user when a recruiter has not responded after a configurable period.

Example:

```text
Application
    ↓
Wait
    ↓
No Response
    ↓
Create Follow-up Draft
```

---

# 🔮 Future Architecture

```text
                         Gmail
                           │
                           ▼
                    Email Detection
                           │
                           ▼
                    Text Processing
                           │
                           ▼
                       Groq AI
                           │
                           ▼
                    Classification
                           │
              ┌────────────┼────────────┐
              │            │            │
             JOB       INTERNSHIP     OTHER
              │            │            │
              └─────┬──────┘            │
                    │                  Stop
                    ▼
             Resume Matching
                    │
                    ▼
              Opportunity DB
                    │
                    ▼
                 OpenAI
                    │
                    ▼
              Reply Generation
                    │
                    ▼
              Gmail Draft
                    │
                    ▼
              Human Review
                    │
                    ▼
                  Send
```

---

# 📦 Installation & Setup

## 1. Clone the Repository

```bash
git clone https://github.com/your-username/Email-Automation-with-n8n.git
```

Navigate into the project:

```bash
cd Email-Automation-with-n8n
```

---

## 2. Import the n8n Workflow

Open your n8n instance.

Go to:

```text
Workflows
    ↓
Import from File
```

Select the workflow JSON file:

```text
workflow/email-automation.json
```

---

## 3. Configure Gmail

Connect your Gmail account through n8n credentials.

---

## 4. Configure Groq

Add your Groq API credentials.

---

## 5. Configure OpenAI

Add your OpenAI credentials.

---

## 6. Configure Candidate Information

Update the candidate profile used by the reply-generation prompt.

---

## 7. Test the Workflow

Send or receive test emails and verify:

```text
Gmail
 ↓
Classification
 ↓
AI Processing
 ↓
Draft Creation
```

---

## 8. Activate the Workflow

After successful testing:

```text
Workflow
   ↓
Activate
```

The workflow can now process incoming emails according to the configured trigger and conditions.

---

# 📋 Example Use Cases

This automation can be useful for:

* AI/ML job seekers
* Software developers
* Students
* Fresh graduates
* Internship applicants
* Freelancers
* Recruiters
* Career consultants
* HR teams

---

# 💡 Why This Project?

Modern job seekers can receive a large number of emails from different sources.

Manually processing every email is repetitive:

```text
Read → Understand → Categorize → Reply → Draft
```

This project transforms that process into:

```text
Receive → Analyze → Classify → Generate → Draft
```

The user remains responsible for reviewing and sending the final response.

---

# 🧠 Key Concepts Demonstrated

This project demonstrates practical experience with:

* Workflow automation
* n8n
* Gmail API integration
* OAuth authentication
* LLM integration
* Groq AI
* OpenAI
* Text classification
* Prompt engineering
* Structured AI output
* Email parsing
* Conditional workflow logic
* Human-in-the-loop AI
* Automated draft generation
* API-based integrations
* AI-assisted productivity

---

# 🏆 Project Highlights

### 🔹 End-to-End Automation

The workflow connects multiple services into one automated pipeline.

### 🔹 Multi-Model AI Architecture

Different AI services are used for different tasks.

### 🔹 Human-in-the-Loop

The AI prepares the response while the user retains final control.

### 🔹 Practical Real-World Use Case

The project addresses a common problem for students, graduates, and job seekers.

### 🔹 Extensible Architecture

The workflow can later be expanded into a complete career-management platform.

---

# 📸 Workflow Preview

Add screenshots of your n8n workflow here.

Example:

```text
docs/
└── workflow-diagram.png
```

Then display it in the README:

```markdown
![n8n Email Automation Workflow](docs/workflow-diagram.png)
```

---

# 🎥 Demo

If you have a video demonstration, add it here:

```markdown
## Demo

[Watch the full workflow demonstration](YOUR_VIDEO_LINK)
```

The demo should ideally show:

```text
1. Incoming Gmail email
2. n8n workflow execution
3. Groq classification
4. Text classifier result
5. OpenAI response generation
6. Gmail draft creation
```

---

# 📌 Important Notes

* The workflow is designed to **create drafts**, not automatically send emails.
* AI-generated responses should be reviewed before sending.
* Model names and n8n node configurations may change over time.
* API usage may incur costs depending on the providers and plans used.
* Never expose API keys or OAuth credentials in the repository.
* Classification accuracy depends on email quality, prompts, model behavior, and workflow configuration.

---

# 🤝 Contributing

Contributions are welcome.

To contribute:

```bash
git fork
```

Create a feature branch:

```bash
git checkout -b feature/new-feature
```

Make your changes and commit:

```bash
git add .
git commit -m "Add new feature"
```

Push your branch:

```bash
git push origin feature/new-feature
```

Then open a Pull Request.

---

# 📄 License

This project is available under the license specified in the repository.

If no license has been added yet, add an appropriate license file before distributing the project publicly.

---

# 👨‍💻 Author

**Zarar Ahmed**

Artificial Intelligence Graduate | AI/ML Developer

### Areas of Interest

* Artificial Intelligence
* Machine Learning
* Deep Learning
* Generative AI
* Natural Language Processing
* Computer Vision
* Agentic AI
* Automation
* RAG Systems

### Portfolio

[Portfolio](https://zarar-portfolio.netlify.app/)

---

# ⭐ Support

If you find this project useful:

* ⭐ Star the repository
* 🍴 Fork the project
* 🐛 Report issues
* 💡 Suggest improvements
* 🤝 Contribute to the project

---

# 🔗 Technology Stack

```text
┌───────────────────────────────────────────┐
│                  n8n                      │
│          Workflow Automation              │
└───────────────────┬───────────────────────┘
                    │
        ┌───────────┼───────────┐
        │           │           │
        ▼           ▼           ▼
     Gmail        Groq       OpenAI
      API          AI          API
        │           │           │
        │           ▼           │
        │      Classification   │
        │           │           │
        └───────────┼───────────┘
                    │
                    ▼
              Gmail Draft
```

---

# 🚀 Final Workflow Summary

```text
                 📧 NEW EMAIL
                      │
                      ▼
                📥 GMAIL
                      │
                      ▼
              🔍 EXTRACT EMAIL
                      │
                      ▼
                 🤖 GROQ AI
                      │
                      ▼
             🏷️ TEXT CLASSIFIER
                      │
             ┌────────┴────────┐
             │                 │
             ▼                 ▼
       JOB / INTERNSHIP       OTHER
             │                 │
             ▼                 ▼
        ✍️ OPENAI            ⛔ STOP
             │
             ▼
       📝 GENERATE REPLY
             │
             ▼
        📧 GMAIL DRAFT
             │
             ▼
       👤 HUMAN REVIEW
             │
             ▼
             🚀 SEND
```

## ⭐ The Goal

> **Automate the repetitive work, use AI where it adds value, and keep the final communication under human control.**

This project demonstrates how **n8n workflow automation, Gmail integration, Groq AI, text classification, and OpenAI** can be combined to build a practical AI-powered email assistant for job and internship opportunities.
