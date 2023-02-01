# Dacon_Machine-Sound-Outlier-Detection
Outlier detection through mechanical sound

## Intro
Determining whether a fan is out of order through unsupervised learning from normal data __(Unsupervised Anomaly Detection)__

## Approach

- Use mean vector of Mel spectrogram and MFCC as input

- Using TSNE to identify differences in data distribution according to type

- __ABOD__

It measures the outlierness of a data point by the angles between the data point and its nearest neighbors. The idea behind ABOD is that outliers will have significantly different angles to their nearest neighbors compared to non-outlier data points, and thus can be detected based on these angles. 

- __Deep-SVDD__

Unlike Kernel-based SVDD, it learns a feature space based on deep learning and finds an optimal sphere (with a small radius) surrounding normal data in that feature space. Then, outliers are detected based on the boundary

## Data preprocessing

- Mel spectrogram of Normal Data
![image]()

<p align="center"><img width="1200" alt="image" src=https://user-images.githubusercontent.com/76990589/216073463-58eee024-6253-40af-b858-6f0579a00989.png>
<p align="center"><img width="1200" alt="image" src=https://user-images.githubusercontent.com/76990589/215993285-7c4943f0-ecea-4ec5-9f0f-e776ca929207.png>
<p align="center"><img width="1200" alt="image" src=https://user-images.githubusercontent.com/76990589/215993732-87605dc6-e875-456f-8068-220f105d4bdc.png>

- MFCC of Normal Data
<p align="center"><img width="1200" alt="image" src=https://user-images.githubusercontent.com/76990589/215995667-3507754d-44c0-46c2-b5c2-f6bf9487d38e.png>
<p align="center"><img width="1200" alt="image" src=https://user-images.githubusercontent.com/76990589/215995729-c29c019e-d1a0-48f9-8532-a7dee91535c7.png>
<p align="center"><img width="1200" alt="image" src=https://user-images.githubusercontent.com/76990589/215995777-4da67d6a-e4bf-432f-b73d-19ab6e7fb890.png>

## Models

- Angle Based Outlier Detection (ABOD) : [Angle-Based Outlier Detection in High-dimensional Data](https://www.dbs.ifi.lmu.de/~zimek/publications/KDD2008/KDD08-ABOD.pdf)

- Deep-SVDD : [Deep One-Class Classification](http://proceedings.mlr.press/v80/ruff18a/ruff18a.pdf)

## Result

