1. Image Classification
: 이미지를 미리 설정해놓은 카테고리 중 하나로 분류하는 과정

1) classifier
- 어떤 이미지를 input으로 받은 뒤 하나의 카테고리로 분류하여 output을 만들어 내는 classifier
- 부서지기 쉬움
- 확장성이 뛰어나지 X
2) semantic gap
- 겉으로 보기엔 쉬워 보이지만 각 픽셀을 3개의 숫자로 표현해야 하기 때문에 기계에게는 어려운 문제
- semantic gap의 종류
(1) viewpoint variation : 각도에 따라 다양한 형태로 포착해 다르게 분류
(2) illumination : 명암 차이로 인해 다르게 분류
(3) deformation : 변형된 형태로 인해 다르게 분류
(4) occlusion : 물체의 일부만 포착되어 다르게 분류
(5) background clutter : 물체와 배경을 구분하기 어려워 다르게 분류
(6) intraclass variation : 다양한 종류로 인해 다르게 분류

2. KNN (K-Nearest Neighbor)
: k개의 비슷한 이미지를 찾은 후 가장 유사한 이미지의 label로 분류하는 방법

1) k의 중요성
- k가 너무 크면 과소적합, 너무 작으면 과대적합 위험이 있어 적절한 k값 탐색이 중요
- 일반적으로 k 는 과반수가 나오게 하기 위해 1이 아닌 홀수로 설정
2) 거리 측정
- 컴퓨터는 이미지를 행렬로 보기 때문에 픽셀의 값이 비슷하면 비슷한 이미지로 판단이 됨 -> 두 행렬 간의 거리를 측정
3) 단점
- 너무 오래 걸림
- 픽셀 간 거리 != 인간의 직관
- 차원의 저주

3. Linear Classification
: 선형분류기로 매우 간단한 학습 알고리즘으로써 신경 네트워크를 구축하는데 많이 사용됨
: parametric approach로써 어떤 이미지가 주어지면, 이를 linear 변환을 통해 리턴한 값을 이미지 분류에 사용함
﻿
1) f(x, W, b) = Wxi​ + b 
- xi : input image -> 행렬로 변환하여 계산
- W : training set으로 알아낸 parameter의 행렬
- b : bias vector로 실제 데이터 x와 관계없이 output에 영향을 주는 요소
2) 단점
- 선형분류기를 하나만 이용하면 템플릿이 하나로만 요약됨
-> 다양한 블록들을 쌓아야 함

4. Loss function
: 신경망 성능의 '나쁨'을 나타내는 지표
: 정답과 비교했을 때 신경망이 학습 데이터를 얼마나 잘 처리했는지, 못했는지를 평가하는 것으로, 이 값이 높을수록 모델이 좋지 않음을 나타냄

﻿
﻿
﻿
﻿
