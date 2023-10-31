1. Semantic Segmentation
 (1) segmentation : 입력 이미지를 픽셀 수준에서 분석하여 각 픽셀에 클래스 레이블을 할당

 (2) 예시 : 스마트폰의 인물 사진 모드 (구글 pixel 2), 자율주행, 의료 영상

 (3) instance segmentation vs semantic segmentation
 - instance segmentation
   : 이미지의 모든 물체에 대해 클래스 라벨을 예측하고 추가로 임의의 ID 부여
   : 같은 class에 속하더라도 다른 instance면 다르게 분류
 - semantic segmentation
   : 이미지의 모든 물체에 대해 클래스 라벨 예측

2. Fully Convolutional Network (FCN)
 (1) VGG16을 backbone으로 사용
 - VGG16 : 3x3의 Convolution 네트워크만을 이용해서 특징을 추출하고, 이후 3개의 FC Layer를 이용해 
Classification을 수행하는 구조
 - Why? : AlexNet, VGG16, GoogleLeNet 중 가장 평가가 좋음
        : 미리 훈련된 네트워크를 그대로 사용 O

 (2) VGG 네트워크의 FC layer인 nn.Linear부분을 convolution으로 변경
     : fully connected layer 대신 fully convolutional layer 사용
 - Why? : 위치정보 추출 O
        : 임의의 입력크기에 대해서도 일관성 있는 결과를 생성

 (3) Transposed Convolution을 통해 Pixel wise Prediction 진행
 - Transposed Convolution
   : pooling 단계에 의해 감소한 이미지의 크기를 원본 크기로 복원하는 방법
   : 학습이 가능한 파라미터를 통해 줄어든 이미지를 다시 키우는 Convolution
 - Skip Connection
   : 단순한 연결 작업으로 coarse한 정보들이 빠질 수 있는 FCN 방법을 보완하는 방법

 (4) FCN의 한계
   : 객체의 크기가 크거나 작을 때 예측 X
   : deconvolution의 절차가 간단해서 객체의 디테일한 모습이 사라짐

 (5) FCN의 한계 극복 방법 - DeconvNet
   : encoder와 decoder 구조 사용
   : unpooling(경계값을 잡아냄) 과 transposed convolution(디테일을 잡아냄)이 반복적으로 이뤄짐
