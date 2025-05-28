# LLM\_DSL\_Evaluation

This repository serves as the main entry point for setting up and managing the **DSL Model Generation Evaluation Framework using LLMs**. It provides tooling to:

* Install and run LLMs via [Ollama](https://ollama.com/)
* Generate DSL models using a structured prompt
* Launch a feedback web app for collecting human evaluations
* Manage evaluations through an admin panel
* Expose APIs to support evaluation workflows

---

## 🔧 Prerequisites

* Python 3.9+
* [Ollama](https://ollama.com/) (for local LLM execution)

Install Ollama (follow the instructions for your OS):

```bash
https://ollama.com/download
```

Then install required Python packages:

```bash
pip install -r requirements.txt
```

---

## 📦 Repository Structure

This main repository links to the following separate components:

* 🔗 [LLM\_Evaluation\_API](https://github.com/baberjunaid/LLM_Evaluation_API) – Flask API backend
* 🔗 [LLM\_Evaluation\_Feedback](https://github.com/baberjunaid/LLM_Evaluation_Feedback) – Streamlit feedback web app
* 🔗 LLM\_Evaluation\_Admin – Local folder (admin panel)

```bashbash
LLM_DSL_Evaluation/
├── ollama_list.txt              # List of all Ollama models used
├── exp_ollama/
│   └── prompt_exp.py           # Script to run prompt across models and generate DSL output
├── LLM_Evaluation_API/         # Flask API backend
├── LLM_Evaluation_Feedback/    # Streamlit app for collecting human feedback
├── LLM_Evaluation_Admin/       # Streamlit admin interface
└── README.md                   # This file
```

---

## 🤖 Setup Ollama & Pull Models

Ensure Ollama is installed and running, then pull the required models listed in `ollama_list.txt`:

```bash
ollama pull $(cat ollama_list.txt)
```

This will download all required LLMs locally.

---

## 🚀 Generate DSL Outputs

Navigate to `exp_ollama` and run the prompt experimentation script:

```bash
cd exp_ollama
python prompt_exp.py
```

This will:

* Load all models listed
* Send the DSL generation prompt
* Save JSON outputs for evaluation

---

## 🖥 Admin Interface

Navigate to `LLM_Evaluation_Admin`:

```bash
cd LLM_Evaluation_Admin
streamlit run admin_app.py
```

Allows you to:

* Create new evaluations
* Upload generated JSON files
* Set descriptions and prompt information
* Edit/delete entries

---

## 🌐 Feedback Interface

Navigate to `LLM_Evaluation_Feedback`:

```bash
cd LLM_Evaluation_Feedback
streamlit run feedback_app.py
```

Allows human evaluators to:

* Select an evaluation
* Enter demographic info
* Review model outputs
* Submit ratings and optional comments

---

## 🔗 API Server

Navigate to `LLM_Evaluation_API`:

```bash
cd LLM_Evaluation_API
python app.py
```

Provides:

* REST endpoints for evaluation metadata and JSON model retrieval
* Feedback submission endpoint

Make sure this is running before using the feedback or admin interfaces.

---

## 📝 Note

All evaluations are saved in `list_of_evaluations.xlsx` and model outputs in `json_models/`. Feedback is stored in `feedback_data/`.

For prompt formatting inside descriptions, use the `<prompt>...</prompt>` block to provide clean tooltips in the feedback UI.

---

## 📬 Contributions

Feel free to fork, raise issues, or suggest enhancements. This repo aims to streamline prompt-based DSL evaluation at scale using LLMs.
