# AI-Medical-Assistant

An intelligent, multi-modal assistant for clinical diagnostics, designed to interpret radiology reports, analyze medical images, and support natural language interactions for patients and clinicians.

---

## 🧠 Project Overview

**AI-Medical-Assistant** is a robust, full-stack AI application that integrates advanced NLP and computer vision models to:

* Summarize and interpret unstructured medical reports.
* Perform phrase grounding on medical images.
* Enable natural language conversations about diagnostic content.
* Provide a patient-friendly, intuitive interface.

The system is designed to support both clinical professionals and non-expert users, improving diagnostic clarity, follow-up tracking, and medical education.

![DEMO ScreenShots](https://drive.google.com/uc?export=view&id=1knwQGGP0IUyRJOUPRcK0DRa1TOOuh8HK)

---
![DEMO ScreenShots](https://drive.google.com/file/d/1jdIcrhJaZ9lXwkhxDnlC5g6k0hwJW7AY)
---

## 🚀 Features

### 1. **Medical Report Understanding**

* Extracts findings, impressions, and critical terms from free-text reports.
* Summarizes reports using transformer-based biomedical LLMs (e.g., MedLLaMA2, Gemma).
* Identifies medical conditions, anatomical regions, and temporal progressions.

### 2. **Medical Image Phrase Grounding**

* Uses **BioViL-T (Biomed Vision-Language Transformer)** to link medical phrases to bounding boxes in X-rays or other imaging.
* Supports both standalone phrase detection and joint embedding visualization.
* Offers attention heatmaps and feature-wise interpretability.

### 3. **Conversational AI Interface**

* Integrated chatbot powered by **Gemini API** or **Ollama-local Gemma**.
* Answers patient questions in layman terms or clinician-level detail.
* Context-aware: uses document embeddings and visual evidence in responses.

### 4. **Real-Time Semantic Search**

* Medical terms and phrases are embedded via Sentence-BERT-style encoders.
* Stored in **Astra DB vector database** for efficient nearest-neighbor lookup.
* Enables search over historical reports, comparisons, and trends.

### 5. **Streamlit-based Web App**

* Lightweight and privacy-first design.
* Minimalistic Apple-style UI for easy interaction.
* Upload image and report → get analysis, bounding boxes, chatbot, and summary.

---

## 🏗️ Architecture

```mermaid
flowchart TD
    A[Upload DICOM/Image + Report] --> B[BioViL-T for Image Embedding + Phrase Grounding]
    A --> C[LLM (MedLLaMA2/Gemma) for Text Embedding + Summarization]
    B --> D[Overlay Bounding Boxes on UI]
    C --> E[Generate Summary / Extract Conditions]
    C --> F[Generate Embeddings for Search]
    E --> G[Streamlit Chatbot Response (Gemini API)]
    F --> H[Astra DB Vector Store]
    G --> I[Interactive Response in Chat UI]
```

---

## 🧰 Tech Stack

| Component              | Technology Used                        |
| ---------------------- | -------------------------------------- |
| Frontend UI            | Streamlit                              |
| Backend API (Optional) | Flask                                  |
| Vision Model           | BioViL-T (Hugging Face Transformers)   |
| Language Model         | MedLLaMA2 / Gemma via Ollama           |
| Embedding Search       | Astra DB (Vector DB)                   |
| Image Processing       | OpenCV, PIL                            |
| Deployment             | Localhost or Cloud (Docker compatible) |

---

## 🧪 Setup Instructions

1. **Clone the repo**

```bash
git clone https://github.com/your-username/AI-Medical-Assistant.git
cd AI-Medical-Assistant
```

2. **Create environment**

```bash
conda create -n medai python=3.10 -y
conda activate medai
pip install -r requirements.txt
```

3. **Start Streamlit app**

```bash
streamlit run app.py
```

4. **(Optional)**: To use local LLM (Gemma via Ollama)

```bash
ollama run gemma:7b
```

---

## 📊 Example Use Case

* A chest X-ray is uploaded along with a radiology report.
* The app overlays bounding boxes for terms like “consolidation” or “opacity.”
* A summary is generated highlighting key findings and impressions.
* A patient can ask: “What does lung consolidation mean?” → chatbot explains in simple terms.
* Clinician can search: “All cases with bilateral effusion” → retrieves matching embeddings from Astra DB.

---

## 📁 Folder Structure

```bash
AI-Medical-Assistant/
├── app.py                   # Streamlit frontend
├── image_processor.py      # Image upload + BioViL-T wrapper
├── report_summarizer.py    # MedLLaMA2/Gemma-based summarization
├── chatbot_engine.py       # Gemini/Gemma interaction
├── embeddings_db.py        # Astra DB connection
├── requirements.txt        # Dependencies
├── assets/                 # Logo, image samples, etc.
└── README.md
```

---

## 🧬 Future Roadmap

* [ ] HIPAA-compliant deployment with FastAPI backend
* [ ] User account system for clinicians and patients
* [ ] Auto-detection of imaging modality and disease type
* [ ] Integration with FHIR/HL7 APIs for hospital interoperability
* [ ] Real-time metrics dashboard

---

## 📄 Citation / Reference

If you use this for research or demos, please cite or mention:

> "AI-Medical-Assistant: A Multi-modal Clinical Assistant" — Developed by Bravim K. Purohit (2025)

---

## 📬 Contact

For collaborations, contact: **Bravim K. Purohit** — [bravimpurohit@gmail.com](mailto:bravimpurohit@gmail.com)
