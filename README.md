# Code Generation Using LLM
## Introduction to the Problem  
This project addresses the problem of generating SQL queries from natural language inputs using Large Language Models (LLMs). It also enhances SQL query generation using Hierarchical Decomposition, addressing challenges in modularity, maintainability, and logical consistency by breaking down complex tasks into smaller subtasks. The solution involves:

- Leveraging pre-trained Transformer models (e.g., T5) for text-to-SQL query generation.
- Implementing Hierarchical Decomposition optimization to the T5 Model as a proposed solution.
- Utilizing evaluation metrics such as Fuzz Ratio, BLEU, and ROUGE scores to assess model performance.
- Testing and validation of SQL query generation to ensure consistency and accuracy.

## Solution Approach  
### Baseline Model  
- **Model:** T5 Transformer.  
- **Process:** Single-pass SQL query generation.  

### Proposed Model  
- **Framework:** Hierarchical Decomposition with 3 stages:  
  1. **Component Identification:** Break down the query into logical sections like `SELECT`, `FROM`, `WHERE`.
  2. **SQL Detail Filling:** Populate each component with specific details.
  3. **Query Construction:** Combine components into a complete query.

## Solution Outline  
1. **Dataset Preparation:**  
   - Load dataset of SQL queries stored in CSV format.
2. **Model Selection:**  
   - Use pre-trained T5 model for code generation and evaluation.
3. **Training and Evaluation:**  
   - Train the models on SQL queries and split the dataset into training and testing sets.  
   - Evaluate model performance in generating and identifying SQL query components.
4. **Component Identification:**  
   - Implement functions to identify specific SQL components (e.g., `SELECT`, `FROM`, `WHERE`) from model-generated outputs.  
   - Divide SQL components into subtasks, divide the dataset corresponding to each subtask, train and test each subtask using a pre-trained T5 Model.
5. **Output Analysis:**  
   - Retrieve test code, predicted code for baseline and proposed solution.  
   - Implement performance measures such as Fuzz Ratio, ROUGE score, and BLEU score.  
   - Compare results of the baseline solution with the proposed solution.

## Examples  
### Input 1:  
- **Question:** "How many departments have a budget greater than $1 million?"  
- **Baseline Output:** `SELECT COUNT(*) FROM department WHERE budget > 1000000;`  
- **Proposed Model Output:** `SELECT COUNT(*) FROM department WHERE budget > 1000000;`  

### Input 2:  
- **Question:** "List all employees in the IT department."  
- **Baseline Output:** `SELECT name FROM employees WHERE department = 'IT';`  
- **Proposed Model Output:** `SELECT name FROM employees WHERE department = 'IT';`  

## Setup Instructions  
### Requirements  
- **Software:**  
  - Python 3.8+  
  - PyTorch  
  - Transformers  
  - Pandas  
  - scikit-learn  
- **Hardware:**  
  - GPU-enabled system for efficient training.  

### Steps to Run  
#### Install Dependencies  
```bash
pip install torch 
pip install transformers 
pip install pandas 
pip install scikit-learn
```

#### Dataset  
- Download the SQL-Create-Context dataset from [Hugging Face](https://huggingface.co/datasets/b-mc2/sql-create-context).  

#### Run Notebook  
- **Baseline Model:** Open `AIT726_Team5_MR_PR_UD_BaselineSolution.ipynb` and follow the instructions to train and evaluate the baseline T5 model.  
- **Proposed Model:** Open `AIT726_Team5_MR_PR_UD_ProposedSolution.ipynb` and follow the instructions to train and evaluate the hierarchical decomposition T5 model.  

#### Evaluate  
- Use the testing scripts in the respective notebooks to compare predicted SQL queries with ground truth. Metrics like BLEU, ROUGE, and Fuzz Ratio will be calculated automatically.

## **Contributors**  
- Praneeth Ravirala
- Mukesh Rajmohan
- Utkarsh Jayesh Desai
