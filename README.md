# ✈️ Aircraft Trajectory Prediction using K-Means & BiLSTM

## 📌 Project Overview
This project proposes a **hybrid learning approach** using **trajectory clustering (K-Means)** and **Bidirectional Long Short-Term Memory (BiLSTM)** to predict aircraft trajectories, aiming to enhance light predictability, reduce congestion and improve safety. As a **proof of concept**, it demonstrates the potential for acurately predicting other flight parameters.

## 🚀 **Key Highlights:**
- **150+ real flight trajectories** from Duluth (DLH) to Minneapolis (MSP) analyzed.
- **K-Means clustering** grouped similar flight and approach paths for improved accuracy.
- **BiLSTM model** accurately predicts future trajectory points until flight concludes.
- **Clustering improved accuracy by 15% (latitude) & 10.5% (longitude).**

## 📊 Methods
1. **Data Collection:** Flight Data Monitoring (FDM) data from Boeing 747-300.
2. **Preprocessing:** Data cleansing, feature selection, resampling, normalization
3. **Clustering:** K-Means applied to segment trajectories.
4. **Deep Learning Model:** BiLSTM trained on clustered and unclustered flight paths. 
5. **Evaluation:** RMSE, MAE, and variance comparison.

## 📈 Results
- Clustered BiLSTM outperforms unclustered models.  
- RMSE values indicate **high prediction accuracy**.  
- Potential applications in **air traffic management & automation**.

---


## ⚙️ **How It Works**

### **⚠️Scope and Limitations**
1. Data used is strictly from a **747-300 flying from DLH to runway 30R and 12L of MSP airports**.
2. Clustering is done only based on **latitude and longitude**.
3. Deep learning model is limited to only considering the following features: **Time, latitude, longitude, altitude, groundspeed, and heading**.
4. Trajectories are analyzed purely in a **simplified 2D space**, focusing on path and trajectory, without considering flight dynamics or aerodynamic factors.


### **1️⃣ Data Collection**
- 3000+ encrypted real flight data all across North America obtained from NASA's **Flight Data Monitoring (FDM)**
- 159 data of flights from Duluth (DLH) to Minneapolis (MSP) were selected
- Features used: **Time, Latitude, Longitude, Altitude, Speed, Heading**.

### **2️⃣ Preprocessing**
1. **Data Cleansing and Visualization**
   - After inaccurate flight data are removed, the remaining data had their sampling rate standardized to ensure a dynamic and continuous flight data. Finished flight data is visualized using the open-source GIS software qGis.
2. **Temporal Alignment and Resampling**
   - To make sure all flight data has identical amount of data samples, their timestep was aligned and resampled with interpolation and decimation. Eventually, the features are scaled and feature vectors are created.
3. **Dimensionality Reduction**
   - To make sure all flight data has identical amount of data samples, their timestep was aligned and resampled with interpolation and decimation. Eventually, the features are scaled and feature vectors are created.

### **3️⃣ Clustering (K-Means)**
1. **Determining K Value**
   - The optimal K value was determined using ta combination of the elbow method, silhouette score, and a heuristic approach, resulting in K = 3.
2. **Clustering Result & Performance**
   - The clustering performance was calculated by measuring how tightly the data points within a cluster are packed together. A lower intra-cluster variance indicates a well-defined cluster.

### **4️⃣ Deep Learning Model (BiLSTM)**
  **BiLSTM Modeling**
  
Six BiLSTM models will be trained, one per cluster, alongside a model using unclustered data to assess clustering's impact. Each model follows an 80/20 train-test split, with one flight reserved for validation. In order to prevent the model from over-fitting during training, the training set was randomized. Hyperparameter tuning is done individually for each cluster model.

  **Architecture:**  
  - Input: time, latitude, longitude, altitude, groundspeed, and heading  
  - Hidden Layers: 128 layers + dropout  
  - Output: Predicted flight position
- **Training:** RMSE & MAE used for loss function.

### **5️⃣ Prediction Results**


### **56️⃣ Evaluation Metrics**
| Model  | RMSE (Latitude) | RMSE (Longitude) |
|--------|---------------|----------------|
| No Clustering | 0.032 | 0.045 |
| K-Means + BiLSTM | **0.027** (⬇️15%) | **0.040** (⬇️10.5%) |

  

📜 **Full Report:** [Here](https://drive.google.com/file/d/1nF59ecE_myQGnDGz8YoO0U8VUmj-UlSf/view?usp=sharing) [and here!](https://drive.google.com/file/d/1Bd1hm8-zfEX9zlucOQ9zgSEgrZIrxmee/view?usp=sharing)
🎤 **Presentation Slides:** [Here!](https://drive.google.com/file/d/1lWnlXLm6o-WbvtOeQkxjwZq7iYxnnYwz/view?usp=drive_link)  
📝 **Notebooks & Code:** Available in the report (SOON in the repository!)  
