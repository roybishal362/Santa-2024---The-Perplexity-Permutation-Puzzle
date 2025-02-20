# 🎄 Santa 2024 Kaggle Competition – Ultra-Optimized Perplexity Minimization 🚀

## **📌 Project Overview**
This repository contains my **Kaggle Santa 2024 competition** solution, which focuses on reordering words in jumbled Christmas stories to minimize **perplexity**. The project implements an **advanced optimization pipeline** using **Large Language Models (LLMs), sentence embeddings, and simulated annealing-based search techniques**.  

## **🏆 Challenge Objective**
- The input dataset contains **shuffled text passages**.  
- The goal is to **reorder words correctly** while preserving all original words.  
- The **evaluation metric** is **average perplexity** (lower scores are better).  

The competition uses **Gemma 2 9B** for final perplexity scoring.

---

## **📂 Dataset & Evaluation**
- **`sample_submission.csv`**: Contains the dataset with shuffled text.  
- **Evaluation Metric**: **Perplexity** (lower = better readability & coherence).  
- **Final Score Computation**:  
  - Each row's text is **processed and reordered**  
  - **Gemma 2 9B** computes **perplexity per row**  
  - The final submission is **ranked by mean perplexity**  

---

## **🔧 Implementation Details**
### **1️⃣ Model Selection**
To optimize perplexity, I tested multiple **LLMs**:  
- **Gemma 2 9B** (Kaggle Official Model)  
- **Mixtral 8x7B** (Higher efficiency & lower perplexity scores)  

| Model | Perplexity Score ↓ (Lower is Better) |
|------------|----------------|
| **Gemma 2 9B** | **2369.73** |
| **Mixtral 8x7B** | **1833.96** |

🚀 **Mixtral performed significantly better**, reducing perplexity by **535.77 points**.  

---

### **2️⃣ Optimization Pipeline**
I developed an **iterative simulated annealing-based approach** to refine word order while maintaining **strict permutation constraints**. The key steps are:

✅ **Step 1:** Tokenization & LLM Setup  
✅ **Step 2:** Compute initial perplexity  
✅ **Step 3:** Iterative word reordering using:  
   - **Word Swapping**  
   - **Block Exchanges**  
   - **Partial Shuffling**  
✅ **Step 4:** Evaluate **perplexity score** after each iteration  
✅ **Step 5:** Accept or reject permutations based on **Boltzmann acceptance probability**  
✅ **Step 6:** Continue iterations until no further improvement  

---

## **🛠️ How to Run**
### **1️⃣ Install Dependencies**
```bash
pip install torch transformers sentence-transformers pandas numpy 
```

## **🔍 Key Insights & Findings
- Mixtral 8x7B significantly outperforms Gemma 2 in this task.
- Using adaptive temperature annealing (5.0 → 0.5) leads to more refined word order.
- Strict permutation validation ensures rule compliance and prevents data leakage.
- Quantization techniques (4-bit loading) reduce VRAM usage while maintaining performance.



