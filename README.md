# Dacon <Outlier detection through mechanical sound>
![image](https://user-images.githubusercontent.com/76990589/216082423-2403ebcd-8dca-46da-8d0e-075366cc59df.png)

## Intro
Determining whether a fan is out of order through unsupervised learning from normal data __(Unsupervised Anomaly Detection)__

## Dataset

- train [Folder]
    - A total of 1279 fan sound samples
    - TRAIN_0000.wav ~ TRAIN_1278.wav


- test [Folder]
    - Fan Sound Samples for Inference
    - TEST_0000.wav ~ TEST_1513.wav


- train.csv [File]
    - SAMPLE_ID : Unique ID per sample
    - SAMPLE_PATH : Sound sample file path
    - FAN_TYPE : Type of fan (0, 2)
    - LABEL : Fan failure (0: Normal, 1: Failure)
    - __All training data have only normal samples__


- test.csv [File]
    - SAMPLE_ID : Unique ID per sample
    - SAMPLE_PATH : Sound sample file path
    - FAN_TYPE : Type of fan (0, 2)


- sample_submission.csv [File]
    - SAMPLE_ID : Unique ID per sample
    - LABEL : Predicted fan failure (0: normal, 1: failure)

_____________________________
    
This dataset is made available by Hitachi, Ltd. under a Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0) license.

[1] Harsh Purohit, Ryo Tanabe, Kenji Ichige, Takashi Endo, Yuki Nikaido, Kaori Suefusa, and Yohei Kawaguchi, “MIMII Dataset: Sound Dataset for Malfunctioning Industrial Machine Investigation and Inspection,” arXiv preprint arXiv:1909.09347, 2019.

[2] Harsh Purohit, Ryo Tanabe, Kenji Ichige, Takashi Endo, Yuki Nikaido, Kaori Suefusa, and Yohei Kawaguchi, “MIMII Dataset: Sound Dataset for Malfunctioning Industrial Machine Investigation and Inspection,” in Proc. 4th Workshop on Detection and Classification of Acoustic Scenes and Events (DCASE), 2019.

_____________________________
    
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
  
<p align="center"><img width="800" alt="image" src=https://user-images.githubusercontent.com/76990589/216086640-983ce935-4d8c-4cde-b8fe-66cae66f2fd9.png>

  
## Models

- Angle Based Outlier Detection (ABOD) : [Angle-Based Outlier Detection in High-dimensional Data](https://www.dbs.ifi.lmu.de/~zimek/publications/KDD2008/KDD08-ABOD.pdf)

- Deep-SVDD : [Deep One-Class Classification](http://proceedings.mlr.press/v80/ruff18a/ruff18a.pdf)

## Result

__0 : Normal, 1: Outlier__
  
<p align="center"><img width="800" alt="image" src=https://user-images.githubusercontent.com/76990589/216079962-7addbea0-fc8f-4f42-9a1b-2722db58dbbc.png>

__PUBLIC SCORE  : 0.99113__
    
__PRIVATE SCORE : 0.99339__
