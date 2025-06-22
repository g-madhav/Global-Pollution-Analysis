## **1. Objective**

To explore global pollution data and uncover patterns related to energy recovery using association rule mining (Apriori algorithm).

---

## **2. Methodology**

### **2.1 Data Preprocessing**

- **Missing Values:** Rows with nulls were dropped for clean model input.
- **Normalization:** Scaled pollution indices (Air, Water, Soil) to a [0,1] range using `MinMaxScaler`.
- **Label Encoding:** Converted categorical variables like *Country* and *Year* to numerical codes.
- **Categorical Derivation:**
    - Derived pollution severity levels (Low, Medium, High) using threshold bins on normalized indices.
    - Created a binary feature `High_Energy_Recovery` using the median of `Energy_Recovered (in GWh)`.

---

### **2.2 Association Rule Mining (Apriori Algorithm)**

- **Approach:**
    - One-hot encoded categorical pollution levels and appended `High_Energy_Recovery` as a binary target.
    - Applied the Apriori algorithm to identify frequent itemsets with a support threshold of 0.1.
    - Extracted rules using confidence ≥ 0.5 and lift > 1 for interpretability and significance.
- **Output:**
    - Generated strong association rules indicating conditions under which high energy recovery is likely.
    - Constructed bar plots and a network graph for rule visualization.

---

## **3. Model Evaluation**

### **Association Rules Evaluation**

- **Top Rules:**
    - Found rules such as:
        - `{'High'} in Air Pollution` → `High Energy Recovery`
        - `{'High'} in Soil Pollution` ∧ `{'Medium'} in Water Pollution` → `High Energy Recovery`
- **Lift Values:** All top rules had lift > 1, confirming positive association strength.
- **Network Visualization:** Provided a visual representation of the interdependence of variables.

---

## **4. Key Findings**

1. **Pollution Severity Matters:**
    - High Air or Soil Pollution levels are frequently associated with High Energy Recovery initiatives.
2. **Rule Strength:**
    - Top rules demonstrated strong support and lift, indicating meaningful relationships.
