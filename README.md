# Dacon_Machine-Sound-Outlier-Detection
__Outlier detection through mechanical sound__
![image](https://user-images.githubusercontent.com/76990589/216082423-2403ebcd-8dca-46da-8d0e-075366cc59df.png)

## Intro
Determining whether a fan is out of order through unsupervised learning from normal data __(Unsupervised Anomaly Detection)__

## Dataset

- train [폴더]
    - 총 1279개 팬(FAN) 소리 샘플
    - TRAIN_0000.wav ~ TRAIN_1278.wav


- test [폴더]
    - 추론을 위한 팬(FAN) 소리 샘플
    - TEST_0000.wav ~ TEST_1513.wav


- train.csv [파일]
    - SAMPLE_ID : 샘플 별 고유 ID
    - SAMPLE_PATH : 음향 샘플 파일 경로
    - FAN_TYPE : 팬(FAN)의 모델 종류 (0, 2 존재)
    - LABEL : 팬(FAN) 고장 여부 (0 : 정상, 1 : 고장)
    - 학습 데이터는 모두 정상 샘플만 존재


- test.csv [파일]
    - SAMPLE_ID : 샘플 별 고유 ID
    - SAMPLE_PATH : 음향 샘플 파일 경로
    - FAN_TYPE : 팬(FAN)의 모델 종류 (0, 2 존재)


- sample_submission.csv [파일] - 제출 양식
    - SAMPLE_ID : 샘플 별 고유 ID
    - LABEL : 예측한 팬(FAN) 고장 여부 (0 : 정상, 1 : 고장)

This dataset is made available by Hitachi, Ltd. under a Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0) license.

[1] Harsh Purohit, Ryo Tanabe, Kenji Ichige, Takashi Endo, Yuki Nikaido, Kaori Suefusa, and Yohei Kawaguchi, “MIMII Dataset: Sound Dataset for Malfunctioning Industrial Machine Investigation and Inspection,” arXiv preprint arXiv:1909.09347, 2019.

[2] Harsh Purohit, Ryo Tanabe, Kenji Ichige, Takashi Endo, Yuki Nikaido, Kaori Suefusa, and Yohei Kawaguchi, “MIMII Dataset: Sound Dataset for Malfunctioning Industrial Machine Investigation and Inspection,” in Proc. 4th Workshop on Detection and Classification of Acoustic Scenes and Events (DCASE), 2019.

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
