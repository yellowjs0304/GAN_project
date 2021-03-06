## 3차 과제 "GAN project" github 페이지 입니다.   
### 조교 이메일 : wodbs9522@gmail.com   
### 목차
#### * [과제 개요](#과제-개요)   
#### * [수행 작업 설명](#수행-작업-설명)   
#### * [제출 결과물](#제출-결과물)   
#### * [환경 세팅](#환경-세팅)   
#### * [폴더 구조](#폴더-구조)   
#### * [기본코드 설명](#기본코드-설명)   
#### * [에러 목록](#에러-목록)   
- - -
## 과제 개요   
* 과제 주제 : 적대적 신경망(GAN)으로 Fashion MNIST 영상 분류 및 생성하기   
![IMAGE1](/ignore/images.jpg)
* 과제 목표 : 영상 분류 및 생성을 위한 인공 신경망 설계   
* 수행 작업   
  * cGAN(Conditional GAN) 구현    
  * DCGAN(Deep Convolutional GAN) 구현      
- - -
## 수행 작업 설명
### 1.cGAN(Conditional GAN) 구현   
![IMAGE2](/ignore/cgan.JPG)   
* 작업 내용   
  * 베이스 모델을 cGAN으로 변경(cgan.py)   
  * cgan.py파일 내의 (1)~(12)의 코드 작성   
