# Energy Efficiency of Residential Buildings

## Project Overview
This project analyzes how residential building characteristics impact energy efficiency, measured through **heating and cooling loads**. By examining factors such as building **size, orientation, glazing area, and compactness**, we aim to identify the most energy-efficient design features.

## Objectives
- Identify design characteristics that significantly impact heating and cooling loads.
- Develop predictive models for estimating energy consumption based on building attributes.
- Compare findings with existing literature and provide actionable insights for architects and builders.

## Dataset
The dataset originates from **Tsanas and Xifara's** study on energy performance estimation using **statistical machine learning tools**. Buildings were simulated in **Ecotect**, assuming a standard volume (771.75m³) and occupancy (7 people) in **Athens, Greece**.

### **Key Variables:**
#### **Input (X) Variables**
| ID  | Variable Name             | Type          | Notes |
|-----|---------------------------|--------------|--------|
| X1  | Relative Compactness      | Continuous   | Influences energy retention |
| X2  | Surface Area              | Continuous   | Removed due to redundancy |
| X3  | Wall Area                 | Continuous   | Affects insulation |
| X4  | Roof Area                 | Continuous   | Affects heat absorption |
| X5  | Overall Height            | Continuous   | Single-story (3.5m) & two-story (7m) |
| X6  | Orientation               | Nominal      | North, East, South, West |
| X7  | Glazing Area              | Continuous   | 0%, 10%, 25%, 40% |
| X8  | Glazing Distribution      | Nominal      | 0 = No glazing, 1-5 = Various distributions |

#### **Output (Y) Variables**
- **Y1 (Heating Load) [Continuous]**
- **Y2 (Cooling Load) [Continuous]**

## **Methodology**
### **1. Data Analysis & Initial Observations**
- **Heating and cooling loads** are strongly correlated.
- **Building orientation** has little impact on energy loads.
- **Compact buildings** are more energy-efficient than sprawling structures.

### **2. Clustering Analysis**
Using **K-Means Clustering (K=3)**, we classified buildings into:
1. **Cluster 1**: Single-story, low energy consumption.
2. **Cluster 2**: Compact two-story, moderate energy consumption.
3. **Cluster 3**: Less compact two-story, high energy consumption.

### **3. Regression Analysis**
#### **Heating Load Model:**
Key predictors:
- **Glazing Area (+)** → Higher glazing increases heating load.
- **Overall Height (+)** → Taller buildings require more heating.
- **Relative Compactness (-)** → More compact buildings lose less heat.
- **Roof & Wall Area (-)** → More insulated surfaces reduce heating load.

**Formula:**
```math
Y_1 = 84.775 + 16.848(X_7) + 4.170(X_5) - 64.773(X_1) - 0.027(X_4) - 0.175(X_3)
```

#### **Cooling Load Model:**
Key predictors:
- **Glazing Area (+)** → More glass increases cooling needs.
- **Overall Height (+)** → Taller buildings trap more heat.
- **Relative Compactness (-)** → Compact buildings have lower cooling loads.

**Formula:**
```math
Y_2 = 97.931 + 13.253(X_7) + 4.284(X_5) - 70.788(X_1) - 0.176(X_4) - 0.044(X_3)
```

## **Key Insights & Recommendations**
- **Most significant factors**: **Height and glazing area** strongly influence energy loads.
- **Compact buildings**: Reduce energy usage significantly.
- **Optimized glazing**: Proper window placement reduces cooling/heating demands.
- **Trade-offs**: High glazing increases **cooling load**, but better insulation can offset this.

## **Implementation**
### **1. Dependencies**
To run the analysis, install the necessary Python libraries:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

### **2. Running the Model**
Clone the repository and execute the script:
```bash
git clone <repo_url>
cd energy-efficiency
python analysis.py
```

## **Future Work**
- **Incorporate real-world datasets** to validate findings.
- **Expand analysis** to include material properties and insulation types.
- **Develop an interactive tool** for architects to estimate energy efficiency.

## **References**
- **Burdick, Arlan.** Strategy Guideline: Accurate Heating and Cooling Load Calculations, U.S. DOE, 2011.
- **Tsanas, Athanasios & Xifara, Angeliki.** Accurate Quantitative Estimation of Energy Performance of Residential Buildings, Energy and Buildings, 2012.

---

