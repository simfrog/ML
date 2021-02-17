# ch4. Multi-Variable Linear Regression  

## 1. Multi-Variable  
Multi-Variable에서 hypothesis와 cost(loss) function 식은 다음과 같이 씀  
![costfunction](https://user-images.githubusercontent.com/31130917/108230352-06e19180-7184-11eb-9645-aec86cb041f2.PNG)  
![multi](https://user-images.githubusercontent.com/31130917/108230450-27115080-7184-11eb-9db3-d18bdd659878.PNG)  
  
* ### Matrix  
Multi-Variable에서의 계산을 빠르고 편리하게 하고자 Marix의 곱셈을 이용하여 계산  
![matrix](https://user-images.githubusercontent.com/31130917/108230799-78b9db00-7184-11eb-8aef-705421fb5649.PNG)  
  
#### => Matrix를 쓸 때는 위와 같이 H(x) = XW 라고 표현  
  
![instance](https://user-images.githubusercontent.com/31130917/108231337-00074e80-7185-11eb-867c-27d4cb1a6893.PNG)  
![manyinstance](https://user-images.githubusercontent.com/31130917/108231621-478dda80-7185-11eb-9802-4618ebfa2ffd.PNG)  
  
#### => instance가 많을 경우 Matrix으로 빠르게 계산할 수 있음  
#### 위 그림에서 행은 instance의 수를, 열은 입력 변수의 수를 나타냄  
  
가변하는 값의 경우 아래와 같이 씀  
![n개](https://user-images.githubusercontent.com/31130917/108232054-b9feba80-7185-11eb-8085-2eb06aa305e4.PNG)  
  
위 그림의 n은 numpy에서는 -1로, tensorflow에서는 None으로 표현  
  
## 2. WX vs XW  
* 이론  
  ### H(x) = Wx + b  
* 구현(Tensorflow)  
  ### H(X) = XW  
  #### => 별도의 처리 없이 Matrix으로 계산 가능  
<출처 : 모두를 위한 딥러닝>
