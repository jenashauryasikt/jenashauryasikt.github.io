---
title: 'Simplified Overview of Cognitive Load Estimation Using Machine Learning'
summary: 'Estimating cognitive load is crucial for human-computer interaction applications, such as autonomous vehicles and medical devices, as it enhances their functionality and user experience significantly.'
date: 2024-06-10
authors:
  - admin
tags:
  - Projects
image:
  caption:
---

{{< toc mobile_only=true is_open=true >}}

### 1. Cognitive Load

Cognitive load refers to the mental effort required to perform a task. High cognitive load can lead to errors and decreased performance, while low cognitive load can indicate underutilization of cognitive resources. Estimating cognitive load helps in creating systems that respond dynamically to the user’s mental state, improving overall efficiency and user satisfaction.

Understanding cognitive load is crucial for improving human-computer interaction (HCI) applications. By estimating cognitive load, systems can adapt to user needs, enhancing experiences in areas like autonomous vehicles, medical devices, and intelligent tutoring. 

#### 1.1 Why Estimate Cognitive Load?

- Enhanced User Experience: Adapting interfaces based on cognitive load can reduce user frustration and increase productivity.
- Safety and Efficiency: In critical applications like driving or operating machinery, monitoring cognitive load can prevent accidents caused by cognitive overload.
- Personalized Learning: Intelligent tutoring systems can adjust difficulty levels based on the learner’s cognitive load, optimizing the learning process.

### 2. Data Collection and Preprocessing

The dataset, CogLoad2020, includes physiological measurements from 23 participants performing cognitive tasks of varying difficulty levels. The data is preprocessed using the following steps:

1. Sampling Rate: Measurements are taken at a 1Hz sampling rate.
2. Time Windows: Data is segmented into 30-second windows for analysis.
3. Feature Extraction: Simple aggregate statistics such as mean, standard deviation, and skewness are calculated for each physiological signal within the time window.

The model uses four physiological indicators to estimate cognitive load:

1. Heart Rate (HR): The number of heartbeats per minute.
2. Skin Conductance (SC): Measures sweat gland activity, which varies with stress and cognitive load.
3. R-R Intervals: The time intervals between successive R-waves of the QRS signal on an electrocardiogram.
4. Skin Temperature (ST): Changes in skin temperature can reflect emotional and cognitive states.

### 3. ML Modeling

The dataset is divided into an 80:20 ratio for training and validation.

#### 3.1 Baseline

![img 1](images/1.png "Fig. 1 Baseline model pipeline for feature engineering and ensemble learning")

