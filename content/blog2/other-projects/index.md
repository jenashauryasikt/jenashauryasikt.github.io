---
title: Other Projects
summary: 
date: 2024-06-10
authors:
  - admin
tags:
  - Projects
image:
  caption:
---

{{< toc mobile_only=true is_open=true >}}

### [1. Unsupervised Generative ML Models](https://github.com/jenashauryasikt/Unsupervised-Generative-ML-Models)
- Conducted comprehensive evaluation of 4 unsupervised generative models in JAX
  - Energy Based Models (EBM)
  - Denoising Score Matching (DSM)
  - Denoising Diffusion Probabilistic Model (DDPM)
  - Generative Adversarial Networks (GAN)
- Multiple 2D datasets were used to evaluate generalized model performances
  - Checkerboard
  - Gaussian Mixtures
  - Pinwheel
  - Spiral
- GAN showed the best generations with the best mean KDE (-1.34) across all datasets. However, I could not realize the potential of GANs to act as the best generators. To that end, adding batch-normalization layers to the genera- tor and discriminator MLPs would have helped to capture more variance but my system compatibility with jax prevented me from such.
- The report can be found [here](Unsupervised.pdf).

### [2. NBA-Draft-Prediction](https://github.com/jenashauryasikt/NBA-Draft-Prediction)
- Benchmarked several ML models like RBF Regression, SVMs, Neural Networks, KNN to predict NBA players’ performance and draft pick in next season, based on demographic or statistical attributes. KNN reached a best of 0.8 R2 score.
- The report can be found [here](ShauryasiktJena_Project_NBA_Report.pdf).

### [3. Parallel Low-Latency Automated Trading System](https://github.com/jenashauryasikt/EE451-Project)
- Parallelized trade orders for NASDAQ stocks of 30 companies over a market day using PThreads in C++
- Reduced latency from 200ms in a linear system to 30ms, increased profits 40-fold by higher trading frequency
- The report can be found [here](TradingSystemParallel.pdf).

### [4. Course Web-Registration System by Socket Programming](https://github.com/jenashauryasikt/Course-Registration-Backend)
- Built backend of a university’s course registration system in C++ across multiple department servers, a main server,
and a client platform with dedicated TCP and UDP ports capable of handling multiple queries, with 0 error rate.

### [5. Load-Carrying Mule Bot for Supermarket Customers](https://github.com/jenashauryasikt/IITDelhi-Design-Systems-Laboratory/tree/main/Experiment%202-Communicatong%20Mule%20Bots)
- Headed team of 40 students in designing a trolley to follow customers via Bluetooth & GPS, and carry their supplies
- Planned installation of WiFi modules enabling P2P communication for optimal routing and sharing charging ports
- The report can be found [here](MuleBot.pdf).