# The Price of a Home… and the Cost of Bias

##  Overview

In this project, I explore a critical question: **Can a machine learning model be accurate, yet still unfair?**

Using the classic **Boston Housing dataset**, I audit different regression models to uncover how bias can hide in plain sight, especially when sensitive features are involved.

## Motivation

After reading **Unmasking AI**, a powerful book that reveals how racial bias can creep into algorithms, I began to wonder:
- What if the data I train on reflects historical injustice?  
- And what if our models unknowingly learn to repeat it?

This project was born out of that question. It’s an effort to not only build predictive models, but to interrogate their fairness.

##  Dataset: Boston Housing

I use the Boston Housing dataset, a widely used dataset in ML education and experimentation. It contains features like:

- `RM` - Average number of rooms
- `DIS` - Distance to employment centers
- `PTRATIO` - Pupil-teacher ratio

And one controversial feature:

- **`B`** -  A proxy for racial composition, based on the percentage of Black residents.

This feature, though often overlooked, carries the Iight of historical segregation and I aim to explore its effect.

##  Tools & Libraries

- **Python**
- **Pandas / NumPy / Scikit-learn** – for preprocessing and modeling
- **Dalex** – for in-depth **fairness auditing**
- **Matplotlib / Seaborn** – for visualization

##  Models Tested

- `Linear Regression`
- `Decision Tree`
- `Random Forest`
- `XGBoost Regressor`

Each model was trained on preprocessed data and evaluated for:

- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)
- R² Score
- **Fairness metrics via Dalex**

## Fairness Auditing

I tested models against **three fairness conditions**:

1. **Independence** – Are predictions influenced by race?
2. **Separation** – Are errors uneven across racial groups?
3. **Sufficiency** – Can I trust predictions equally for everyone?

Dalex was used to compute fairness scores using **Direct Density Ratio Estimation (DDRE)**.

##  Results Summary

| Model               | Accuracy (RMSE) | Fair? | Failed Metric    |
|---------------------|-----------------|--------|------------------|
| Linear Regression   | 4.92             | ❌     | Independence     |
| Decision Tree       | 3.09             | ✅     | —                |
| Random Forest       | 2.95             | ✅     | —                |
| XGBoost Regressor   | 2.56             | ❌     | Separation       |

**Insight:** 
- Even high-performing models (like XGBoost) can fail fairness tests.  
- Fairness isn't a given, it must be **audited**.


##  Key Takeaways


- High accuracy doesn't guarantee fairness.
- Even strong-performing models like XGBoost can still show bias against certain groups.
- Linear Regression, despite its simplicity, failed the independence test, showing its predictions were influenced by sensitive features.
- Decision Tree and Random Forest models emerged as both accurate and fair, making them more trustworthy for real-world use.


## Final Thought

**A fair model shouldn't just be good at predicting,  it should also be good for people.**


## Installation and Setup

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/johnjoel2001/XAI-Project.git
   cd XAI-Project
   ```
2. Run the main.ipynb
3. The requirements are listed in the first cell.


## Notes & References

1) AI Tools Ire not used in this Project.

2) [Conditional Metrics for Fairness in Machine Learning (arXiv)](https://arxiv.org/pdf/2001.06089)

3) [Dalex Official Documentation](https://dalex.drwhy.ai/)


