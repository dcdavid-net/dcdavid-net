# Project: AI Bias Mitigation

**Course:** AI, Ethics, and Society (CS6603)

## **The Challenge**
Machine learning models often inherit historical biases present in training data. This project involved auditing the **Taiwan Credit Dataset** to detect and mitigate bias in creditworthiness predictions. The specific focus was on how the model treated protected classes, specifically **Gender** (Male vs. Female) and **Age**.

## **The Approach**
### 1. Detection
I utilized the **AI Fairness 360 (AIF360)** toolkit to calculate key fairness metrics:
* **Disparate Impact**: Assessing the ratio of favorable outcomes (loan approval) between privileged (Male) and unprivileged (Female) groups.
* **Statistical Parity Difference**: Measuring the difference in favorable outcome probabilities.

### 2. Mitigation (Reweighing)
Instead of modifying the model itself, I applied a **Pre-processing** technique called **Reweighing**.
* This algorithm assigns weights to training examples to ensure that the protected attributes (e.g., Female) are independent of the class label (Creditworthy/Not Creditworthy) before training begins.
* This creates a "fair" dataset where privileged and unprivileged groups have equal base rates of favorable outcomes.

## **The Results**
* **Before Mitigation**: The initial model showed bias favoring the privileged group.
* **After Mitigation**: By applying the Reweighing algorithm, I successfully improved the **Disparate Impact** metric for Gender from **~0.79** to **1.0** (indicating perfect fairness).
* **Trade-offs**: While fairness improved for Gender, the "Age" attribute saw slight shifts in fairness metrics, highlighting the complexity of intersectionality in bias mitigation—fixing one bias can sometimes inadvertently impact another.