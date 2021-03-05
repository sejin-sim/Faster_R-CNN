# Faster_R-CNN (Object_detection)

## 1. Faster R-CNN 흐름
### 1) R-CNN : CNN 사용 최초의 object detection 방법

<img src ="https://user-images.githubusercontent.com/67107675/110052877-ab2a2180-7d9b-11eb-998a-7d0b6e784f83.png" width="70%" height="70%">

 (1) Hypothesize Bounding Boxes (Proposals - Selective Search)   
 (2) Resampling pixels, features for each boxes   
 (3) Classifier, Bounding Box Regressor   
 - AlexaNet 사용 224 x 22x 강제 warping : 성능 ↓
 - Selective search 통해 2,000개 image proposal all input : 소요 시간 ↑
 - Selective search & SVM은 GPU 사용 적합 구조 X
 - Computation share X : No back propagation

### 2) Fast R-CNN :  RoI pooling

<img src ="https://user-images.githubusercontent.com/67107675/110053107-1d9b0180-7d9c-11eb-88b5-6ab2b46e89d6.png" width="70%" height="70%">

 (1) RoI pooling : feature map에 이전 RoI projection, RoI를 FC layer input 크기에 맞게 고정된 크기로 변형 가능   
 (2) FCL → Classifier, Bounding Box Regressor 동시 학습
 - Region Proposal을 CNN Network가 아닌 Selective search 외부 수행 : 병목 현상

### 3) Faster R-CNN : RPN

<img src ="https://user-images.githubusercontent.com/67107675/110053867-7323de00-7d9d-11eb-8b2b-c32e2552d18b.png" width="40%" height="40%"> 

  (1) Region proposal Networks(RPN) : input-Featrue Map, output-Object proposal의 Sample
  - Region Proposal을 CNN Network 내부 수행 & GPU 연산 : 소요 시간 ↓

### 4) 비교

<img src ="https://user-images.githubusercontent.com/67107675/110054598-b9c60800-7d9e-11eb-8d43-89916bf8b2c2.png" width="50%" height="50%"> 

## 2. Code (Pytorch)
### 1) [Model Implementations](https://colab.research.google.com/github/sejin-sim/Faster_R-CNN_Object_Detection/blob/main/Faster_R-CNN_Implementations_by_Pytorch.ipynb) 
### 2) [Model Carry out](https://colab.research.google.com/github/sejin-sim/Faster_R-CNN_Object_Detection/blob/main/Faster_R-CNN_Object_Detection.ipynb)
