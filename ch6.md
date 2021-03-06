# ch6. Multinomial classification  

## 1. Logistic regression(Binary classification)  
### 데이터를 1과 0의 두가지 그룹으로 나누기 위해 사용하는 모델  
### softmax : 데이터를 2개 이상의 그룹으로 나누기 위해 binary classification을 확장한 모델  
![logistic regression](https://user-images.githubusercontent.com/31130917/111204643-b38b2380-8609-11eb-99d5-3e4725335f32.png)  
Wx의 결과로 z가 나오고, S로 표현되는 sigmoid에 전달되어 최종적으로 Y를 예측  
#### Y : 실제값  
#### Y-hat : 예측값  
  
## 2. Multinomial classification  
![multinomial1](https://user-images.githubusercontent.com/31130917/111205641-cce09f80-860a-11eb-84e3-8eefb01161f3.png)
![multinomial2](https://user-images.githubusercontent.com/31130917/111205501-a6baff80-860a-11eb-8486-0725ed8a4942.png)  
  
![multinomial3](https://user-images.githubusercontent.com/31130917/108628847-5683ce00-74a0-11eb-8e1a-7d0b05676d89.PNG)  
  
위의 그래프는 아래와 같은 행렬식으로 쓸 수 있음  
  
![multinomial4](https://user-images.githubusercontent.com/31130917/108628848-571c6480-74a0-11eb-9929-8922f1261021.PNG)  
![multinomial5](https://user-images.githubusercontent.com/31130917/108628850-571c6480-74a0-11eb-9b63-e0980cc2ce24.PNG)  
![sigmoid1](https://user-images.githubusercontent.com/31130917/108628921-c2663680-74a0-11eb-92f6-f47f3eb59bb0.PNG)  
하지만 이와 같이 계산하면 0~1사이의 값으로 안 나옴  
  
* ### SOFTMAX function  
![softmax](https://user-images.githubusercontent.com/31130917/108628968-12dd9400-74a1-11eb-86c1-142ce5ac95e2.PNG)  
  
    1. 입력을 sigmoid와 마찬가지로 0과 1사이의 값으로 변환  
    2. 변환된 결과에 대한 합계가 1이 되도록 만들어 줌  
  
* ### 'ONE-HOT' encoding  
'ONE-HOT' encoding 기법을 사용해 SOFTMAX 함수를 이용하여 나온 결과값을 0과 1로 딱 떨어지게 만듬  
![one-hotenecoding](https://user-images.githubusercontent.com/31130917/108629061-7962b200-74a1-11eb-85e3-bd55c5ca74af.PNG)  
#### => tensorflow에서는 'argmax'를 이용하여 처리  
  
* ### Cross-entropy cost function
![cross-entropy](https://user-images.githubusercontent.com/31130917/108629105-c47cc500-74a1-11eb-9e3e-0ae8d3f461ed.PNG)  
cross-entropy : 통계학 용어, 두 확률 분포 p와 q사이에 존재하는 정보량을 계산하는 방법  
#### S(y) = Y-hat, L = Y  
L은 label을 의미
#### cost함수는 예측한 값과 실체 값의 거리(distance, D)를 계산하는 합수로, 이 값이 줄어드는 방향으로, 즉 entropy가 갑소하는 방향으로 진행하다보면 최저점을 만남  
  
![cross-entropy 계산](https://user-images.githubusercontent.com/31130917/108629220-4bca3880-74a2-11eb-9f8c-b46c1d80d275.PNG)  
![cross-entropy 계산2](https://user-images.githubusercontent.com/31130917/108629222-4cfb6580-74a2-11eb-9f37-cf7f513e9da5.PNG)  
  
![logistic cross entropy](https://user-images.githubusercontent.com/31130917/108629323-a368a400-74a2-11eb-9ec4-d14f1844ba47.PNG)  
#### 실제값 L1, L2는 1과 0, 그리고 서로 반대의 값을 지닐 수 밖에 없기 때문에 L2 = 1-L1 일 수 밖에 없음(0또는1, 1또는0)  
#### S1, S2는 예측값이기 때문에 1, 0만 나오는 것은 아니지만 둘의 합은 1이 될 수 밖에 없음(0.3, 0.7 등등, 즉 1-S1=S2)  
#### 따라서 -L1*log(S1)-(1-L1)*log(1-S1) 가 됨  
#### L1 = y, S1 = H(x) 로 바꾸면 -y*log(H(x))-(1-y)*log(1-H(x)) 가 됨  
  
* ### Cost function  
![costfunction](https://user-images.githubusercontent.com/31130917/108629585-fbec7100-74a3-11eb-8383-7a92515a6f80.PNG)  
L은 loss의 약자로 다른 말로든 cost 또는 error라고 함  
비용은 결국 잘못 예측했을 때의 값, 즉 에러라고 볼 수 있음  
  
* Gradient descent  
![gradient descent](https://user-images.githubusercontent.com/31130917/108629634-2dfdd300-74a4-11eb-895f-cd7d2e2b4200.PNG)  
알파 오른쪽의 삼각형은 미분을 한다는 뜻  
gradient descent 알고리즘을 구현하기 위해서는 cost함수와 gradient를 계산하는 함수가 모두 필요  
따라서 위 그림은 learning rate에 미분 결과를 곱한 값을 빼야 한다고 나와있음(앞에 음수 기호가 있음)  
하지만 이걸 미분하는 것은 너무 복잡하기에 생략  
<출처 : 모두를 위한 딥러닝>
