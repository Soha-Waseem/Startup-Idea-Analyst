#  Startup Idea Analyst

### AI-powered startup validation assistant built with n8n + Google Gemini

##  Overview

**Startup Idea Analyst** is an AI-powered conversational advisor designed to help founders think critically about their startup and project ideas.

Instead of simply answering whether an idea is "good" or "bad", the agent breaks an idea down into **seven practical business dimensions** and provides constructive recommendations for moving toward validation and an MVP.

The workflow is built in **n8n**, with **Google Gemini 3.1 Flash Lite** powering the AI Agent and **Simple Memory** maintaining conversational context.

---

##  Why I Built This

Coming up with a startup idea is easy.

Knowing **whether the idea solves a real problem, who actually needs it, how it could make money, and what should be built first** is much harder.

I built Startup Idea Analyst to create a structured thinking partner for founders.

The goal is not to replace market research or founder judgment. Instead, it helps turn an unstructured idea into a clearer set of questions:

> **What problem are we solving?**

> **Who experiences this problem?**

> **What makes the solution valuable?**

> **What could prevent it from working?**

> **How could it generate revenue?**

> **What is the smallest MVP worth testing?**

This project also explores how **AI agents and workflow automation can be combined to create practical decision-support tools**, rather than generic chatbots.

---

##  What It Does

A founder can simply describe an idea conversationally.

The agent then evaluates it across:

| #  | Dimension           | What It Evaluates                                     |
| -- | ------------------- | ----------------------------------------------------- |
| 01 |  **Problem**      | The problem being solved and its urgency              |
| 02 |  **Audience**     | Target users and potential beachhead segment          |
| 03 |  **Strengths**    | Timing, insight, simplicity, traction, defensibility  |
| 04 |  **Weaknesses**   | Risks, gaps, differentiation, acquisition, complexity |
| 05 |  **Competitors**  | Direct, indirect, and alternative solutions           |
| 06 |  **Monetization** | Potential revenue models and pricing logic            |
| 07 |  **MVP**         | Smallest version needed to validate the idea          |

The workflow also ends with an **overall verdict** identifying the strongest aspect of the idea and the most important thing to validate or refine next.

---

#  AI Agent

The AI Agent uses a carefully defined system prompt that locks its scope to startup/project idea analysis.

### Scope

The agent focuses exclusively on:

```text
Problem
Audience
Strengths
Risks
Competitors
Monetization
MVP
```

If a user asks for something unrelated, the agent redirects the conversation back toward startup or project idea evaluation.

### Response Philosophy

The agent is designed to be:

*  **Supportive**
*  **Focused**
*  **Analytical**
*  **Honest**
*  **Action-oriented**
*  **Non-hype driven**

It is also instructed not to fabricate statistics, market sizes, or uncertain competitor names.

---

#  Workflow Architecture

The complete workflow follows a simple but effective architecture:

```text
                    ┌─────────────────────┐
                    │       Founder       │
                    │    Startup Idea     │
                    └──────────┬──────────┘
                               │
                               ▼
                 ┌──────────────────────────┐
                 │   Chat Message Trigger   │
                 │          n8n             │
                 └────────────┬─────────────┘
                              │
                              ▼
                 ┌──────────────────────────┐
                 │        AI Agent          │
                 │  Startup Idea Analyst    │
                 └───────────┬──────────────┘
                             │
                 ┌───────────┴───────────┐
                 │                       │
                 ▼                       ▼
       ┌──────────────────┐    ┌──────────────────┐
       │  Gemini 3.1      │    │  Simple Memory   │
       │  Flash Lite      │    │                  │
       │                  │    │ Conversation     │
       │ AI Reasoning     │    │ Context          │
       └──────────────────┘    └──────────────────┘
                             │
                             ▼
                 ┌──────────────────────────┐
                 │ Structured Startup       │
                 │ Analysis                 │
                 └──────────────────────────┘
```

The exported workflow contains the Chat Trigger, AI Agent, Gemini Chat Model, and Simple Memory nodes with their corresponding connections.

---

#  Screenshots

###  AI Agent in Action
<img width="465" height="299" alt="1" src="https://github.com/user-attachments/assets/3c230227-d59a-4343-a911-c8ae2c3c46b1" />

###  n8n Workflow
<img width="905" height="385" alt="0" src="https://github.com/user-attachments/assets/5b8d24a6-1b76-40e6-965f-e0fa5369b6ab" />

