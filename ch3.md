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
### Minimize cost function  
많은 최소화 문제에 사용됨  
주어진 cost function, cost(W,b)는 비용을 최소화 하고자 W와 b를 찾음  
more general function에서도 적용됨  
ex) cost(w1, w2, ...)  
  
    1. 추측 값 부터 시작(  
      - 0, 또는 아무 값에서 시작가능  
      - W 와 b를 계속 조금씩 변경하여 cost(W,b)를 줄임  
    2. parameter를 변경할 때마다 cost(W,b)를 가장 많이 절감할 수 있는 기울기를 선택  
    3. 반복  
    4. local mininum으로 수렴될 때까지 이 작업 수행  
  
#### 어떤 시작점에서 시작하든 항상 최소점에 도달  
  
## 3. 기울기 구하는 방법  
2m으로 나눠도 똑같음  
![포말식](https://user-images.githubusercontent.com/31130917/107906209-e5ba4e80-6f93-11eb-8f6e-ba13483f133c.PNG)  
  
알파를 learning rate이라고 부르는데 일단 상수라 가정(W값의 감소 또는 증가되는 비율을 나타냄)  
![포말식2](https://user-images.githubusercontent.com/31130917/107906303-1d28fb00-6f94-11eb-9ee0-904e8e3ed03d.PNG)  
W에서의 편미분은 기울기를 나타냄  
#### 양수 값을 갖는다면 W는 왼쪽으로 이동시켜야만(감소) 손실함수 cost(W) 최소값 찾음  
#### 음수 값을 갖는다면 W는 오른쪽으로 이동시켜야만(증가) cost(W) 최소값 찾음  
  
미분절차  
![미분절차](https://user-images.githubusercontent.com/31130917/107906428-7002b280-6f94-11eb-93b0-cbb296b3ec14.PNG)  
#### 마지막 식이 Gradient descent algorithm의 식으로 이 식을 여러번 실행 시키면 minimize cost를 구할 수 있음  
  
아래와 같은 경우 시작점이 바뀌면 그 최소값 또한 달라짐  
![convexfunction](https://user-images.githubusercontent.com/31130917/107906650-f1f2db80-6f94-11eb-9367-d6e91328d3f1.PNG)  
  
cost function을 가지고 그림을 그리면 아래와 같이 나타나고 어느 점에서 시작하든 최소값이 같음  
![convexfunction2](https://user-images.githubusercontent.com/31130917/107906720-2797c480-6f95-11eb-9a6d-e497170d55b4.PNG)  
<출처 : 모두를 위한 딥러닝>
