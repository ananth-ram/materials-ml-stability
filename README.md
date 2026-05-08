# 🔬 Machine Learning Prediction of Materials Stability

This project explores the use of machine learning to predict the thermodynamic stability of inorganic materials using data derived from the Materials Project database.

The goal is to demonstrate how simple structural and thermodynamic descriptors can capture key trends in materials stability and serve as a foundation for data-driven materials discovery.

---

## 📊 Dataset

The dataset consists of **2642 materials** obtained from the Materials Project database.

### Features used:
- Formation Energy (eV/atom)
- Energy Above Hull (eV/atom)
- Density (g/cm³)
- Volume (Å³)
- Number of atomic sites (nsites)

### Target Definition:
Material stability is defined using the energy above hull:

$$
\text{stability} =
\begin{cases}
1, & E_{\text{hull}} < 0.05 \text{ eV/atom} \\
0, & E_{\text{hull}} \ge 0.05 \text{ eV/atom}
\end{cases}
$$

### Class Distribution:
- Stable materials: **2204**
- Unstable materials: **438**

The dataset is moderately imbalanced, with a majority of stable compounds.

---

## 🤖 Methodology

The workflow consists of:

1. Data preprocessing and cleaning  
2. Feature selection using physically interpretable descriptors  
3. Binary classification based on thermodynamic stability  
4. Train-test split  
5. Model training using a Random Forest classifier  
6. Model evaluation using:
   - Accuracy  
   - Confusion matrix  
   - ROC curve (AUC)  
7. Feature importance analysis  

---

## 📈 Results

### Model Performance:
- **Accuracy:** 86.6%  
- **ROC AUC:** 0.81  

### Confusion Matrix:

|                | Predicted Unstable | Predicted Stable |
|----------------|------------------|------------------|
| **Actual Unstable** | 32               | 59               |
| **Actual Stable**   | 12               | 426              |

The model successfully identifies most stable materials but shows a tendency to misclassify some unstable materials as stable.

---

## 📉 Regression Metrics (Trend Analysis)

Although the primary task is classification, regression metrics were also evaluated:

- **MAE:** 0.566 eV/atom  
- **RMSE:** 0.735 eV/atom  
- **R²:** 0.35  

These results indicate that the model captures general trends but does not fully resolve the quantitative complexity of energy landscapes.

---

## 🔬 Feature Importance

The relative importance of features is:

**Density > Volume > Number of Sites**

### Interpretation:
- **Density** is the most important feature, reflecting the role of atomic packing and bonding strength in determining stability.  
- **Volume** captures structural and geometric effects.  
- **Number of sites** has minimal influence, suggesting system size alone is not a strong predictor.

---

## 🧠 Scientific Insight

The results highlight the interplay between thermodynamic and structural factors in determining material stability.

While energy-related quantities govern stability, structural descriptors such as density and volume introduce corrections that reflect geometric constraints and bonding environments.

The model’s tendency to overpredict stability (false positives) reflects the known challenge of distinguishing metastable phases near the convex hull, a key problem in computational materials discovery.

---

## 🎯 Conclusion

This project demonstrates that machine learning models trained on Materials Project data can effectively classify material stability using a small set of physically meaningful descriptors.

- High classification performance indicates that essential stability trends are captured.  
- Moderate regression performance highlights the need for richer feature representations.  

This work provides a foundation for applying machine learning in materials discovery and motivates the use of more advanced descriptors in future studies.

---

## 🚀 Future Work

- Incorporate compositional descriptors (electronegativity, atomic radii, etc.)  
- Use advanced featurization tools such as `matminer`  
- Apply SHAP analysis for model interpretability  
- Extend to regression tasks (e.g., band gap prediction)  

---

## ⚙️ Requirements
- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn
