# 📝 Text Summarizer — End-to-End NLP Pipeline With LLMs

## 📌 Overview

**TextSummarizer** is a modular, production-style Natural Language Processing (NLP) system designed to generate high-quality summaries from long-form input text.  

The project follows a **clean, multi-stage pipeline architecture** commonly used in real-world ML systems and includes:

- 🚀 A fully modular NLP pipeline under `src/textSummarizer/`  
- 📦 Reusable components for preprocessing, tokenization, and summarization  
- ⚙️ YAML-driven configuration (`params.yaml`)  
- 🌉 CLI interfaces (`main.py`, `app.py`)
- API included (FastAPI) to serve the model  
- 🐳 Dockerized environment for reproducible execution  
- 🧪 Research notebooks & sandbox folder (`research/`)  
- 📦 Python packaging (`setup.py`)  
- 📚 Logging, utilities, and entity-based configs like production ML systems  

## 🎯 Problem / Goal

As the amount of digital text grows, organizations need tools that can:

- Reduce reading time  
- Extract essential insights  
- Summarize large documents automatically  
- Deliver consistent results without human bias  

**Goal:** Build a maintainable, modular text summarization system that can be expanded with extractive or abstractive models and integrated into larger applications.


## 🤖 Model Training (PEGASUS-SAMSum)  
The project includes a full training workflow using:

**Model:** `google/pegasus-samsum`  
**Dataset:** Dialogue and conversational corpora (SAMSum-style)  
**Purpose:** Improve summarization performance on unstructured, dialogue-like or mixed-format text.

### 🔧 Training Steps:
- Tokenization + preprocessing  
- Input/output pair generation  
- Fine-tuning via Hugging Face Trainer  
- Validation + evaluation metrics  
- Saving the trained model to local `artifacts/` directory  

This results in a summarization model that produces **clearer, more human-like summaries**.

## 🚀 FastAPI Deployment  
The project includes a full **FastAPI service** for real-time summarization.

### ✔ Built-in Endpoints
- `/` → redirected to the docs  
- `/train` → to train the model  
- `/predict` → to make prediction
  


## 🧱 Architecture & Pipeline Design

The entire summarization workflow is structured into **modular components**, enabling reuse, testing, and easy upgrades.

### 📁 Folder Structure

```
textsummarizer/
│
├── app.py # Optional API / CLI interface
├── main.py # Main entry point for pipeline execution
│
├── src/
│ └── textSummarizer/
│ ├── components/ # Core modules: ingestion, processing, summarization
│ ├── config/ # Centralized configuration handling
│ ├── constants/ # Project-level constants
│ ├── entity/ # Config entities (dataclasses)
│ ├── logging/ # Project-wide logger
│ ├── pipeline/ # High-level pipeline orchestration
│ └── utils/ # Helpers for paths, reading text, tokenization
│
├── config/ # Additional config resources
├── research/ # Notebooks for experimentation
│
├── params.yaml # YAML-driven pipeline settings
├── requirements.txt # Project dependencies
├── Dockerfile # Docker deployment
├── setup.py # Packaging for pip install
├── template.py # Template code for module scaffolding
└── README.md

```

## 🔍 How The Pipeline Works

### 1️⃣ **Configuration Layer**
Located in:

src/textSummarizer/config
src/textSummarizer/entity
params.yaml

- YAML inputs define the summarization parameters  
- Config + Entity classes convert YAML into strongly typed objects  
- Centralized settings ensure pipeline reproducibility  

### 2️⃣ **Components Layer (Core Processing)**

Found under:
```
src/textSummarizer/components/
```

Typical components include:

- data_ingestion  
- data_transformation 
- model_trainer 
- model_evaluation

Each component is its own class/module, making the system **clean and maintainable**.

### 3️⃣ **Pipeline Layer**

Found under:
```
src/textSummarizer/pipeline/
```

This layer orchestrates the full text-summarization training flow:

data_ingestion → data_transformation  → model_trainer 
 → model_evaluation.

## 🧠 Methodology

Depending on configuration, the summarizer can support:

- **Extractive summarization** (identifying key sentences)  
- **Abstractive summarization** (model-generated rewriting)  
- **Hybrid methods**  

The architecture is model-agnostic, meaning:

- You can plug in your own LLM  
- Add a Hugging Face transformer  
- Integrate OpenAI/Cohere APIs  
- Extend chunking to support long-context models  

This modularity is exactly how enterprise ML teams structure scalable NLP services.

---

## ⚙️ Tech Stack

### **Languages & Frameworks**
- Python 3.x  
- PyYAML  
- PyTorch / Transformers (if integrated)  
- FastAPI for Model serving 
- LLMs
- Nltk

### **Infrastructure**
- Docker   
- CLI runtime  
- YAML-driven configuration  

### **Development**
- Modular ML design  
- OOP-based component abstraction  
- Logging + utilities  
- Research notebooks  

---

## 🚀 Running the Project

### 1️⃣ Local Installation

```bash
git clone <repo-url>
cd textsummarizer

python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate

pip install -r requirements.txt
python3 app.py

```

Happy Coding!!!

