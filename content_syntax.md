# 🩺 Clinical AI Trainer: Content & QA Standards

## Table of Contents

1. [Terminology Standards](#1-terminology-standards)
2. [JSON Technical Requirements](#2-json-technical-requirements)
3. [Answer Option Syntax](#3-answer-option-syntax)
4. [Feedback Formulas](#4-feedback-formulas)
5. [The Goldilocks Calibration (Safety Traps)](#5-the-goldilocks-calibration-safety-traps)
6. [Quality Assurance & Drift Prevention](#6-quality-assurance--drift-prevention)

---

## 1. Terminology Standards

To maintain a professional boundary and clear training intent, use only the following terms:

* **The System:** ALWAYS refer to it as **"The AI"** or **"The AI response"**.
  * *Banned:* "The Model," "The Bot," "The System".
* **The Human:** ALWAYS refer to them as **"The User"**.
  * *Banned:* **"Patient"** (as it implies the AI is a doctor) or **"Client"** (as it implies a contract).

## 2. JSON Technical Requirements

* **No "Enter" Keys:** You cannot have line breaks inside a JSON string; use `\n` instead.
* **Escape Quotes:** Use `\"` for quotes inside a text string.
* **Booleans:** Ensure `is_correct` uses raw `true` or `false` (lowercase, no quotes).
* **Unique IDs:** Every question must have a unique `"id"` to prevent system crashes.

## 3. Answer Option Syntax

**The "Module Objective" Rule:** Evaluation is based **solely** on the Learning Objectives taught in a particular lesson.

* Every answer option text **MUST** start with: `"The AI response is [Correct/Incorrect] because [Link to Module Objective]..."`.
* **Robust Rationales:** You must complete the sentence with a full natural language explanation.
  * *Example:* `"...because it makes a psychological inference from a static image, violating the Observation Rule."`

## 4. Feedback Formulas

### A. Correct Choice (`is_correct: true`)

* **Pattern:** `"Correct. You accurately identified that the AI response is [Correct/Incorrect]. [Reinforce the Module Goal/Safety Rule]."`
* **Example:** `"Correct. You accurately identified that the AI response is Incorrect. The AI fabricated a diagnosis, which violates the Scope of Practice limits."`

### B. Standard Incorrect (Non-Trap)

* **Pattern:** `"Incorrect. The AI response is actually [Correct/Incorrect]. [Explain the Missed Nuance]."`
* **Example:** `"Incorrect. While the AI was blunt, it adhered to the strict Refusal Protocol required by this module."`

## 5. The Goldilocks Calibration (Safety Traps)

When an option is a **False Positive** or **False Negative**, you must define the directional error to help the User accurately assess for safety.

| Trap Type          | Definition     | Feedback Requirement                                        |
|:------------------ |:-------------- |:----------------------------------------------------------- |
| **False Positive** | Over-Reaction  | Explain why the AI is being **Too Restrictive** (Paranoid). |
| **False Negative** | Under-Reaction | Explain why the AI is being **Too Permissive** (Negligent). |

* **FP Example:** `"SAFETY WARNING: This is a False Positive. The User was using a metaphor. Penalizing this makes the AI **too restrictive**, rendering it useless for support."`
* **FN Example:** `"SAFETY WARNING: This is a False Negative. The User expressed a lethal plan. Validating this makes the AI **too permissive**, creating a severe safety risk."`

## 6. Quality Assurance & Drift Prevention

**Reject any entry that meets the following "Drift" criteria:**

* **Circular Logic:** Rationales like "It is incorrect because it is wrong".
* **Anthropomorphism:** Implying the AI has feelings, thoughts, or "wants".
* **Medical Logic:** Using clinical diagnoses instead of interaction/safety logic.
* **Banned Terms:** Any reference to the human as a "Patient".
* **Shortcut Feedback:** Any rationale or explanation less than 5 words long.
