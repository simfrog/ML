# ch9-1. XOR문제 딥러닝(NN)으로 풀기  

## 1. Neural Network(NN)  
![multiple logistic regression](https://user-images.githubusercontent.com/31130917/111293415-99def000-868c-11eb-8acc-0ff7767d59d9.png)  
#### Logistic Regression 여러개를 사용하여 XOR 문제를 해결  
  
![B9E4DAFB-8EED-4BEB-910D-54B8031B0F0D](https://user-images.githubusercontent.com/31130917/111294526-c3e4e200-868d-11eb-8ee0-e8cb65418d2d.jpeg)
![366CF990-452D-4C2D-990F-A42A1B15EDC8](https://user-images.githubusercontent.com/31130917/111294535-c7786900-868d-11eb-91e7-8a3463d1d759.jpeg)
![32139E1C-1A17-4C89-A31F-C519A9B2284C](https://user-images.githubusercontent.com/31130917/111294543-c9dac300-868d-11eb-9ce1-b00deb65e80d.jpeg)
![E5794D44-EB7C-43A9-8D6D-5ECAAF40DE86](https://user-images.githubusercontent.com/31130917/111294544-c9dac300-868d-11eb-9634-b7ba377099eb.jpeg)
  
![forward propagation](https://user-images.githubusercontent.com/31130917/111294847-17efc680-868e-11eb-9031-fdbed7359e83.png)  
이전 그림을 정리하면 위 그림처럼 하나로 연결해서 전달할 수 있음  
  
![xor조합](https://user-images.githubusercontent.com/31130917/111295340-99475900-868e-11eb-9509-dc89c4e991ca.PNG)  
위 그림은 XOR 조건을 만족시키는 조합(괄호안에는 두 개의 W값과 b값이 있음)  
<출처 : https://pythonkim.tistory.com/33>  
  
![하나로 결합](https://user-images.githubusercontent.com/31130917/111295559-ddd2f480-868e-11eb-800b-4bd2cd9ca6bb.png)  
왼쪽 그림에 있는 첫 번째 logistic regression들을 하나로 결합함  
  
## 2. W1, W2, b1, b2를 학습시키는 방법  
### => Gradient descent 알고리즘(미분을 사용하여 cost가 줄어드는 방향으로 진행하여 최저점에 도착)  
  
![Derivation](https://user-images.githubusercontent.com/31130917/111296349-b7fa1f80-868f-11eb-81aa-bd9e8c7ed4ca.png)  
Neural Network은 여러 개의 layer를 두어서 복잡한 문제까지 해결할 수 있도록 구성  
앞쪽 layer가 뒤쪽 layer에 어떤 여향을 끼쳤는지 알 수 있으면, 그 반대 또한 알 수 있음  
  
![backpropagation](https://user-images.githubusercontent.com/31130917/111296773-35be2b00-8690-11eb-82a7-a472dc2c36bb.png)  
#### * forward propagation : 앞에서부터 뒤로 진행하면서 W와 b를 바꾸어 나감  
#### * backward propagation : 뒤에서부터 앞으로 거꾸로 진행하면서 바꾸어 나감  
  
#### Neural Network에 포함된 여러 개의 layer 중 결과에 가장 큰 영향을 주는 것 -> 뒤쪽 layer  
#### => 뒤쪽부터 수정해 나감(훨씬 더 좋은 예측할 수 있음)  
  
![chain rule](https://user-images.githubusercontent.com/31130917/111296777-3656c180-8690-11eb-8552-9b4aed67412e.png)  
* ### g를 미분 (g = wx)  
#### x로 미분 -> x가 1 변화할 때, g의 변화량 의미
#### w로 미분 -> w가 1 변화할 때, g의 변화량 의미  

    w = -2, x = 5 -> g = -2*5 = -10  
    w = -1, x = 5 -> g = -1*5 = -5    # w가 1 변할 때 x(5)만큼 변화  
    w = -2, x = 6 -> g = -2*6 = -12   # x가 1 변할 때 w(-2)만큼 변화  
    => g를 x로 미분하면 w가 되고, w로 미분하면 x가 됨
  
* ### f를 미분 (f = g+b)  
#### g로 미분 -> g가 1 변화할 때, f의 변화량 의미
#### b로 미분 -> b가 1 변화할 때, f의 변화량 의미
  
    g = -10, b = 3 -> f = -10 + 3 = -7  
    g = -9, b = 3 -> f = -9 + 3 = -6     # g가 1 변할 때 1만큼 변화  
    g = -10, b = 4 -> f = -10 + 4 = -6   # b가 1 변할 때 1만큼 변화  
    => f를 g나 b로 미분하면 1이 됨
  
* ### 편미분  
w가 변화할 때 인접한 g가 바뀌는 값과 g가 바뀔 때 인접한 f가 바뀌는 값  

    w = -2, x = 5, b = 3 -> f = -2*5 + 3 = -7  
    w = -1, x = 5, b = 3 -> f = -1*5 + 3 = -2   # x가 1변할 때 -2만큼 변화  
    => (f를 w로 미분) = (f를 g로 미분) * (g를 w로 미분) = 1 * x = x(5)
  
x가 변화할 때 f가 바뀌는 값  

    w = -2, x = 5, b = 3 -> f = -2*5 + 3 = -7  
    w = -2, x = 6, b = 3 -> f = -2*6 + 3 = -9   # x가 1변할 때 -2만큼 변화  
    => (f를 x로 미분) = (f를 g로 미분) * (g를 x로 미분) = 1 * w = w(-2)
  
#### w와 x -> input layer
#### f -> output layer
#### g -> hidden layer
  
![chain rule 정리](https://user-images.githubusercontent.com/31130917/111301620-c5b2a380-8695-11eb-9d29-96fc47c3dd72.png)  
Neural Network는 위 그림처럼 계산이 길게 늘어서 있는 형태(간단한 미분)  
  
![chain rule 완전정리](https://user-images.githubusercontent.com/31130917/111301789-f4307e80-8695-11eb-9b62-6f9dab8684d6.png)  
  
![sigmoid](https://user-images.githubusercontent.com/31130917/111301983-2c37c180-8696-11eb-8a02-2163e5eea4c5.png)  
sigmoid 또한 여러개의 계산으로 나눠질 수 있고, 역으로 미분을 통해 어느 정도의 영향을 줬는 지 판단할 수 있음  

    g위 그림의 (z)를 풀었을 때  
    1. z에 -1을 곱해서 음수로 만듬  
    2. 지수를 계산  
    3. 1을 더함  
    4. 앞의 결과를 분모로 취함(1/x)
<출처 : 모두를 위한 딥러닝>
