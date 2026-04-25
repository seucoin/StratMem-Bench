# 📦 StratMem-Bench Dataset

This repository contains the **StratMem-Bench dataset**, a benchmark for evaluating memory use in virtual character dialogue.

---

## 📊 Overview

StratMem-Bench is a dataset for **single-turn dialogue generation** with an emphasis on how models utilize a provided memory pool.

Each instance includes:
- a user query
- a virtual character persona
- a set of candidate memories

Models are expected to generate responses based on these inputs.

---

## 📁 Data Format

The dataset is stored as a JSON file:

StratMemBench.json

Each entry has the following structure:

{
  "id": "unique_id",
  "query": "...",
  "query_time": "...",
  "history": "...",
  "roles": {
    "human": "...",
    "virtual_person": "..."
  },
  "memory": {
    "must": [{"fact": "..."}],
    "nice": [{"fact": "..."}],
    "irr": [{"fact": "..."}]
  },
  "virtual_person_persona": {
    "virtual_person_name": "...",
    "summary": "...",
    "traits": [...],
    "style": [...],
    "domains": [...],
    "values": [...]
  }
}

---

## 🔍 Field Description

### id
Unique identifier for each instance.

### query
The current user question.

### query_time
Timestamp of the query.

### history
Dialogue history (may be empty).

### roles
Defines the participants:
- human: user name
- virtual_person: character name

### memory
A set of candidate memory items:

- must: essential information
- nice: optional supportive information
- irr: irrelevant information

Each memory item is a short factual statement:
{"fact": "..."}

### virtual_person_persona
Describes the virtual character, including:
- summary
- personality traits
- speaking style
- domains of knowledge
- values

---

## 🧪 Example

{
  "query": "When did you last go swimming with your kids?",
  "memory": {
    "must": [
      {"fact": "Melanie went swimming with her kids on 2023-05-08."}
    ],
    "nice": [],
    "irr": [
      {"fact": "Melanie painted a lake sunrise in 2022."}
    ]
  }
}

---

## 📥 Usage

### Load the dataset

```python
import json

with open("StratMemBench.json", "r") as f:
    data = json.load(f)

print(len(data))
```

---

### Typical input construction

[Persona]
...

[Dialogue History]
...

[Memory Pool]
...

[User Query]
...

---

## ⚠️ Notes

- Memory items are provided as **unlabeled text during inference** (no role annotations should be exposed to models).
- The dataset is designed for **single-turn generation tasks**.
- All data is **synthetic or anonymized**.

---

## 📜 License

(To be added)

---

## 📬 Contact

(To be added)
