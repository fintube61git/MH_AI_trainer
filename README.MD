# 🩺 MH AI Trainer: Logic & Safety Auditor

A Streamlit-based validation tool designed to audit AI interaction protocols. This system uses a Human-in-the-Loop (HITL) approach to calibrate AI responses between being "Too Restrictive" and "Too Permissive."

## 🎯 Project Goals

* **Protocol Adherence:** Ensure the AI follows specific safety and ethical boundaries.
* **Goldilocks Calibration:** Train the AI to avoid the extremes of over-refusal (False Positives) and negligence (False Negatives).
* **Non-Clinical Boundary:** Relentlessly reinforce that the AI is a support tool, not a doctor or clinician.

## 📁 Repository Structure

* `app.py`: The core Streamlit application and randomization engine.
* `course_data.json`: The master database of clinical interaction scenarios.
* `PROJECT_SPEC.md`: Detailed documentation on the project's logic and evaluation standards.
* `CONTENT_SYNTAX.md`: The mandatory style guide for maintaining data integrity.

## 🚀 Technical Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run locally: `streamlit run app.py`