* cGAN이란?   
  * 생성자가 랜덤하게 이미지를 생성하는 것이 아닌, 원하는 이미지를 생성할 수 있는 모델
  * 생성자, 판별자의 입력으로 noise외에 label을 함께 넣어줌
  * [참고 사이트](https://rm-7.tistory.com/2)   
* 결과물   
  * 베이스 모델(gan.py), 구현한 모델(cgan.py)의 생성된 이미지, loss를 비교   
  * epoch은 5000으로 비교   
  
### 2.DCGAN(Deep Convolutional GAN) 구현   
![IMAGE2](/ignore/dcgan.JPG)   
* 작업 내용   
  * 베이스 모델을 DCGAN으로 변경(dcgan.py)   
  * dcgan.py파일 내의 (1),(2)의 코드 작성   
  * generator   
    * input size : [100]   
	* output size : [28,28,1]   
  * discriminator   
    * input size : [28,28,1]   
	* output size : [1]   
* DCGAN이란?   
  * Convolutional 구조를 사용한 GAN 모델
  * [참고 사이트](http://jaejunyoo.blogspot.com/2017/02/deep-convolutional-gan-dcgan-1.html)   
* 결과물   
  * 베이스 모델(gan.py), 구현한 모델(dcgan.py)의 생성된 이미지, loss를 비교   
  * epoch은 5000으로 비교   
  
#### 코드 작성시 필요하시면, [케라스 문서](https://www.tensorflow.org/api_docs/python/tf/keras)에서 검색하여 사용하세요.   

- - -
## 제출 결과물   
1.과제 보고서   
  * 작업1의 결과와 분석   
  * 작업2의 결과와 분석   
  * 보고서 양식 별도 제공   
    
2.작업2의 구현 코드(dcgan.py)   
3.작업2의 학습된 모델(model.h5)   
- - -
## 환경 세팅   

1.window(No Anaconda)
```
python –m pip install numpy matplotlib   
python –m pip install tensorflow==2.0
```   

2.window(Anaconda)
```
conda install numpy matplotlib   
pip install tensorflow-cpu  # CPU version(GPU가 없을 경우 설치)
pip install tensorflow-gpu  # GPU version
```   

3.ubuntu(Anaconda)
```
conda install tensorflow==2.0
conda install numpy matplotlib
```
- - -
## 폴더 구조   
```
code
  ㄴcGAN
    ㄴimages
    ㄴloss_graph
    ㄴsaved_model
    ㄴcgan.py
  ㄴDCGAN
    ㄴimages
    ㄴloss_graph
    ㄴsaved_model
    ㄴdcgan.py
  ㄴGAN
    ㄴimages
    ㄴsaved_model
    ㄴsaved_model
    ㄴgan.py
```   

## 기본코드 설명   
```
* gan.py : MLP로 구성된 기본 GAN(베이스 모델)   
* cgan.py : conditional GAN(작업1 관련 파일)
* dcgan.py : deep convolutional GAN(작업2 관련 파일)
  * GAN,CGAN,DCGAN() : 각 모델 클래스
    * train() : 모델 학습
    * build_generator() : 생성자 모델 정의
    * build_discriminator() : 판별자 모델 정의
    * plotLoss() : 손실 그래프 생성(loss_graph 폴더 안에 자동 생성)
    * sample_images() : 결과 이미지 생성(images폴더 안에 자동 생성)
    * save/load model() : 학습된 모델 저장 및 불러오기(saved_model 폴더 안에 자동 생성)
```
<span style="color:red">※ 주의사항 ※</span>   
<span style="color:red">작업1 : 표기 해둔 (1)~(12)외에 수정 금지(모델은 MLP기반 그대로 유지)</span>   
<span style="color:red">작업2 : 표기 해둔 (1),(2)(build_generator(), build_discriminator()) 외에 수정 금지</span>   
<span style="color:red">다른 딥러닝 프레임워크 사용 금지</span>   

- - -
## 에러 목록   
### Index   
1. #### [No such file or directory](#error1)   
2. #### [데이터 다운로드 시간이 너무 오래걸려요!](#error2)   
3. #### [Pycharm으로 실행이 안돼요!](#error3)   
4. #### [gan.py의 loss_graph가 안생겨요!](#error4)   

### error1   
* 에러 내용 : "No such file or directory"   
```
FileNotFoundError: [Errno 2] No such file or directory: 'loss_graph/gan_loss_epoch_5000.png'
```
* 에러 원인 : 해당 폴더가 존재하지 않아서 나는 에러(images 혹은 saved_model폴더가 없을 경우 같은 에러가 날 수 있습니다.)   
* 해결 : 해당 위치에 폴더 생성([폴더 구조](#폴더-구조)를 참고해주세요.)   

### error2   
* 에러 내용 : "데이터 다운로드 시간이 너무 오래걸려요!"   

(1)[여기](http://mjgim.me/2018/08/30/fashion_mnist.html)를 클릭하여 데이터를 직접 다운받아주세요.   
![IMAGE3](/ignore/error2.png)   

(2)[여기](https://appia.tistory.com/164)를 참고하여 pandas를 설치해 주세요.   

(3)데이터 로드 부분의 코드를 아래와 같이 변경해 주세요.   
```
## pandas import
# 맨 위에 pandas를 import해주세요.
import pandas as pd

##코드 변경
#변경전(train함수 안에 있는 코드입니다.)
(X_train, _), (_, _) = fashion_mnist.load_data() 혹은 (X_train, y_train), (_, _) = fashion_mnist.load_data()

#변경후
train_data = pd.read_csv("data/fashion-mnist_train.csv") #경로는 본인이 데이터 파일을 넣어둔 곳으로 잡아주셔야 합니다.
y_train = np.array(train_data["label"][:])
del train_data["label"]
X_train = np.array(train_data[:])
```   

### error3   
* 에러 내용 : "Pycharm으로 실행이 안돼요!"   

(1)Anaconda Prompt를 실행하여, 본인이 만든 환경으로 접속해 주세요.   
```
conda activate 환경이름
```   
![IMAGE4](/ignore/conda1.JPG)   
(2)코드가 있는 폴더로 이동해 주세요.   
```
cd 폴더 경로
```   
![IMAGE5](/ignore/conda2.JPG)   
(3)파일을 실행해 주세요.   
```
python 파일이름.py
```   
![IMAGE6](/ignore/conda3.JPG)   
   
### error4   
* 에러 내용 : "gan.py의 loss_graph가 안생겨요!"   
* 에러 원인 : plotLoss 함수 추가 이전 버전이 배포되면서 생긴 문제입니다.   
* 해결 : 깃허브에서 code/GAN 내의 gan.py 파일을 다시 받아주세요.   

