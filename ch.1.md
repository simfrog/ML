# ch1. 기본적인 머신러닝의 용어와 개념 설명  

## 1. 머신러닝(Machine Learning)  
* 명시적 프로그래밍(Explicit programming)의 한계    
  * Spam filter : many rules  
  * Automatic driving : too many rules  
  
* ### 머신러닝 : 프로그램 자체가 어떤 자료나 현상에서 자동적으로 배우는 것  
  
* ### 머신러닝의 학습 방법  
  * ### Supervised learning : labeled examples(training set)을 가지고 학습하는 방법  
    * 머신러닝의 일반적인 문제  
     ex) Image labeling, Email spam filter, Predicting exam score  
    * 유형  
      * #### regression  
        ex) 공부한 시간을 기준으로 기말 점수 예측  
      * #### binary classification(분류)  
        ex) 공부한 시간을 기준으로 Pass/non-pass 결정  
      * #### multi-label classification  
        ex) 공부한 시간을 기준으로 등급(A, B, c, ...) 결정  
  * ### Unsupervised learning : un-labeled data, 즉 데이터를 보고 스스로 학습
    ex) Google news grouping, Word clustering
