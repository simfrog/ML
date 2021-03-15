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

    1. 학습된 모델을 수정하는 것은 옳지 않음  
     -> 예측이 틀릴 수는 있지만, 누구나 알 수 있는 사실에 대해 틀린 예측을 하면 올바른 모델이라고 할 수 없음  
    2. 어떤 방식의 선처리가 됐건 데이터를 2개로 분리하는 것은 편협한 느낌  
     -> 0에서 100점, 0에서 1.0 등의 구간을 통해 성공과 실패를 판정할 수 있는 모델이 필요  
    3. 직선에 대해 x에 대한 y를 예측하는 것이 아닌 직선의 아래쪽과 위쪽이라는 새로운 방식의 판정 기준을 도입(분류이기 때문에)  
    4. 점수가 아주 작거나 매우 큰 경우에 대해서도 모델을 수정하지 않고 사용할 수 있는 방법이 필요(1번과 유사)  
  
## 2. Sigmoid function(Logistic function)  
![식](https://user-images.githubusercontent.com/31130917/111198124-92730480-8602-11eb-8586-eb8ccd470e23.png)
![sigmoid](https://user-images.githubusercontent.com/31130917/111198374-d403af80-8602-11eb-931f-706a58778f68.png)  
출력값 y가 1 또는 0 만을 가져야만 하는 분류 시스템에서 함수 값으로 0~1 사이의 값을 가지는 sigmoid 함수를 사용할 수 있음  
  
    e로 시작하는 계산식이 0일 떄, 1/1이 돼서 최대값인 1이 됨  
    e로 시작하는 계산식이 매우 클 때, (1/큰수)이 돼서 최소값인 0이 됨  
    WX가 0일 때, 지수가 0이 되어, 분모는 2가 되고, 이때 중간값인 1/2이 됨  
  

![costfunction](https://user-images.githubusercontent.com/31130917/108448780-b19da100-72a5-11eb-95f1-2a08c0eaed58.PNG)  
Hypothesis는 cost함수를 구성하는 핵심이기 때문에 cost함수 또한 이전과 달라져야 함  
왼쪽은 직선을 살짝 구부려서 연결을 한 모양, 오른쪽은 sigmoid를 구부려서 연결한 모양  
오른쪽의 경우 매끄럽게 만들지 않으면 local minimum을 최저점으로 잘못 발견할 수 있는 문제 발생  
그래서 반드시 구불구불한 형태의 그래프를 매끈하게 펴야함, 그래야 global minimum에 도착할 수 있음  
  
![costfunctionforLogistic](https://user-images.githubusercontent.com/31130917/108448853-d2fe8d00-72a5-11eb-9d6e-187a2292fe44.PNG)  
지수를 사용하는 hypothesis의 비용을 판단하기 위해 log를 사용  
log를 사용함으로써 구불구불한 cost함수를 매끈하게 필 수 있음  
  
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
