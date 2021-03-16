# ch8. 딥러닝의 기본 개념  

## 1. 딥러닝의 시작  
![사람의 뇌](https://user-images.githubusercontent.com/31130917/111249049-65e4da00-864e-11eb-890d-72c67fa8bd4c.png)  
사람의 뇌와 비슷하게 동작하도록 구성  
일정 크기 이하라면 활성화되지 않도록 구성  
  
![logistic regression 여러개](https://user-images.githubusercontent.com/31130917/111249046-65e4da00-864e-11eb-936c-f0f2b8aa5ffc.png)  
Logistic Regression을 여러 번 적용하면 오른쪽과 같은 형태로 구성  
  
## 2. XOR 문제  
![xor](https://user-images.githubusercontent.com/31130917/111249042-654c4380-864e-11eb-9343-59566b9956b2.png)  
OR과 AND에서는 잘 동작하지만, XOR문제는 linear 방식으로 풀 수 가 없음  
  
![layer여러개](https://user-images.githubusercontent.com/31130917/111249040-64b3ad00-864e-11eb-8e92-b17a2b2c8b04.png)  
layer가 여러 개 있을 때, 각각의 layer에서 사용한 W와 b를 조절할 수 없다고 수식으로 증명  
  
## 3. Backpropagation  
![backpropagation](https://user-images.githubusercontent.com/31130917/111249037-64b3ad00-864e-11eb-9e6e-a69e3e13bee9.png)  
#### Output layer부터 Input layer까지 반대로 error를 보정하는 기술  
Hinton 교수가 발표  
  
![convolutional](https://user-images.githubusercontent.com/31130917/111249033-641b1680-864e-11eb-89f9-aad3a0265737.png)  
LeCun 교수가 만든 Convolutional 네트워크.  
텐서플로우에 배포하는 mnist 예제 코드가 이걸로 되어 있음  
여러가지를 동시에 구성해서 99.2% 달성  
  
![backpropagation문제점](https://user-images.githubusercontent.com/31130917/111249031-62e9e980-864e-11eb-89c0-af06b5922288.png)  
#### 하지만 layer가 많을 경우 뒤에서부터 멀리 떨어진 layer의 W와 b를 변경할 수 없음  
  
![breakthrough](https://user-images.githubusercontent.com/31130917/111249715-7c3f6580-864f-11eb-9980-6e59c49fdb3d.png)  
해결방법을 찾음  

    여러개의 layer가 있어도 초기값을 잘 선택하면 학습이 가능  
    신경망을 잘 구성하면 복잡한 문제를 효율적으로 풀 수 있음  
    Neural Network 대신 사람들의 주의를 끌 수 있는 Deep learning으로 rebranding  
  
![요약](https://user-images.githubusercontent.com/31130917/111249704-7b0e3880-864f-11eb-8b8a-fe9d3178ab0d.png)  
지금까지 발견한 것들에 대한 요약  

    labeled dataset이 너무 작았음  
    컴퓨터는 수백만배 느림  
    초기화를 잘 하지 못함  
    non-linearity(sigmoid)를 잘못 사용  
 <출처 : 모두를 위한 딥러닝>
