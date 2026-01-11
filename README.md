# WISE knowledge editing method on Qwen2.5-7B


## Statement of the Problem
- Large Language Models (LLMs) encode factual knowledge implicitly in their parameters, making direct knowledge updates difficult.
- Full retraining is computationally expensive, while fine-tuning often causes catastrophic forgetting and degrades unrelated knowledge.
- Knowledge editing methods enable targeted modification of specific facts but suffer from limited speed, scalability, and stability under sequential edits.
- This work addresses the problem of improving speed and quality of knowledge editing, focusing on sequential editing while preserving rewrite accuracy, generalization (rephrase, portability), and locality.
- Efficient and reliable knowledge editing is crucial for deploying LLMs in dynamic real-world environments where facts change over time.


## Purpose and Objectives
**Research purpose**: Evaluate the effectiveness of the [WISE](https://arxiv.org/abs/2405.14768) knowledge editing method on the ZsRE dataset, analysis of WISE knowledge editing method stability with a focus on sequential editing stability and query-type-specific performance

**Objectives**:
- Analyze existing knowledge editing methods and their limitations
- Configure and adapt the WISE knowledge editing algorithm for efficient local model updates on the ZsRE dataset.
- Design and implement a custom evaluation protocol for measuring knowledge retention under sequential edits.
- Implement a sequential editing pipeline on a large language model (Qwen2.5-7B).
- Analyze knowledge retention and degradation under multiple sequential edits.
- Conduct an analysis of editing behavior and retention across different question types (who, what, when, where, which).


## Research Methods and Tools
**Methods**:
- Experimental evaluation of knowledge editing methods on a dataset.
- Sequential knowledge editing to analyze stability and retention under multiple edits.
- Analytical evaluation using rewrite, rephrase, portability, and locality metrics.
- Continual retention analysis to measure knowledge degradation over time.
- Comparative analysis across different question types (who, what, when, where, which)

**Tools**: Python, EasyEdit, HuggingFace Transformers, PyTorch, NumPy, Matplotlib.

**Data**: ZsRE (Zero-Shot Relation Extraction) dataset.


## Scientific Novelty
- A **custom retention evaluation protocol** for sequential knowledge editing is proposed, enabling continual assessment of all previously edited facts after each new edit.
- The effectiveness of the WISE knowledge editing method is analyzed under **long sequential edit streams**, rather than isolated single edits.
- A **query-type-specific analysis** of knowledge editing behavior is introduced for the ZsRE benchmark.
- The interaction between local parameter editing, knowledge retention, and forgetting effects is systematically studied.
- The proposed evaluation setup **reveals limitations of standard post-edit metrics** and provides deeper insight into long-term editing stability.


## General solution flow
- Select a pre-trained large language model (Qwen2.5-7B-Instruct).
- Configure the WISE knowledge editing algorithm for local parameter updates.
- Apply knowledge edits sequentially using ZsRE benchmark facts.
- After each edit, re-evaluate all previously edited facts.
- Collect performance and retention metrics over time.

**Outcome**: A reproducible pipeline for analyzing sequential knowledge editing stability.


## Sequential Editing and Retention Evaluation
<img width="1915" height="919" alt="image" src="https://github.com/user-attachments/assets/01d584ae-83b6-4ecf-a378-201c5bbde7ee" />


## Query-Type-Specific Analysis
<img width="500" alt="image" src="https://github.com/user-attachments/assets/23a06e81-202e-4efd-bee2-8adf292f9046" />


## Key Results
<img width="1979" height="898" alt="image" src="https://github.com/user-attachments/assets/96a0c8f1-c804-4304-9493-714414bffa76" />

---
<img width="1984" height="960" alt="image" src="https://github.com/user-attachments/assets/041cce94-2683-47d1-929a-aa4fed7862a8" />


## Conclusion
- A sequential editing pipeline on a large language model (Qwen2.5-7B) was successfully implemented.
- A custom retention-aware evaluation protocol was designed and implemented.
- The model copes quite well with remembering the last fact edited using WISE (except for portability).
- However, the model correctly reproduces only about 15-17% of all previous facts edited using WISE.
- Edits associated with queries starting with "what" show the lowest retention performance.
- Edits related to "which" and "who" questions exhibit the highest stability in retention performance, without sudden complete knowledge loss (however, cumulative knowledge degradation is also present).
- For "who" and "when" queries, edits rarely transfer to related factual questions, resulting in very low portability.

**Future work**: Extend the analysis to other knowledge editing methods and models.


