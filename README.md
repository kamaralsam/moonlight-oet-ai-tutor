<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10%2B-blue?logo=python" />
  <img src="https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter" />
  <img src="https://img.shields.io/badge/OpenAI-API-412991?logo=openai" />
  <img src="https://img.shields.io/badge/ML-TF--IDF%20%2B%20LLM-brightgreen" />
  <img src="https://img.shields.io/badge/Status-Prototype-informational" />
  <img src="https://img.shields.io/badge/Contributions-Welcome-success" />
</p>

**🌙 Moonlight OET AI Tutor – Retrieval-Augmented LLM Demo**

This project is a small but powerful demo of how an LLM + retrieval system can work together to support students preparing for the OET (Occupational English Test).

It combines:

TF-IDF similarity search (to find relevant past samples)

OpenAI’s GPT-4.1-mini (to generate clear, helpful explanations)

Friendly tutor-style responses

Error-tolerant design (gracefully handles rate limits / offline mode)

As a result, the system acts like a tiny AI tutor:
it retrieves similar OET examples from your dataset and explains why certain answers are correct, partial, or incorrect — in a simple, encouraging tone.

**⭐ Why I Built This**

I’m building “Moonlight OET,” a set of study tools for healthcare professionals preparing for the OET exam.
This project is the first step toward a full AI-powered OET assistant that:

understands student questions

retrieves the most relevant examples

explains common mistakes

provides actionable exam tips

This notebook is a baseline prototype that I will expand later into a full RAG (Retrieval-Augmented Generation) system.

**🧠 How It Works (Simple Overview)**
**1️⃣ Load a small dataset**

A concise CSV of labeled OET samples (correct, incorrect, partial) is prepared in
01_data_preparation.ipynb.

**2️⃣ Build a TF-IDF retriever**

Using sklearn, the model finds the closest examples to any new student question.

**3️⃣ Create context for the LLM**

Relevant examples are formatted into a readable context block:

Example 1:
Text: ...
Label: Partial
Task: Reading Part A

**4️⃣ Ask the LLM**

The LLM receives both the question + examples and responds as:

short

clear

encouraging

OET-focused

**5️⃣ Friendly error handling**

If the API hits a rate limit or disconnects, the tutor responds gently instead of crashing.

**📁 Project Structure**
moonlight_oet_ai_tutor/
│
├── data/
│   ├── raw/                 # raw reading/listening text
│   └── processed/           # merged + cleaned dataset
│       └── oet_samples_small.csv
│
├── notebooks/
│   ├── 01_data_preparation.ipynb   # create processed dataset
│   └── 02_baseline_qa.ipynb        # retrieval + LLM tutor demo
│
├── src/
│   └── prompt_templates.py         # optional prompt building helpers
│
└── README.md

**🚀 How to Run the Tutor Yourself**
**1. Create a virtual environment**
python -m venv .venv
.venv\Scripts\activate

**2. Install dependencies**
pip install -r requirements.txt

**3. Add your OpenAI API key**

Inside 02_baseline_qa.ipynb, update:

client = OpenAI(api_key="YOUR_KEY_HERE")

**4. Run the notebook**

Start with → 01_data_preparation.ipynb
Then → 02_baseline_qa.ipynb

You will see:

retrieved examples

similarity scores

a friendly tutor explanation

**💡 Example Output (Conceptual)**

To avoid losing marks for partial answers in OET Listening, try to capture the full detail — not just the main idea.
Partial answers often miss numbers, timings, or instructions.
A quick tip: listen for verbs + details, and double-check the end of the recording for clarifications.

**🌟 What I Learned**

How to build a simple retrieval system

How to structure an LLM workflow with context + labels

How to design friendly AI user experiences

How to handle rate limits and API errors gracefully

How to package small ML/LLM demos into clean portfolio projects

**✨ Next Steps (Future Work)**

Move from TF-IDF to a small embedding model

Add student progress tracking

Build a lightweight web UI (Streamlit/FastAPI)

Expand dataset to full OET Reading/Listening samples

Turn this into part of a RAG-powered study assistant
