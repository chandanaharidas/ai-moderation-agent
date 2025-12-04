# AI Content Moderation Dashboard Using Gemini & Flask

An end-to-end AI system that moderates harmful text using **Gemini** with a fully interactive dashboard for both single and batch text moderation.

## Project Type
**Agents Intensive – Capstone Project**

**Problem Statement :**

Online platforms receive millions of user posts daily, and many contain unsafe content such as harassment, hate speech, toxicity, sexual content, and violent threats. Manual moderation is slow, expensive, and not scalable.

This project aims to build an AI-based content moderation system that can automatically classify unsafe content and help keep online platforms safe.The goal is to automate detection and reduce human workload while improving accuracy and speed.
Why agents?

In this project, I designed a parallel agent system because content moderation is not a single-step task. Different types of harmful behavior (harassment, hate speech, toxicity, sexual, violence etc) require different forms of analysis.

Instead of depending on one large agent to do everything, I created multiple specialized agents, each with a dedicated responsibility:
**Harassment Agent** → Detects rude, insulting, intimidating behavior

**Hate Speech Agent** → Detects prejudice targeting race, gender, religion, caste, or groups
**Spam Agent** → Detects spam, scams, promotions
**Toxicity Agent** → Detects rude, aggressive, negative language
**Sexual Agent** → Detects adult content or sexual content
**Self Harm Agent** → Detects suicide intent or self-harm
**Violence Agent** → Detects threats of physical harm or violence.

Each agent has its own prompt and rules. This ensures higher accuracy because each agent focuses only on one category of unsafe content.
To improve speed and efficiency, I executed all agents in parallel using Python’s concurrent.futures module. This means the system runs all moderation checks at the same time, allowing fast, real-time content classification.

**Benefits of using parallel agents:**

    Faster processing (multiple checks run simultaneously)
    More accurate results
    Modular and scalable design (new agents can be added easily)
    Closer to real Trust & Safety systems used in industry

**Core Concept & Value**

The core idea of my project is a parallel multi-agent moderation system, where multiple agents independently analyze the same text for different harmful behaviours (harassment, hate speech, spam, toxicity, etc.).

Instead of relying on one large model, each agent is specialized and focuses on only one category.
This improves accuracy and reduces misclassification.

Value of this approach:

Real-time automated detection

Higher accuracy with dedicated agents

Faster outputs through parallel execution

Scalable system (easily add new agents)

Reduces workload for human moderators

Supports safer online platforms

Together, the parallel agents and structured outputs create a practical, high-value solution for Trust & Safety teams handling large volumes of content.
What I created --

I built an end-to-end AI Content Moderation System that combines Colab (for backend logic), Flask (for the API layer), and Gemini (for running parallel agents).

Backend in **Google Colab**
The backend is developed and executed in Google Colab. All agent definitions, prompts, parallel execution logic, and result formatting happen here.

Colab manages:
    loading Gemini
    running all parallel agents
    generating JSON outputs
    handling multi-line inputs

This is the main engine of the moderation system.

**Flask API Layer**
I exposed the moderation engine using a Flask API so that the system can communicate with a front-end dashboard.
Flask acts as the bridge between:

    User interface (HTML/JS)
    Gemini moderation agents
    JSON response renderer

The /moderate API endpoint receives text, sends it to the agents, and returns structured predictions.

Multi-Agent System Powered by Gemini
The core logic of my system uses parallel Gemini agents, each specializing in one harmful-content category:

    Harassment Agent
    Hatet Speech Agent
    Spam Agent
    Toxicity Agent
    Sexual Agent
    Self Harm Agent
    Violence Agent

Each agent has its own instructions and operates independently.
To improve speed, I execute all agents in parallel using Python’s concurrent.futures.
This allows the system to classify text in real-time.

**Complete Moderation Pipeline**
The system performs the following:

    Accepts raw text
    Passes it to the backend
    Runs multiple agents simultaneously
    Collects each agent’s decision
    Combines outputs into a final JSON result
    Sends the output back to the UI for display

Overall, I created a full moderation workflow from input → AI analysis → structured output → UI display. 

**Flow / Architecture--**
System Flow Diagram

<img width="1536" height="1024" alt="diagram" src="https://github.com/user-attachments/assets/4750e3ff-4236-400d-aa0a-428add2f4da6" />

**Architecture Explanation**

The system follows a simple flow from user input -> backend processing -> final output.
1. **User**
The user enters any text into the moderation dashboard.

2. **Frontend (HTML/CSS /JS)**

The frontend only handles th UI:

    accepts user input
    sends data to the backend
    displays results after processing

3. **Flask API Layer**

The Flask exposes a /moderate endpoint.
It:

    receives the text from frontend
    forwards it to the moderation engine running in Colab
    returns structured JSON output back to the UI