[(Borisov, 2021)](https://pdf.sciencedirectassets.com/776616/1-s2.0-S2451958821X00024/1-s2.0-S2451958821000646/main.pdf?X-Amz-Security-Token=IQoJb3JpZ2luX2VjEDkaCXVzLWVhc3QtMSJHMEUCIGz7DwIHxdD56%2FFN0AGLyabgPJzA3ehNAujNPU%2FIqUnfAiEA7FpVvYQvPyab1sO%2BwtNRR5CUPVbDY%2BYL81Up6zFJyn8qvAUI0v%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FARAFGgwwNTkwMDM1NDY4NjUiDB9%2BgW8nVQfa3eoq7SqQBcq8D0vPx%2BHHhv497oOxSHT4FL07R1HmomTHdqI3vv%2FXumdGbRCxNoAJAl%2BOuR746C43YAoonSptCeeuhhd7k%2FECdMzJ0iBSH4iWp%2BRXLVDWEcJWtP%2FCamg1TTxQWroKbbJ5QVmHHkDaY7VFRq2S9UE%2BTDH9M5zw86KtpXESedmVOOqoqMVntwhTGEleTha%2FfEGmRO9J4xEW%2FC9cdw0SMJzLfT2ok0aLyByM5Bq6kAhXhRUbEtBMWtWUuiWBwNTxJmHpmOCapMfUI7iWeg%2BzHgFzVQX7JHH%2FA0ju76xk1jvsjVNwAE0UNf24AHNcTmsgL%2BE%2BUYDhYMJmj4dQf7WbcQb3OZxzakBQ4iHArzvq%2FJOiZGRRXUxlrhvg5YTUSukaPEcLpPVGCF6gtd4pI%2F65xx3%2FAO9q7oa9aAkI%2FOYfrMf%2BzL3VlQLs6zaoD11dSuL1SFe%2FLOeWvibd3yB6c82kyd749aD3c4L2yNrCkSQFPdtAXI6vqmPN3TD8FWJNnSTdw98RN4TJ4ptaZ9kG3ZyyAROHGcCcTeQNH8Iw3aEwCvjK33Q5dNlR61OTRs4NdHsKlcxa4hlcrLwYZM7BJ1iUJgJsERAapBOm3vkQu23dE38xNVJZhHcdgsoYOpEeQBLyp1IoOoWx1k0JLo9sq0tzSCfYoX%2BCDYPtetuO6wQ3OZgs%2FD4lkjzp1PoyF%2BWx1a5GMxzQLwayAnaOFOXvUhhzG6YphJ0sS1iFrw2x%2FnhZ9i4QLF6sWEqqtyzjPviDuJkcJ59iZVl0ycigRxLfYyIYfyNruH5PVhZE%2FjUeMz31Zuom2%2Fhe2QZL4qxbgFehAWkNZpxG6ZF%2BL1wJP56Zk%2FiRWh60k71Ii%2Bdz3Vsj%2FH4mU9xBML3CurMGOrEBYpi4V0fu8zePEdJ0j2mNtJqlg82l5zPdoTC2kEBqe1s2Ln8tDOt1uvL5KIDmaPYvz77ONo5cro%2Ff2vYBZUAvl9KTqNZSD7I3hrZFRiX1f30hqSrZrxWPOFHJBpybhn%2BN3SN%2Bl680pPsgawSQUFM9t%2Fr5llGY9bRQ%2FgcjjN2PE%2BeO9G%2BBM3vyDIn4DK5Xuz5lgiLYTN0cX5b%2B2eChNsRA8Zd5DjCcnl9LepEVAEKOJXjg&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20240616T093526Z&X-Amz-SignedHeaders=host&X-Amz-Expires=300&X-Amz-Credential=ASIAQ3PHCVTYTJD2U7OI%2F20240616%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Signature=0a863efdb494cecd1f4ebbc70c820348b532689fb340b6c4c259ebec3d6c7574&hash=763300db21aa8f9987479adb79c9dbbfe6c2a25bc755b2cf36b1e100817bec3b&host=68042c943591013ac2b2430a89b270f6af2c76d8dfd086a07176afe7c76c2c61&pii=S2451958821000646&tid=spdf-31e8e7ed-98a1-40be-8877-ff9323200f82&sid=338a69548ab1c740312bdf92790f9dcd99bdgxrqa&type=client&tsoh=d3d3LnNjaWVuY2VkaXJlY3QuY29t&ua=13175756535f0d095700&rr=8949cf4aca780fb7&cc=us) The baseline model uses an ensemble of 8 GBDT models based on LightGBM, optimized with random search and Bayesian algorithms. Despite testing more models, the final meta-model averages these 8 models, achieving an accuracy of 62.5%.

#### 3.2 Experiments

Several machine learning models were tested to estimate cognitive load - Gaussian Naive Bayes (GNB), K-Nearest Neighbors (KNN), Support Vector Machines (SVM), and Neural Networks (NN). The NN model outperformed other methods in estimating cognitive load. The architecture includes a single hidden layer with ReLU activation functions. The Adam optimizer is used with an initial learning rate of 0.001 and the NN is trained for a maximum of 300 epochs on a CPU.

Key NN performance metrics include:
- Accuracy: 67.71%
- ROC-AUC: 65.81%
- F1-Score: 68%

### Conclusion

The neural network model achieved a 5.2% improvement over the baseline model in estimating cognitive load. Future work includes collecting more data and exploring deeper neural network architectures to further enhance accuracy.

The project report can be found [here](CognitiveLoad_NN.pdf)