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
Harassment Agent → Detects rude, insulting, intimidating behavior
Hate Speech Agent → Detects prejudice targeting race, gender, religion, caste, or groups
Spam Agent → Detects spam, scams, promotions
Toxicity Agent → Detects rude, aggressive, negative language
Sexual Agent → Detects adult content or sexual content
Self Harm Agent → Detects suicide intent or self-harm
Violence Agent → Detects threats of physical harm or violence.

Each agent has its own prompt and rules. This ensures higher accuracy because each agent focuses only on one category of unsafe content.
To improve speed and efficiency, I executed all agents in parallel using Python’s concurrent.futures module. This means the system runs all moderation checks at the same time, allowing fast, real-time content classification.

Benefits of using parallel agents:

    Faster processing (multiple checks run simultaneously)
    More accurate results
    Modular and scalable design (new agents can be added easily)
    Closer to real Trust & Safety systems used in industry

Core Concept & Value

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

Backend in Google Colab
The backend is developed and executed in Google Colab. All agent definitions, prompts, parallel execution logic, and result formatting happen here.

Colab manages:
##loading Gemini
    running all parallel agents
    generating JSON outputs
    handling multi-line inputs

This is the main engine of the moderation system.

Flask API Layer
I exposed the moderation engine using a Flask API so that the system can communicate with a front-end dashboard.
Flask acts as the bridge between:

    User interface (HTML/JS)
    Gemini moderation agents
    JSON response renderer

The /moderate API endpoint receives text, sends it to the agents, and returns structured predictions.

Multi-Agent System Powered by Gemini
The core logic of my system uses parallel Gemini agents, each specializing in one harmful-content category:

    **Harassment Agent**
    Hatet Speech Agent
    Spam Agent
    Toxicity Agent
    Sexual Agent
    Self Harm Agent
    Violence Agent

Each agent has its own instructions and operates independently.
To improve speed, I execute all agents in parallel using Python’s concurrent.futures.
This allows the system to classify text in real-time.

Complete Moderation Pipeline
The system performs the following:

    Accepts raw text
    Passes it to the backend
    Runs multiple agents simultaneously
    Collects each agent’s decision
    Combines outputs into a final JSON result
    Sends the output back to the UI for display

Overall, I created a full moderation workflow from input → AI analysis → structured output → UI display. 
