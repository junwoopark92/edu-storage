# SK AI symposium 
2017.09.29

## Opening - 김지원

 * 과거 AI: rule based기반, expert 규칙주입
 * 최근 AI: data based, ml 현재 AI의 한 형태
 지도학습기반의 사람이상의 성능을 내는 것이 힘들다. 
 테스크마다 학습을 위한 데이터를 만드는 것은 힘듬.
 * Future AI:
 강화학습, 비지도학습이 더 중요해질것이라 판단
 강화학습의 문제: 학습시간의 문제, 현실에서 시뮬레이션이 쉽지 않음.
 이러한 문제를 해결하기 위해 가상세계에서 할수있도록 환경을 구축하는 것이 중요
 강화학습 + 비지도의 결합은 사람이상의 성능을 기대할수 있고 데이터생성에 비용이 들지 않는다.
 
 * t-brain, sk 가 무엇을 하고 있는가?   
 AI리서치 - DiscoGAN, continuos learning.  
 AI엔지니어링 - 
 
 * Why?: sk가 AI를 모든 분야에 적용할수 없음, 인력부족으로 


## DiscoGAN - 차문수
### Motivation
image to image translation	
기존 ground truth data가 필요함	
몇 도메인에서는 라벨링 데이터 자체가 불가능함		
라벨이 없을떄 일단 데이터를 다 모아보자: unsupervised learning의 기본적인 생각		
사람은 쉽게 두 그룹의 관계를 정의할수 있음: cross domain relation

### GAN 컨셉
generative model의 컨셉	
generative: 가짜 이미지 생성	
discriminator: 가짜와 진짜 이미지 구분	
=> 원래원본의 분포를 매칭시킬수 있는 효과가 있다.	

### discoGAN 문제접근
인풋을 노이즈로 시작하지 않음. 이미 존재하는 이미지로 풀어낸다.  	
금발 -> 흑발.  
디스크리미네이터가 흑발을 가지고 있는지밖에 판단하지 않음	
원래 우리가 만들고 싶은 금발여성이 아닌 어느누구나 흑발을 가지고 있으면 로스가 없음	
-> 생성이미지를 다시 원본과 비교

GAN이 학습이 잘안됨... 바닐라간같은 경우, 요즘엔 안정화되있음	
미러테스크를 아키텍처로 구현

### gan 평가 메져
토이도메인으로 타겟점에 얼마나 잘 모여 있는지확인

### 다른 cross domain relation 적용
남 -> 여.   
image 3d각도 -> 다른 객체의 3d각도(앵글이라는 관계를 알고 싶다.).     
가방 -> 신발

### disco간 공개
디스코간 skt깃헙 공개되어있음.
두도메인에서 이미지를 연결

### future work
여러모델이 만들어야하는 구조에서 하나의 네트워크에서 사용하고 싶다
스타일측면에서 나에 입혀보거나 적용시켜보는 테스크를 해보고 싶다. (transfer)

### 질문
1. 사이클 디스코 차이
사이클간은 리죨루션 문제를 품

2. 다른 데이터(텍스트 오디오)간
이미지외에 다른 데이터에서의 적용은 잘되는가요? 오디오나 텍스트에서는 아직 잘되고 있진않음


## FastText - armand joulin(facebook ai research)
fastext library: text classification si core to many problems(info retrieval or web search)

3 step
### 1. pre-trained word representation
learn a continuous repretaiotn of word using massive data
워드와 그 주변 컨텍스트의 스코어의 최대화로 학습
속도는 word2vec보다 2배정도 밖에 느리지 않지만 성능측면에서 더 좋음
cpu만가지고도 쉽게 할수 있음

### 2. scaling massive data

### 3. 

## Learning to See with no teacher - phillib isola(open ai)
labelling의 어려움

### supervised computer vision vs vision in nature
보통 자연적으로 라벨링된 시각이미지를 보는것이 아닌 raw한 이미지를 보는 것

### representation learning
image X -> vector -> image X`

training data pair(흑, 컬) 
input -> 흑 -> 예측 컬러   
		-> 컬러 -> 흑백 예측  
		
### gan
min max problem

### cycle gan
스타일 체인지
github.com/phillip


## Continual Learning with Deep genaerative Reply - 이정권
gan을 사용해서 딥러닝에서 발생하는 문제를 해결하자 

### continual learning
시간산의 흐름에서 테스크가 들어오면 AI가 해결하고 시간이지나서 다른 종류의 테스크를 문제를 푸는
즉 여러문제를 하나의 네트워크가 문제해결력을 보유하도록 하는 문제

### lifelong learning
시간의 흐름에 따른 지식의 축적

### multi task learning
시간의 축이 아닌 경우에도 하나의 agent가 여러가지 테스크를 해결하도록

### Catastrophic Forgetting problem 
위의 문제들이 힘든점: 뉴런넷에서 자주 발생하는 문제로 하나의 테스크를 가르쳐주고 다른 테스크를 배우면 이전의 문제해결력에 영향읆 미침
이전의 정답스페이스를 기억하지 못함

### trival sol
accumulate data: 이전의 데이터도 함께 쌓아 학습함

### related works: elastic weight consolidation
A를 푸는 문제의 weight 스페이스에서 B의 weight스페이스로 쉽게 이동해버려서 A의 문제해결력을 잊어버림
그래서 L2 regluraler추가해봤지만 그래도 일정방향만 바꿀뿐이지 부족

새로운 텀을 셍성
아이디어는 기존에 학습되지 않았던 weight를 사용해서 새로운문제를 풀수 있도록 설계

### 논문컨셉
간의 생성능력을 이용하여 샘플링을 하여서 예전문제를 풀던 능력을 갖을수 있다.
뇌에서 기억마다 장기혹은 단기, 위험상황 복합적으로 저장되어 있음

generator: 간에서 기존문제의 샘플을 생성, 다른 문제의 미니배치의 샘플을 섞어서 학습
solver: cnn으로 이루어진 것

### 실험결과
#### replay
생성된 데이터가 몇번까지 지속되서 기억되는지
전달되면서 조금식 감소함.... 간이 거의 완벽히 간 네트워크가 엠니스트 데이터분포를 추정하였기때문에
 
#### 새로운 테스크를 배우기
엠니스트와, 컬러 숫자이미지, 2가지 테스크

#### 순차적으로 라벨을 배우는 실험
01 구분 -> 23 구분 -> 456789구분

### mnist말고 다른 문제에 대해서는?
복잡한 데이터에 대해서는 간의 능력이 아직 부족
간의 경우에는 모드컬렉싱 문제가 있음. 이미지생성에 배리언스가 작아서 밸런스가 맞지않게됨 그래서 잊어버림..
