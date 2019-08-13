# WatermarkReco

Pytorch implementation of Paper "Large Scale Historical Watermarks Recognition: dataset and a new consistency-based approach"

[[PDF(TODO)]]() [[Project webpage]](http://imagine.enpc.fr/~shenx/Watermark/) 

<p align="center">
<img src="TODO" width="400px" alt="teaser">
</p>

If our project is helpful for your research, please consider citing : 
```
@inproceedings{shen2019watermark,
          title={Large Scale Historical Watermarks Recognition: dataset and a new consistency-based approach},
          author={Shen, Xi and Pastrolin, Ilaria and Bounou, Oumayma and Gidaris, Spyros and Smith, Marc and Poncet, Olivier and Aubry, Mathieu},
          booktitle={Arxiv},
          year={2019}
        }
```

## Table of Content
* [Installation](#installation)
* [Feature Pretraining: Classification](#feature-pretraining:-classification)
* [Local Matching](#local-matching)
* [Feature Learning](#feature-learning)
* [Visual Results](#visual-results)


## Installation

### Dependencies

Code is tested under **Pytorch > 1.0 + Python 3.6** environment. To install all dependencies : 

``` Bash
bash requirement.sh
```

### Datasets

To download datasets: 
``` Bash
cd data/
bash download_data.sh
```

Resume of the watermark dataset:
 
| Dataset |  Test (#cls X #img per cls) | Description and Task|
| :------: |  :------: | :------: |
| A Train | 100 X 50 + 100 X 10| Train and test on the same 100 classes, classification|
| A Test | 100 X 3| Another 100 classes different from A train, 1 ref + 2 test photographs, one-shot recognition|
| B Train | 140 X 1-7| 140 classes, 1 engraving + 1-7 photographs, cross-domain feature fine-tuning|
| B Test | 100 X 3| 100 classes different from B Train, 1 engraving + 2 photographs, one-shot cross-domain recognition|
| Briquet | 16753 X 1| 16753 classes, 1 engraving, large scale one-shot cross-domain recognition|

###  Models

To download pretrained models: 
``` Bash
cd model/
bash download_model.sh # classification models + fine-tuned models
```
## Feature Pretraining: Classification

Dataset: A Train

``` Bash
cd classification/
bash demo_train.sh # Training with Dropout Ratio 0.7
```

## Local Matching

### One-shot Recognition 

Dataset: A Test
``` Bash
cd localMatching/
bash demo_A.sh 
```

### One-shot Cross-domain Recognition


Dataset: B Test 
``` Bash
cd localMatching/
bash demo_B.sh # Using classification model 
bash demo_B_Finetune.sh # Using our fine-tuned model 
```

Dataset: Shoes / Chairs
``` Bash
cd localMatching/
bash demo_SBIR_ImageNet.sh # Using ImageNet pretrained model
bash demo_SBIR_Finetune.sh # Using our fine-tuned model 
```

### Large Scale One-shot Cross-domain Recognition (16753 classes)

Dataset: B Test + Briquet 
``` Bash
cd localMatching/
bash demo_Briquet_Finetune.sh # Using our fine-tuned model 
```














