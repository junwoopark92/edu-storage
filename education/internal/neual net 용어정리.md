## neual net 용어정리

### 1. Artificial Neural Network

* Single-layer Neural Networks (number of layer)
	* Feedforward Neural networks (net structure)
		* Perceptron 
		* Support Vector Machine (구조상 svm도 유사)
		
* Multi-layer Neural Networks
	* Feedforward Neural networks
		* Multi-layer perceptron
	* CNN, RNN(like recurrent)

### 2. Single-layer Neural Networks
1. Feedforward Neural networks:
2. Perceptron: is an algorithm for learning a binary classifier  
=> 이진 분류기를 학습시키는 알고리즘    
=> 뉴럴넷의 특별한 형태  
=> 일반적으로 perceptron이라하면 sigle layer nn

	binary classifier: is function the maps its inpus x to an output value f(x)  
	=> 실수벡터를 정의역으로 0,1을 공역으로 가지는 함수

	1). 여기서 f(x)는 다음과 같음
$$
f\left( x \right) =\begin{cases} \begin{matrix} 1 & if\quad w\cdot x+b>0 \end{matrix} \\ \begin{matrix} 0 & otherwise \end{matrix} \end{cases}
$$

	2). weight update rule은 다음과 같음 (not backpropagation, stepping towards)
$$
{ w }_{ i }\left( t+1 \right) ={ w }_{ i }\left( t \right) +\left( { d }_{ i }-{ y }_{ i }(t) \right) { x }_{ j,i }\quad for\quad all\quad feature\quad 0\le i\le n
$$

3. Support Vector Machine:

### 3. Multi-layer Neural Networks