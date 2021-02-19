# ch5. Logistic Classification의 가설 함수 정의  
 
 ## 1. 분류(Classification)  
 미지의 입력 데이터에 대해 결과가 어떤 종류의 값으로 분류 될 수 있는지를 예측  
 ex) 스팸 문자 분류 : spam(1) or Ham(0)  
     암 판별 : 악성종양(1) or 종양(0)  
     페이스북 피드 : show(1) or hide(0)  
     신용카드 부정거래 탐지 : 합법적(1) or 불법적(0)  
     주식 등등  
  
* 선형 회귀(Linear regression)의 문제점  
Classification에서는 반드시 0 또는 1, 그 사이의 값이 나와야 함  
Hypothesis(H(x) = Wx + b)는 1보다 더 크거나 0보다 더 작은 값이 나올 수 있음  
  
* Logistic Regression 알고리즘  
1. Training Data 특성과 분포를 나타내는 최적의 직선을 찾고(Linear Regression)  
2. 그 직선을 기준으로 데이터를 위(1) 또는 아래(0) 등으로 분류(Classification) 해주는 알고리즘  
=> Classification 알고리즘 중에서도 정확도가 높은 알고리즘으로 알려져 있어 딥러닝에서 기본 컴포넌트로 사용되고 있음  
![logisticregression](https://user-images.githubusercontent.com/31130917/108447960-2a036280-72a4-11eb-8fb4-0885a26e3460.PNG)  
<출처 : https://www.youtube.com/watch?v=ZKHw95q4ZOA&list=PLS8gIc2q83OhM0RTktKDitgZGX5dHo7Vs&index=9&t=4s>  
  
## 2. Sigmoid function(Logistic function)  
출력값 y가 1 또는 0 만을 가져야만 하는 분류 시스템에서 함수 값으로 0~1 사이의 값을 가지는 sigmoid 함수를 사용할 수 있음  
![sigmoid](https://user-images.githubusercontent.com/31130917/108448278-bf065b80-72a4-11eb-81ae-6a65ae44f2ae.PNG)  
  
![logistichypothesis](https://user-images.githubusercontent.com/31130917/108448428-07257e00-72a5-11eb-81f0-a1fbcde7b7e6.PNG)  
  
![costfunction](https://user-images.githubusercontent.com/31130917/108448780-b19da100-72a5-11eb-95f1-2a08c0eaed58.PNG)  
따라서 아래와 같이 사용  
![costfunctionforLogistic](https://user-images.githubusercontent.com/31130917/108448853-d2fe8d00-72a5-11eb-9d6e-187a2292fe44.PNG)  
최종 수식은 다음과 같음  
![최종 cost](https://user-images.githubusercontent.com/31130917/108449120-47393080-72a6-11eb-997a-1a7ae27487ba.PNG)  
ex) y=1, c=-log(H(x))  
    y=0, c=-1*log(1-H(x))  
  
* ### Minimize Cost  
![minimizecost](https://user-images.githubusercontent.com/31130917/108449259-8798ae80-72a6-11eb-84d7-2e1af8c29f31.PNG)  
<출처 : 모두를 위한 딥러닝>  
  
* loss function cross-entropy 유도 
![유도과정](https://user-images.githubusercontent.com/31130917/108449419-cf1f3a80-72a6-11eb-9496-c3e875fdeea9.PNG)  
<출처 : https://www.youtube.com/watch?v=ZKHw95q4ZOA&list=PLS8gIc2q83OhM0RTktKDitgZGX5dHo7Vs&index=9&t=4s>
