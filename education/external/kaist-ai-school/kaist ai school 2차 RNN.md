# Kaist AI School 2차

## RNN
데이터를 두가지로 분류가능: 관측이 한번에 됨 vs 순서가 존재(시계열)

과거를 감안해서 미래를 예측하는 구조
### SRN(simple Recurrent nn)
파타미터 값들은 재사용(sharing)

### RNN in-out에 따른 종류
one2one: vanilla ff nn	
one2many: image captioning	
many2one: video -> activity	
many2many: translation	
many2many+ 동시성: 음성인식기	

### rnn 훈련은 어떻게?
BPTT(backpropagation through time)	
#### 학습시의 문제
vanising gradient:

* lstm 
* gru	

overfitting:

* l2 term
* dropout
* early stoping	

### langauge modeling
NNLM

### RNN variation
rnn의 다양한 변형들

* bidirectional RNN
* LSTM	
97년등장 등장초기 반응x, 이해하기어렵고, 데이터문제떄문
이후 인기를 얻음	
게이트 개념: 입력을 얼만큼 받을것인가 결정	
input gate 시그모이드사용 1: 입력을 다받아들임, 0: 입력을 받아들이지 않음	
forget gate: 기존의 값을 잊도록	
block input:	
cell state: 기억, 메모리, 과거의 값을 저장, 새로받아야할 입력해야할 값을 포겟과 인풋게이트에 의해 저장	
output gate: 출력을 얼만큼	

cell이 과거의 state를 저장
입력과 과거의 값을 갖고 forget을 만듬

cell: long term
hidden: short term

* GRU
LSTM의 gate를 줄여라 복잡하다
hidden에 과거의 값들이 저장에 되어있음
히든값에 cell정보도 포함한 개념

### NTM(neural turing machine)
복잡한계산을 할때 중간값을 컴퓨터는 쉽게 기억할수 있음
사람은 X
사람은 대신 인지를 잘함
사람+컴퓨터의 장점 결합

srn -> lstm -> ntm

ntm에는 메모리가 존재
메모리를 읽고 쓰기 위해선 헤더가 필요함
어디를 쓰고 어디를 지울것인가?
이 헤더를 lstm을 사용

무엇을 할수 있나? : 영국의 자하도를 기억, 가족의 가계도를 기억 -> 그래프를 기억
최단거리를 알려줘? 

### RHN(Recurrent Highway Network)
lstm의 성능을 더 파워풀하게 올릴 수 있을 것인가

입력부터 출력의 깊이 depth 
반복의 깊이 recurrent depth

residual net구조를 이용한 

