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

- __Mel spectrogram and MFCC__ of Normal Data

<p align="center"><img width="1200" alt="image" src=https://user-images.githubusercontent.com/76990589/216074210-a5bc6e18-d6d2-4e6e-888e-f67d3ab2b21a.png>

- __Data distribution by Fan type__
  
<p align="center"><img width="800" alt="image" src=https://user-images.githubusercontent.com/76990589/216077039-68764e1b-80af-44e1-9a6f-ea5d34745bbf.png>

  
## Models

- Angle Based Outlier Detection (ABOD) : [Angle-Based Outlier Detection in High-dimensional Data](https://www.dbs.ifi.lmu.de/~zimek/publications/KDD2008/KDD08-ABOD.pdf)

- Deep-SVDD : [Deep One-Class Classification](http://proceedings.mlr.press/v80/ruff18a/ruff18a.pdf)

## Result

__0 : Normal, 1: Outlier__
  
<p align="center"><img width="800" alt="image" src=https://user-images.githubusercontent.com/76990589/216079962-7addbea0-fc8f-4f42-9a1b-2722db58dbbc.png>
