# ch6. Multinomial classification  

## 1. Logistic regression(Binary classification)  
### 데이터를 1과 0의 두가지 그룹으로 나누기 위해 사용하는 모델  
### softmax : 데이터를 2개 이상의 그룹으로 나누기 위해 binary classification을 확장한 모델  

![logistic 식](https://user-images.githubusercontent.com/31130917/108628697-b037c880-749f-11eb-9837-d392c0e8cccf.PNG)  
![logistic 그림](https://user-images.githubusercontent.com/31130917/108628612-56370300-749f-11eb-8620-72fe61e42afb.PNG)  
  
#### Y : 실제값  
#### Y-hat : 예측값  
  
## 2. Multinomial classification  
![multinomial1](https://user-images.githubusercontent.com/31130917/108628844-5552a100-74a0-11eb-8896-6254b850b0ea.PNG)  
![multinomial2](https://user-images.githubusercontent.com/31130917/108628846-5683ce00-74a0-11eb-8dc4-c97c0968cfd7.PNG)  
![multinomial3](https://user-images.githubusercontent.com/31130917/108628847-5683ce00-74a0-11eb-8e1a-7d0b05676d89.PNG)  
위의 그래프는 아래와 같은 행렬식으로 쓸 수 있음  
![multinomial4](https://user-images.githubusercontent.com/31130917/108628848-571c6480-74a0-11eb-9929-8922f1261021.PNG)  
![multinomial5](https://user-images.githubusercontent.com/31130917/108628850-571c6480-74a0-11eb-9b63-e0980cc2ce24.PNG)  
하지만 이와 같이 계산하면 0~1사이의 값으로 안 나옴  
![sigmoid1](https://user-images.githubusercontent.com/31130917/108628921-c2663680-74a0-11eb-92f6-f47f3eb59bb0.PNG)  
  
* ### SOFTMAX function  
아래의 함수를 통해 0~1 사이의 값으로 만듬  
![softmax](https://user-images.githubusercontent.com/31130917/108628968-12dd9400-74a1-11eb-86c1-142ce5ac95e2.PNG)  
  
* ### 'ONE-HOT' encoding  
'ONE-HOT' encoding 기법을 사용해 SOFTMAX 함수를 이용하여 나온 결과값을 0과 1로 딱 떨어지게 만듬  
![one-hotenecoding](https://user-images.githubusercontent.com/31130917/108629061-7962b200-74a1-11eb-85e3-bd55c5ca74af.PNG)  
#### => tensorflow에서는 'argmax'를 이용하여 처리  
  
* ### Cross-entropy cost function
![cross-entropy](https://user-images.githubusercontent.com/31130917/108629105-c47cc500-74a1-11eb-9e3e-0ae8d3f461ed.PNG)  
#### S(y) = Y-hat, L = Y  
  
![cross-entropy 계산](https://user-images.githubusercontent.com/31130917/108629220-4bca3880-74a2-11eb-9f8c-b46c1d80d275.PNG)  
![cross-entropy 계산2](https://user-images.githubusercontent.com/31130917/108629222-4cfb6580-74a2-11eb-9f37-cf7f513e9da5.PNG)  
  
![logistic cross entropy](https://user-images.githubusercontent.com/31130917/108629323-a368a400-74a2-11eb-9ec4-d14f1844ba47.PNG)  
#### 실제값 L1, L2는 1과 0, 그리고 서로 반대의 값을 지닐 수 밖에 없기 때문에 L2 = 1-L1 일 수 밖에 없음(0또는1, 1또는0)  
#### S1, S2는 예측값이기 때문에 1, 0만 나오는 것은 아니지만 둘의 합은 1이 될 수 밖에 없음(0.3, 0.7 등등, 즉 1-S1=S2)  
#### 따라서 -L1*log(S!)-(1-L1)*log(1-S1) 가 됨  
#### L1 = y, S1 = H(x) 로 바꾸면 -y*log(H(x))-(1-y)*log(1-H(x)) 가 됨  
  
* ### Cost function  
따라서 아래와 같이 cost function을 정의할 수 있음  
![costfunction](https://user-images.githubusercontent.com/31130917/108629585-fbec7100-74a3-11eb-8383-7a92515a6f80.PNG)  
  
* Gradient descent  
![gradient descent](https://user-images.githubusercontent.com/31130917/108629634-2dfdd300-74a4-11eb-895f-cd7d2e2b4200.PNG)  
<출처 : 모두를 위한 딥러닝>
