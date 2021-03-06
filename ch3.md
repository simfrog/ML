# ch3. 선형 회귀(Linear Regression)의 비용(cost)최소화 알고리즘의 원리 설명  

## 1. Minimize cost 구하는 방법  
![간단회귀식](https://user-images.githubusercontent.com/31130917/107905255-88250280-6f91-11eb-9436-7fc4185bd65e.PNG)  
기존 공식을 단순화하고자 위와 같이 b를 없앰  
  
![간단회귀식계산](https://user-images.githubusercontent.com/31130917/107905250-86f3d580-6f91-11eb-9feb-fe2b3027e048.PNG)  
위와 같이 계산한 식을 점으로 나타내면 아래와 같이 표현됨  
  
![간단회귀식그래프](https://user-images.githubusercontent.com/31130917/107905356-c6babd00-6f91-11eb-9583-e30c47df921e.PNG)  
위의 그래프로 보아 W가 1일 때 가장 작은 비용이 듬  
W = 1 이므로 H(x) = x 이고 cost는 0이 됨  
  
## 2. Gradient descent algorithm(경사 하강 알고리즘)  
아래와 같은 역할 수행  

    최저 비용을 계산하는 함수    
    다양한 최저 계산에 사용  
    Cost함수에 대해 최소가 되는 기울기(W)와 y절편(b)탐색  
    피처(feature, 변수)가 여러개인 버전에도 적용 가능 ex) cost(w1, w2, ...)  
  
정리하면

    어떤 위치(왼쪽 또는 오른쪽 경사)에서 시작하더라도 최소 비용 계산  
    기울기(W)와 y절편(b)을 계속적으로 변경하면서 최소 비용 계산  
    반복할 때마다 다음 gradients(기울기의 정도) 계산  
    최소 비용에 수렴할 때까지 반복  
  
#### => 어떤 시작점에서 시작하든 항상 최소점에 도달  
  
## 3. 기울기 구하는 방법  
왼쪽부터 1번, 2번, 3번  
![1](https://user-images.githubusercontent.com/31130917/111187818-bbda6300-85f7-11eb-8283-7d147c2e8443.png)
![2](https://user-images.githubusercontent.com/31130917/111187822-bc72f980-85f7-11eb-8b42-7da0bb7ef105.png)
![3](https://user-images.githubusercontent.com/31130917/111187825-bd0b9000-85f7-11eb-8aee-ec6bfeee9346.png)  
1번 그림은 데이터 개수가 m일 때, m이 아닌 2m을 사용하겠다는 뜻  
그 이유는 오른쪽 그림에서 제곱을 미분하게 되면 2가 앞으로 나오는데, 이때 분자에 있는 2와 분모에 있는 2를 약분하면 공식이 단순해지기 때문  
2m으로 나눠도 변함이 없기 때문에 2m으로 변경  
  
#### 양수 값을 갖는다면 W는 왼쪽으로 이동시켜야만(감소) 손실함수 cost(W) 최소값 찾음  
#### 음수 값을 갖는다면 W는 오른쪽으로 이동시켜야만(증가) cost(W) 최소값 찾음  
  
![1](https://user-images.githubusercontent.com/31130917/111189324-4f606380-85f9-11eb-9be0-2fd78211c3a2.png)
![2](https://user-images.githubusercontent.com/31130917/111189322-4f606380-85f9-11eb-843f-2c4efd9b8604.png)
![3](https://user-images.githubusercontent.com/31130917/111189315-4ec7cd00-85f9-11eb-9843-c3084922285d.png)  
알파를 learning rate이라고 부르는데 일단 상수라 가정(W값의 감소 또는 증가되는 비율을 나타냄)  
  
첫번째 그림은 구하고자하는 변화량, 가운데는 cost(W)를 가리키는 공식  
첫번째와 가운데 공식을 더하면 오른쪽의 복잡한 공식이 만들어짐  
(분자와 분모에 있는 기호는 도함수)  
  
미분절차  
![미분절차](https://user-images.githubusercontent.com/31130917/107906428-7002b280-6f94-11eb-93b0-cbb296b3ec14.PNG)  
첫번째 공식에서 제곱은 두번째 공식의 시그마 오른쪽에 2로 변환  
여기에 (Wx-y)에 대해 미분을 적용해야 하고 결과는 Wx는 x, y는 W가 없으므로 상수처리되어 0이 됨  
따라서 (Wx-y)에 대해 W로 미분을 하면 x가 나오게 되고 두번째 오른쪽 끝에 추가됨  
이를 정리하면 세번째 공식이 만들어짐  
여기서 알파는 임의로 추가하는 상수로 미분에는 적용되지 않음  
#### 마지막 식이 Gradient descent algorithm의 식으로 이 식을 여러번 실행 시키면 minimize cost를 구할 수 있음  
  
![convexfunction](https://user-images.githubusercontent.com/31130917/107906650-f1f2db80-6f94-11eb-9367-d6e91328d3f1.PNG)  
아래와 같은 경우 시작점이 바뀌면 그 도착점(최소값) 또한 달라짐  
  
![convexfunction2](https://user-images.githubusercontent.com/31130917/107906720-2797c480-6f95-11eb-9a6d-e497170d55b4.PNG)  
cost function을 가지고 그림을 그리면 아래와 같이 나타나고 어느 점에서 시작하든 최소값이 같음  
위 그림과 같이 오목한 형태가 되도록 만들어야 함  
#### => convex 함수  
#### gradient descent algorithm은 convex 형태에 대해서만 적용할 수 있음  
<출처 : 모두를 위한 딥러닝>