This layer connects the UI and the AI agents.
4. **Parallel Gemini Agents (Moderation Engine)**

This is the core intelligence of the system.

I used multiple specialized Gemini agents, each focused on detecting a specific harmful behavior:

    Harassment Agent
    Hate Speech Agent
    Spam Agent
    Toxicity Agent
    Sexual Agent
    Self Harm Agent
    Violence Agent

Each agent analyses the text independently using custom prompts.
All agents run in parallel using Python’s concurrent.futures, which:

    speeds up processing
    increases accuracy
    ensures modularity

5. **Aggregation / Final Output**

Once all agents finish:

    their outputs are collected
    merged into a single JSON result
    returned to Flask

This combined output includes:

    labels
    agent decisions
    safety classification

6. **Frontend Display**

The UI shows the final moderation:

    Green=safe
    Red=unsafe
    Category-wise breakdown
    Clear structured output

## Demo -- How It Works

This demo explains how my AI-based text moderation system works.

1️⃣ User enters a text

The process starts when the user types or pastes any text into the input box on my web interface.
This could be a comment, message, or any content that needs to be checked.

2️⃣ User clicks the “Moderate” button

Once the text is entered, the user clicks the Moderate button.
This triggers a request to the backend.

3️⃣ Frontend sends the text to the Flask backend

The text is sent through a POST request.
The frontend does not do any AI work — it simply collects the input and sends it to the server.

4️⃣ Flask backend receives and prepares the text

The backend:

Validates the input

Removes extra spaces

Ensures the text is not empty

Prepares the prompt for the Gemini AI model

Then it forwards the text to the moderation agent.

5️⃣ Gemini AI analyses the text

The AI checks the content for:

Hate speech

Abuse

Threats

Harassment

Sexual content

Toxicity

Harmful intent

Gemini returns:

A category

Action-Approve/Remove/Flag

Reason -A short explanation

6️⃣ Backend structures the AI response

The Flask backend formats the AI output into a clean JSON response:

label → safe or unsafe

reason → explanation

This helps the frontend display it neatly.

7️⃣ Result displayed to the user

The frontend finally shows:

The moderation decision (Safe/Unsafe)

Why it was marked that way

The result appears instantly, allowing the user to understand the safety of their text

5️⃣ Summary Dashboard

After performing multiple moderations ( batch), the system generates a real-time Summary Dashboard that helps the user understand the overall content safety patterns.

The summary includes:

✔ Total Processed

The total number of text items analyzed so far.

✔ Approved Count

How many texts were marked Safe.

✔ Rejected Count

How many texts were marked Unsafe :

✔ Unsafe Percentage

A quick metric showing how much of the content is considered unsafe.
This helps users understand the risk level at a glance.

✔ Recent Actions Panel

Displays the latest moderation decisions in order:

The exact text

Whether it was Approved or Rejected

Timestamp of moderation
The Build -- 🔧 Tools & Technologies Used

My AI Moderation System is built using a combination of modern web technologies and advanced AI tools. Each component plays a specific role in ensuring efficiency, accuracy, and smooth user experience.

## 1️⃣ Frontend (User Interface)

HTML, CSS, JavaScript

Builds a clean and responsive UI

Handles user input for single and batch moderation

Displays results in real-time (single result, table for batch, dashboard summary)

Sends requests to the Flask backend using Fetch API

## 2️⃣ Backend (Server Layer)

Python + Flask Framework

Acts as the API layer between the frontend and the AI model

Validates input text

Handles both single-text and batch-text requests

Reads .txt files for file-based batch moderation

Formats and returns structured JSON responses

## 3️⃣ AI Model (Moderation Engine)

Gemini 2.5 Flash (Generative AI Model)

Performs intelligent text moderation

Detects hate speech, harassment, toxicity, threats, adult content, and harmful intent

Provides reason + category + action

Supports both individual and batch moderation

Generates a summary after batch processing

## 4️⃣ Concurrency / Batch Processing Tools

Python’s concurrent.futures

Enables parallel processing of multiple lines

Makes batch moderation faster and scalable

Prevents the UI from hanging during large file processing

## 5️⃣ File Handling

Python File I/O

Supports .txt file upload

Extracts lines from files and moderates them one by one

## 6️⃣ Data Formatting

JSON

Used for clean communication between Flask and the frontend

Ensures structured, readable results

Useful for summary generation and table display

## 7️⃣ Deployment (Local Demo)

Flask Localhost (127.0.0.1:5000)

Used for testing the dashboard

Simulates real-world moderation pipeline

**If I had more time, this is what I'd do-**

    Login authentication
    Image/Video Moderation
    More categories (Fake News Detection,Cyber bullying,Child Safety)
    Database storage of moderation logs
    Dashboard analytics
