# Data Directory: Requirements Ambiguity & Uncertainty Dataset

This directory contains annotated requirement datasets used for training, prompting, and evaluating the Large Language Model (LLM) ambiguity detection framework.

## Data Definition $(X, y)$

The core dataset maps raw, natural language software requirements to structured ground-truth quality annotations:

* **Input ($X$):** Raw requirement statement extracted from Software Requirements Specifications (SRS).
* **Target ($y$):** Structured ground truth annotation containing ambiguity status, defect categories, trigger terms, severity rating, and an actionable unambiguous rewrite.

---

## File Overview

| File | Format | Purpose |
| :--- | :--- | :--- |
| `requirements.csv` | CSV | Flat tabular structure suitable for quick inspection, baseline statistical models, and tokenizers. |
| `requirements.json` | JSON | Rich nested schema for LLM zero/few-shot prompting, RAG document indexing, and evaluation routines. |

---

## Annotation Schema ($y$)

Each requirement object follows this schema:

```json
{
  "id": "REQ-XXX",
  "X": "Raw requirement text",
  "y": {
    "is_ambiguous": true | false,
    "ambiguity_type": ["Lexical", "Syntactic", "Semantic", "Pragmatic", "Uncertainty"],
    "trigger_words": ["vague_term_1", "weak_modal_2"],
    "severity": "High" | "Medium" | "Low" | "None",
    "explanation": "Detailed explanation of defect reasons.",
    "suggested_rewrite": "Unambiguous IEEE 830-compliant requirement formulation."
  }
}
