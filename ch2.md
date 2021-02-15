# ch2. 선형 회귀(Linear Regression)의 가설(Hypothesis)와 비용(cost)  

## 1. 선형 회귀(Linear Regression)  
가장 기본적이고 많이 사용되는 머신러닝 알고리즘 중 하나  
어떤 요인의 수치에 따라 특정 요인의 수치가 영향을 받음  
#### 변수 x에 의해서 값이 종속적으로 변하는 변수 y  
ex) 시험 공부하는 시간을 늘리면 성적이 잘 나옴  
![regression1](https://user-images.githubusercontent.com/31130917/107740649-faf26b80-6d4e-11eb-8e46-78953e432a91.PNG)  
  
* ### (Linear) Hypothesis  
![선형회귀](https://user-images.githubusercontent.com/31130917/107740645-f9c13e80-6d4e-11eb-94d6-23b54f76c555.PNG)  
  
* ### cost function(Loss function)  
![어느가설이좋은가](https://user-images.githubusercontent.com/31130917/107740932-88ce5680-6d4f-11eb-87ee-e1f72643d40c.PNG)  
#### => 점과의 거리가 가까울 수록 맞는 가설  
#### H(x)-y -> + 또는 - 가 될 수 있기 때문에 옳지 않음  
### (H(x)-y)^2 -> 점과의 거리를 구하는 식(차이가 적을 때 보다 차이가 클 때 패널티를 더 많이 줌)  
비용 계산은 다음과 같음  
![비용](https://user-images.githubusercontent.com/31130917/107741332-4d805780-6d50-11eb-8f29-d7e6213617b8.PNG)  
#### m은 데이터 개수, H(x)는 예측값, y는 실제값  
  
![비용정리](https://user-images.githubusercontent.com/31130917/107741538-b7006600-6d50-11eb-9131-7ed853a43450.PNG)  
### => Goal : Minimize cost  
<출처 : 모두를 위한 딥러닝>
