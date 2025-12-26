# Local Rule-Based Explanations on German Credit Risk

This project applies LORE (Local Rule-Based Explanations) to the German Credit Risk dataset in order to generate and evaluate local explanations for black-box classification models.

The main focus of the project is the implementation and evaluation of explanation quality, with particular attention to:
- Deletion check (primary focus)
- Continuity
- Preservation

The work follows the methodological framework proposed in the original LORE paper and adapts it to a real-world credit risk use case.

---

## Project Overview

Explainable AI (XAI) methods are essential in high-stakes domains such as credit risk assessment.  
In this project, we:

1. Train a black-box classifier on the German Credit Risk dataset  
2. Generate local rule-based explanations using LORE  
3. Evaluate the explanations using established quality criteria:
   - Deletion check
   - Continuity
   - Preservation

The goal is to assess how stable, faithful, and meaningful the generated explanations are.

---

## Dataset

- **Dataset**: German Credit Risk Dataset  
- **Task**: Binary classification (credit risk assessment)
- **Features**: Numerical and categorical attributes

The dataset is stored in the `data/` folder and accessed using relative paths.

---

## Methodology

### Model
- Black-box model: Random Forest Classifier
- Preprocessing:
  - Standard scaling for numerical features
  - Ordinal encoding for categorical features
- Train/test split with stratification

### Explanation Method
- LORE (Local Rule-Based Explanation)
- Surrogate model: Decision Tree
- Neighborhood generation: Genetic algorithm

The model is wrapped using `sklearnBBox` to allow interaction with the LORE framework.

---

## Evaluation of Explanations

The project includes an explicit evaluation phase for the generated explanations:

### Deletion Check (Main Focus)
Evaluates how model predictions change when features involved in the explanation are removed or altered.  
This test measures the faithfulness of the explanation. 
We perform deletion checks by replacing feature values with randomly sampled values within the interquartile range (IQR) of the original data, ensuring realistic perturbations.

### Continuity
Assesses whether small perturbations in the input lead to consistent explanations.

### Preservation
Measures whether the explanation preserves the original model decision when applied to similar instances.

---

## References 
The explanation method and evaluation criteria implemented in this project are based on the following works:

1. Guidotti, R., Monreale, A., Ruggieri, S., Turini, F., Pedreschi, D., & Giannotti, F.  
   *Local Rule-Based Explanations of Black Box Decision Systems*.  
   IEEE Access, 2019.  
   arXiv: https://arxiv.org/abs/1805.10820  

2. Official LORE implementation:  
   https://github.com/kdd-lab/LORE_sa  

3. Guidotti, R., Monreale, A., Ruggieri, S., Turini, F., Pedreschi, D., & Giannotti, F.  
   *Stable and Actionable Explanations of Black-Box Models through Factual and Counterfactual Rules*. 
   https://link.springer.com/article/10.1007/s10618-022-00878-5 

4. Doshi-Velez, F., & Kim, B.  
   *From Anecdotal Evidence to Quantitative Evaluation Methods: A Systematic Review on Evaluating Explainable AI*.  
   arXiv: https://arxiv.org/abs/2201.08164

## License 
This project is released for academic use. 
It builds upon the LORE (Local Rule-Based Explanation) framework.  
Please refer to the original repository for the full license details:
https://github.com/kdd-lab/LORE_sa

