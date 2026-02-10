# Data Generation using Modelling and Simulation for Machine Learning

## Problem Statement
The objective of this assignment is to generate synthetic data using a simulation tool and apply machine learning models to the generated data. The aim is to compare multiple ML models using appropriate evaluation metrics and identify the best-performing model.

---

## Simulation Tool Used
The simulation tool used in this project is **SimPy**, an open-source discrete-event simulation library based on Python.  
SimPy enables modeling of real-world systems as discrete events and processes, making it suitable for queueing system simulations.

---

## System Description
A **single-server queueing system (M/M/1)** is simulated in this project.  
Such systems are commonly found in real-world scenarios such as:
- Bank service counters  
- CPU task scheduling  
- Network packet processing  

In the system, customers arrive randomly, wait in a queue if the server is busy, receive service, and then leave the system.

---

## System Parameters and Bounds

| Parameter | Description | Lower Bound | Upper Bound |
|---------|-------------|-------------|-------------|
| Arrival Rate (λ) | Rate at which customers arrive | 1 | 8 |
| Service Rate (μ) | Rate at which the server processes customers | λ + 1 | λ + 6 |
| Simulation Time (T) | Total simulation duration | 50 | 200 |

To ensure system stability, simulations were performed under conditions where the service rate was always greater than the arrival rate.

---

## Data Generation Methodology
1. Random values of arrival rate, service rate, and simulation time are generated within the defined bounds.
2. Customer arrivals are modeled using exponentially distributed inter-arrival times to correctly simulate an M/M/1 queueing system.
3. Service times are generated using an exponential distribution.
4. The simulator records the **average waiting time** for customers.
5. Gaussian noise is added to the simulation output to model real-world uncertainty.
6. This process is repeated **1000 times** to generate a synthetic dataset suitable for machine learning.

---

## Dataset Description
- **Number of simulations:** 1000  
- **Input features:**
  - Arrival rate
  - Service rate
  - Simulation time
- **Target variable:**
  - Average waiting time

---

## Machine Learning Models Used
The following regression models were trained and evaluated using the simulated dataset:
- Linear Regression  
- Decision Tree Regressor  
- Random Forest Regressor  
- K-Nearest Neighbors (KNN)  
- Support Vector Regressor (SVR)

---

## Evaluation Metrics
The models were compared using the following evaluation metrics:
- **MAE (Mean Absolute Error)**
- **RMSE (Root Mean Squared Error)**
- **R² Score (Coefficient of Determination)**

Higher R² score and lower MAE/RMSE values indicate better model performance.

---

## Results and Comparison
The performance of all models was visualized using a bar graph of R² scores.

The results show that ensemble-based models perform better on the simulated queue data.  
Among all models, **Random Forest Regressor** achieved the highest R² score, indicating superior performance in capturing the non-linear relationship between arrival rate, service rate, and average waiting time.

---

## Best Model
**Random Forest Regressor** was selected as the best-performing model due to:
- Higher prediction accuracy  
- Ability to model non-linear system behavior  
- Robust performance on noisy simulated data  

---

## Conclusion
This project demonstrates how simulation-based data generation can be effectively combined with machine learning. Using SimPy, a realistic M/M/1 queueing system was simulated to generate synthetic data. Multiple ML models were trained and evaluated on this data, and the Random Forest Regressor was found to perform best. This approach is useful in scenarios where real-world data is limited or expensive to obtain.

---

## Tools and Libraries Used
- Python  
- SimPy  
- NumPy  
- Pandas  
- Scikit-learn  
- Matplotlib  

---

## Submission
The complete implementation, including simulation, dataset generation, machine learning model comparison, and result visualization, is provided in the accompanying Google Colab notebook uploaded to this repository.
