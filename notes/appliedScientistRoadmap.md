# First: What “Applied Scientist” REALLY means in Big Tech

### An Applied Scientist is not:
- just training models
- just writing PyTorch
- just reading papers

### An Applied Scientist is:
- **someone who formulates problems mathematically**
- **chooses the right modeling assumptions**
- **understands why a model works / fails**
- **connects theory → production constraints**
- **can defend design choices**

> **This is why interviews go deep.**

## 🧠 CORE EXPECTATION STACK (Big Tech)
**Math Foundations**
   ↓
**Statistical ML**
   ↓
**Modern ML / DL**
   ↓
**Optimization & Generalization**
   ↓
**ML Systems & Production**
   ↓
**Research Thinking**

---

## 🧱 LAYER 1: Math Foundations (NON-NEGOTIABLE)
> **This is where Applied Scientist interviews separate people.**

### 1️⃣ Probability & Statistics (VERY DEEP)
*You must reason, not recall formulas.*

**Must-master concepts**
- Random variables (discrete vs continuous)
- Joint / conditional distributions
- Bayes theorem (intuitive + formal)
- Expectation, variance
- Covariance, correlation
- Law of large numbers
- Central limit theorem

**In-depth topics**
- Maximum Likelihood Estimation (MLE)
- Maximum A Posteriori (MAP)
- Bias–variance tradeoff (formal)
- Hypothesis testing
- Confidence intervals
- p-values (and their misuse)

> 👉 **You should be able to derive MLE for common models.**

### 2️⃣ Linear Algebra (Model-Level Understanding)
*Not just “I know matrices”.*

**Must know**
- Vector spaces
- Eigenvalues / eigenvectors
- Rank, null space
- Orthogonality
- SVD (VERY important)

**In-depth**
- Why PCA = eigenvectors of covariance
- Geometry of linear models
- Conditioning & numerical stability

### 3️⃣ Optimization
*Interviewers LOVE this.*

**Core**
- Gradient descent
- Convex vs non-convex
- Local vs global minima

**Deep**
- SGD vs batch GD
- Momentum
- Adam vs RMSProp
- Learning rate schedules
- Why deep nets still converge (intuition)

---

## 📊 LAYER 2: Classical Statistical ML (Applied Scientist FAVORITE)
> **You MUST know these deeply, not superficially.**

### Models you must MASTER
- Linear regression
- Logistic regression
- Naive Bayes
- k-NN
- SVM
- Decision Trees
- Random Forest
- Gradient Boosting

### For EACH model, know:
- **Assumptions**
- **Loss function**
- **Optimization method**
- **When it fails**
- **Bias vs variance behavior**
- **Interpretability**

> **If asked: “Why not use XGBoost here?”**
> **You must justify, not guess.**

---

## 🤖 LAYER 3: Deep Learning (Conceptual Depth > Tricks)

### Core Architectures
- MLP
- CNN
- RNN
- LSTM / GRU
- Transformers

### In-depth understanding
- Why attention works
- Vanishing gradients
- Initialization
- Regularization (dropout, weight decay)
- Overfitting in deep nets
- Representation learning

### Training-level depth
- Loss landscapes
- Batch size effects
- Gradient noise
- Early stopping

> **You should be able to debug training failures mentally.**

---

## 📉 LAYER 4: Evaluation, Generalization & Failure Modes
> **This is pure Applied Scientist territory.**

### Must-know
- Train/val/test leakage
- Overfitting vs underfitting
- Cross-validation
- ROC vs PR curves
- Precision/Recall trade-offs

### Deep concepts
- Distribution shift
- Covariate shift
- Concept drift
- Label noise
- Imbalanced datasets

> **If model accuracy drops in prod → YOU diagnose why.**

---

## 🧠 LAYER 5: ML Systems (Big Tech Cares A LOT)
> **Applied Scientists are NOT isolated researchers.**

### Must know
- Offline vs online training
- Batch vs real-time inference
- Feature pipelines
- Data versioning
- Model versioning

### Deep
- Training–serving skew
- Feature leakage
- Model monitoring
- A/B testing models
- Shadow deployment

> **Interview question: “How would you deploy this model safely?”**

---

## 🧪 LAYER 6: Research Thinking (THIS IS THE DIFFERENTIATOR)

### You will be asked questions like:
- Why does this work?
- What assumption are you making?
- What happens if assumption breaks?

### You must be comfortable with:
- Reading papers
- Re-deriving equations
- Questioning baselines
- Designing ablations

> **Even if role is “applied”, research mindset is tested.**

---

## 🧰 Tools (Depth ≠ Framework Count)
*You don’t need 20 tools. You need clarity.*

**Expected familiarity**
- Python (NumPy, SciPy)
- PyTorch or TensorFlow
- Pandas
- Sklearn
- Some distributed training idea

> **Frameworks are secondary to thinking.**

---

## 🧭 INTERVIEW PATTERN (Very Important)
**Big tech Applied Scientist interviews usually include:**

1. **Math / probability deep dive**
2. **ML theory + intuition**
3. **Model selection reasoning**
4. **Failure diagnosis**
5. **Applied system question**
6. **Past project deep dive**

> **They WILL push until you say: “I don’t know, but here’s how I’d find out”**
> *That’s okay — hand-wavy answers are not.*

---

## 🗺️ PRACTICAL ROADMAP FOR YOU

### Phase 1 (0–3 months)
- Probability + Linear Algebra refresh
- Classical ML (deep understanding)
- Re-derive common models

### Phase 2 (3–6 months)
- Deep learning fundamentals
- Optimization theory
- Evaluation & generalization

### Phase 3 (6–9 months)
- ML systems
- End-to-end ML project
- Paper reading + reproduction

---

## ⚠️ Reality Check (Honest)
> **To switch SDE → Applied Scientist in big tech:**
> - You must **outthink**, not out-code
> - Interviews are **harder** than SDE
> - **Depth** matters more than breadth
> - But with your ML background + systems exposure at Amazon, you’re actually in a **strong position**.

---

## 🎯 One grounding question (answer this next 👇):
**Why does logistic regression use log-loss instead of MSE, and what breaks if you use MSE?**

> **If you can answer this cleanly → you’re already entering Applied Scientist territory.**