# 🤖 HMM + Q-Learning Based Hangman AI

This project implements a **Hybrid AI Agent** that plays the classic *Hangman* game using:
- a **Hidden Markov Model (HMM)** for letter probability estimation, and  
- **Q-Learning Reinforcement Learning (RL)** to improve guessing strategy over time.

The model learns from a large English corpus (`corpus.txt`) and is evaluated on unseen test words (`test.txt`).

---

## 🚀 Project Overview

The agent integrates two AI paradigms:
1. **HMM (Hidden Markov Model):**
   - Learns positional letter probabilities.
   - Models sequential dependencies using bigrams, trigrams, and contextual pattern statistics.

2. **Q-Learning (Reinforcement Learning):**
   - Learns an optimal guessing policy.
   - Uses a Q-table to decide whether to exploit known information or explore new letters.

---

## 🧠 Algorithm Details

### 🔹 Hidden Markov Model (HMM)
- **States:** Hidden letters in the target word.  
- **Observations:** Known letters (`a-z`) and blanks (`_`).  
- **Training:** Frequency-based learning from `corpus.txt`.  
- **Output:** Emission probabilities for each letter at each position.

### 🔹 Reinforcement Learning (Q-Learning)
- **State Representation:** `(prefix, suffix, blanks, lives_left, vowels_count)`
- **Actions:** Guessing one of the remaining unguessed letters.
- **Reward Function:**
  - ✅ Correct guess: `+15`
  - ❌ Wrong guess: `-8`
  - 🔁 Repeated guess: `-10`
- **Q-Update Rule:**
  Q(s,a) = Q(s,a) + α [r + γ * max(Q(s', a')) - Q(s,a)]
  where:
  - α = learning rate  
  - γ = discount factor  
  - r = reward  

---

## 📊 Evaluation Metrics

After training, the agent is evaluated on 1000 test words.

| Metric | Description |
|--------|--------------|
| **Success Rate** | Percentage of words guessed correctly |
| **Avg. Wrong** | Average number of wrong guesses per game |
| **Avg. Repeats** | Average number of repeated guesses |
| **Final Score** | Weighted performance score combining above metrics |

### Example Output:
```
FINAL METRICS:
 - Success Rate : 19.75%
 - Avg Wrong    : 5.58
 - Avg Repeats  : 0.00
 - Final Score  : -55405.00
```

---

## 📈 Learning Curve Plots

- Reward per Episode (training stability)
- Exploration vs. Exploitation (epsilon decay)
- Accuracy improvement across episodes

These plots are auto-generated in the notebook version.

---

## 🧩 Project Structure

```
📂 ML HACKATHON PROJECT
├── corpus.txt
├── test.txt
├── HMM_RL_Hangman.py      # Main training + evaluation script
├── Analysis_Report.docx    # Hackathon report 
├── Analysis_Report.pdf     # Same report in PDF
├── README.md               # (this file)
├── smart_q_table.pkl       # Trained Q-table
└── results/plots/          # Training plots
```

---

## ⚙️ How to Run

1. **Upload** project folder to Google Colab or your local drive.
2. **Set correct paths** for `CORPUS_PATH`, `TEST_PATH`, and `QTABLE_FILE` in the code.
3. **Run the script**:
   ```bash
   python HMM_RL_Hangman.py
   ```
4. If no pre-trained model is found, training will start automatically.
5. After training, evaluation results and final metrics will be printed.

---

## 💡 Key Observations
- Combining HMM and RL significantly improves contextual letter prediction.
- RL helps reduce repeated or random guesses by learning from previous attempts.
- Performance depends heavily on corpus diversity and training episodes.

---

## 🔍 Future Improvements
- Implement **Deep Q-Networks (DQN)** for continuous learning.
- Introduce **LSTM-based HMM** for sequence modeling.
- Improve corpus quality and include semantic embeddings (e.g., Word2Vec).

---

## 👩‍💻 Contributors
| Role | Name |
|------|------|
| **Person A** | HMM Model Design & Training |
| **Person B** | RL Agent Development & Integration |
| **Person C** | Evaluation, Plotting, and Final Report |

---

## 🏆 Deliverables

- ✅ **Working Demo**
- ✅ **HMM Construction and Training**
- ✅ **Q-Learning Environment + Agent**
- ✅ **Training and Evaluation Code**
- ✅ **Performance Metrics**
- ✅ **Plots**
- ✅ **Analysis Report (DOCX + PDF)**

---


