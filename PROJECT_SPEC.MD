# 🩺 Mental Health AI Trainer - Master Project Specification (v0.9)

## 1. Project Overview

**System Name:** Clinical AI Trainer / Logic Validator  
**Current Version:** Prototype v0.9  
**Objective:** To train and validate an AI’s ability to handle mental health scenarios by having human clinical experts audit responses against specific safety, ethical, and interaction protocols.

---

## 2. Core Logic & Mechanics

### A. The "Goldilocks" Calibration Standard

The primary goal is to train the AI to find the balance between two failure states:

* **False Positive (Too Restrictive):** The AI is overly sensitive or paranoid, triggering crisis refusals for safe emotions or metaphors. This destroys rapport and renders the tool useless.
* **False Negative (Too Permissive):** The AI is negligent or "too nice," missing lethal plans, medical emergencies, or overstepping boundaries by diagnosing. This creates real-world risk.

### B. Two-Layer Randomization Engine

* **Scenario Shuffling:** Upon loading a module, the system pulls **5 unique scenarios** from the master database using `random.sample()`.
* **Option Shuffling:** To prevent rote memorization, answer options (Correct + Distractors) are shuffled locally for every question.
* **Session Persistence:** Uses Streamlit `session_state` to ensure progress isn't lost during an active audit loop.

---

## 3. Data & Content Standards

### A. Terminology Constraints

* **The AI:** Referred to strictly as "The AI" or "The AI response."
* **The Human:** Referred to strictly as "The User." (The term "Patient" is banned to prevent the AI from adopting a medical persona).

### B. Answer & Feedback Formula

Every assessment must follow a strict natural language rationale to prevent "shortcut" learning:

1. **Answer Options:** Must start with `"The AI response is [Correct/Incorrect] because..."` and link directly to the current Module's Objective.
2. **Correct Feedback:** Must follow the pattern: `[Verdict] + [Identification] + [Reinforcement of Principle]`.
3. **Safety Trap Feedback:** Must explicitly state if the error was **"Too Restrictive"** or **"Too Permissive."**

---

## 4. Module Architecture

Evaluation is based solely on the specific **Learning Objective** of the active module:

* **Orientation:** Core HITL (Human-in-the-Loop) principles.
* **Clinical Reasoning:** Identifying reasoning vs. diagnostic overreach.
* **Precision without Jargon:** Plain language vs. clinical labels.
* **Risk Calibration:** Distinguishing distress from active lethal risk.
* **Pseudo-Therapy:** Spotting the "Righting Reflex" and unsolicited advice.
* **Values & Neutrality:** Identifying moralizing and bias.
* **Visual Inference:** Differentiating observation from psychological inference.
* **Symbolic Content:** Distinguishing metaphor from literal medical emergencies.

---

## 5. File Manifest for Deployment

The following files are required for a complete, functional deployment:

1. `app.py`: The Streamlit application engine.
2. `course_data.json`: The master database of clinical scenarios.
3. `requirements.txt`: Necessary Python libraries (`streamlit`).
4. `.gitignore`: Rules to exclude cache and local config files.
5. `PROJECT_SPEC.md`: This documentation.
6. `CONTENT_SYNTAX.md`: The mandatory style and voice guide for data entry.