###  Startup Analysis Output
<img width="334" height="205" alt="6" src="https://github.com/user-attachments/assets/436e33b4-d73b-4ed8-ac66-53d9365711a4" />

---

#  Demo

### Example Input

```text
I want to build an AI platform that helps university
students find internships based on their skills.
```

### The agent evaluates:

```text
 Problem Being Solved
 Target Audience
 Strengths
 Weaknesses
 Competitors
 Monetization Ideas
 MVP Suggestions
```

### Example Output Structure

```text
## 1. Problem Being Solved

...

## 2. Target Audience

...

## 3. Strengths

...

## 4. Weaknesses

...

## 5. Competitors

...

## 6. Monetization Ideas

...

## 7. MVP Suggestions

...

## Overall Verdict

...
```

---

# 🛠️ Tech Stack

| Technology                | Role                        |
| ------------------------- | --------------------------- |
| **n8n**                   | Workflow automation         |
| **n8n AI Agent**          | Agent orchestration         |
| **Google Gemini**         | Large language model        |
| **Gemini 3.1 Flash Lite** | AI reasoning and generation |
| **Simple Memory**         | Conversational context      |

The workflow specifically configures `models/gemini-3.1-flash-lite` for the Gemini Chat Model.

---

# ⚙️ How It Works

### 01 — User sends an idea

The n8n Chat Trigger receives the founder's message.

### 02 — AI Agent processes the idea

The message is passed to the Startup Idea Analyst agent.

### 03 — Gemini generates the analysis

Google Gemini 3.1 Flash Lite interprets the idea according to the agent's structured evaluation framework.

### 04 — Memory maintains context

Simple Memory allows the agent to maintain conversational context while discussing the idea.

### 05 — Founder receives actionable feedback

The response is organized into seven sections and ends with an overall validation recommendation.

---

# 📂 Repository Structure

```text
startup-idea-analyst/
│
├── Startup Idea Analyst.json
├── README.md
│
└── screenshots/
    ├── startup-idea-demo.png
    ├── n8n-workflow.png
    └── startup-analysis.png
```

---

#  Getting Started

## Prerequisites

You'll need:

* [n8n](https://n8n.io/)
* Google Gemini API credentials
* The workflow JSON file from this repository

## Import the Workflow

1. Open your n8n instance.
2. Create or open your workspace.
3. Select **Import from File**.
4. Import:

```text
Startup Idea Analyst.json
```

5. Configure your Google Gemini credentials.
6. Save the workflow.
7. Activate/test the workflow.
8. Open the chat interface and submit a startup idea.

---

#  Credentials

The exported workflow requires Google Gemini credentials to run.

**Never commit your API keys or credentials to GitHub.**

Use n8n's credential management system and keep sensitive credentials outside the repository.

---

#  Use Cases

Startup Idea Analyst can be useful for:

*  Startup founders
*  Hackathon participants
*  Students developing projects
*  Indie hackers
*  Early-stage product teams
*  Entrepreneurs exploring business ideas
*  Entrepreneurship programs

---

#  Future Improvements

Potential next iterations could include:

*  Automated web-based competitor research
*  Market research integration
*  Startup financial projections
*  Market-size analysis
*  Customer persona generation
*  Business Model Canvas generation
*  Automated validation experiment suggestions
*  Startup scoring framework
*  Founder-ready validation checklist
*  Multi-language support

These are **future possibilities**, not features currently implemented in the workflow.

---

#  Project Status

** Functional Prototype**

Current workflow components:

* ✅ n8n Chat Trigger
* ✅ n8n AI Agent
* ✅ Google Gemini integration
* ✅ Gemini 3.1 Flash Lite
* ✅ Simple Memory
* ✅ Structured startup analysis
* ✅ Scope-controlled AI behavior

The workflow itself is currently marked inactive in the exported configuration, so activation should be done after importing and configuring credentials.

---

#  What This Project Demonstrates

This project demonstrates practical experience with:

```text
AI Agents
    ↓
Prompt Engineering
    ↓
Workflow Automation
    ↓
LLM Integration
    ↓
Conversational Memory
    ↓
Structured Business Analysis
```

Rather than building a generic chatbot, the workflow uses **defined agent behavior + structured reasoning + memory + automation** to solve a specific business problem.


---

<p align="center">

### ⭐ If this project helped you, consider starring the repository!

**Built with 🤖 AI + ⚙️ n8n + 💡 Startup Thinking**

</p>
