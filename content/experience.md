---
title: Experience
date: 2024-06-10
hide_date: true
reading_time: false
---

My journey in academia and the tech industry so far.

{{< toc mobile_only=true is_open=true >}}

### Applied Research Intern
**<span style="color: #ADD8E6;">Big Vision LLC</span>**<br>
May 2023 - Aug 2023 · San Diego, California

My project was to deliver a robust OCR tool to sports coaching agency to digitize statistics and strategies for their record-keeping. I was supervised by the VP of Technology, Mr. Pranav Mishra, and reported to the COO.

Tasks

- Fine-tuned PaddleOCR improving English OCR inference to >99% accuracy, 15% better readability for sports strategies. Overcame the initial accuracy bottleneck of about 85% by iterative training runs. The next iterative run included augmented data and hard negatives to enhance overall training generalization and improved inference.
- Pioneered fine-tuning of PaddleStructure for machine-readability of text structures, like lists, tables etc., and reached 90% accuracy. Included additional finetuning of PaddleStructure for arrows specifically, as arrows are crucial for sports coaching strategies.
- Initial research included surveying and benchmarking various OCR frameworks including but not limited to Tesseract, Amazon Textract etc.
- Developed an annotation tool to correct bounding boxes and/or labellings after the initial run of an OCR over the dataset to improve quality of the dataset labels.

### Research Intern
**<span style="color: #ADD8E6;">Clemson University</span>**<br>
May 2021 - Jan 2022 · Clemson, South Carolina (Remote)

This role allowed me to pursue interdisciplinary research for Environmental Sciences and Computer Science to estimate soil moisture at various depths and high resolutions. It helped me realize my aim to develop ML models for sustainable practices. I was supervised by Professor Ashok Mishra. 

Tasks 

- Developed an LSTM model to estimate soil moisture, reducing RMSE loss by <4% from the previous best algorithm of XGBoost. This LSTM model could run training and inference in parallel using batch processing, for soil moisture estimation at multiple depths.
- Due to LSTM's ability to capture patterns in sequential data, this model could estimate soil moisture at any of the 5 depth levels studied at a spatial resolution of 1 sq km and temporal resolution of 1 day. The estimation accuracy was >90% for an error margin of 5%.
- This project helped several collaborating meteorological agencies who provided the initial datasets at much farther spatial resolutions. It reduced the cost of installation for area-wise denser/more soil moisture sensors.

### Quantitative Research Intern
**<span style="color: #ADD8E6;">Torch Investment Group</span>**<br>
Jun 2021 - Oct 2021 · Singapore (Remote)

My experience in this internship helped me learn the maths for financial analysis and utilizing ML models to understand better investment or trading strategies.

- Refined Light-GBM and RNN models to predict annual stock returns, surpassing previous best model performance of XGBoost by ∼5%
- Formulated a CAGR(Compound Annual Growth Rate)-based investment algorithm focusing on the intrinsic value of stocks. This metric of undervalued/overvalued stocks yielded over a 10% increase in annual returns across an investment portfolio of 30 stocks

### Machine Learning Intern
**<span style="color: #ADD8E6;">Tech Mahindra</span>**<br>
May 2020 - Jul 2020 · Pune, India

I got the opportunity to work at Tech Mahindra's esteemed innovation cell, the Makers Lab. This project allowed minimal staffing at offices during COVID lockdowns to allow for smooth running of systems.

- Trained a YOLOv4 model from the ground-up to detect unmasked faces and monitor COVID protocols in workplaces, with >85% accuracy in violation detection
- Integrated above mask detection model and a vision model to measure the distance between two people for social distancing with a Django UI
- Implemented a parallel Real-Time Streaming Protocol across all the office CCTV cameras to alert alarms upon detecting COVID protocol violations in the workplace.
- For initial work, had to curate a sizeable 10,000+ image dataset of people wearing COVID masks properly and otherwise