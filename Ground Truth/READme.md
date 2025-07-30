# 🧠 Ground Truth Package

This folder contains the annotated ground truth and associated files used in our evaluation of software decomposition techniques. It includes the extracted class lists, LLM-based layer identification outputs, and partition structures for both ground truth and tool-generated results.

---

## 📁 Folder Structure

```
ground_truth/
└── AppName/
    ├── extracted_Classes.csv
    ├── Coded_<AppName>.csv
└── partition/
    ├── ground_truth.json
    ├── <Tool1>_partition.json
    ├── <Tool2>_partition.json
    └── ...
```

---

## 📄 `extracted_Classes.csv`

This file contains the list of all class names extracted from the application.  
These classes form the basis of all annotations and partitioning work in subsequent steps.

**Format:**
```csv
ClassName, Code, Path
```

---

## 📄 `Coded_<AppName>.csv`

This file contains the results from **Phase 1: Layer Identification**, where each class was annotated using the **LLaMA 3.3 70B** model.

Each row provides:
- The class name
- The predicted architectural or functional layer (e.g., User Layer, Data Layer, AI Preprocessing Layer, etc.)

**Example Format:**
```csv
ClassName,User Layer,Logic Layer,Data Layer,Non-AI Layer,AI Preprocessing Layer,Model Training & Evaluation Layer,Model Deployment Layer
ClassA,0,0,1,0,1,0,0
ClassB,0,0,0,0,0,1,0
...
```

This layer annotation serves as a rich structural representation for ground truth validation and component classification.

---

## 📁 `partition/`

This subfolder contains the class partitions used in the evaluation process.

### ✅ `ground_truth.json`

- The **manually defined ground truth partition**.
- Used as the reference baseline for all evaluation metrics (e.g., precision, recall).

### 🛠 Tool-Generated Partitions

Files such as:
- `Asparagus_partition.json`
- `Stock News Prediction_partitions.json`
- `Text Analyzer_partition.json`

These represent the output of each tool/approach and are compared against `ground_truth.json` during evaluation.

**Format Example (`*_partition.json`)**:
```json
{
  "partition_1": ["ClassA", "ClassB"],
  "partition_2": ["ClassC"],
  ...
}
```

---

## 📌 Notes

- All class names are assumed to be unique.
- Ensure that all partition files and layer mappings operate on the same set of class identifiers (as defined in `classes.csv`).
- The `Coded_<AppName>.csv` file can be used to derive semantically guided groupings or feature inputs for machine learning models.


---
