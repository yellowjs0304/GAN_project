## 3차 과제 "GAN project" github 페이지 입니다.   
### 조교 이메일 : wodbs95@gmail.com   
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
* cGAN이란?   
  * 생성자가 랜덤하게 이미지를 생성하는 것이 아닌, 원하는 이미지를 생성할 수 있는 모델
  * 생성자, 판별자의 입력으로 noise외에 label을 함께 넣어줌
  * [참고 사이트](https://rm-7.tistory.com/2)   
  
### 2.DCGAN(Deep Convolutional GAN) 구현   
![IMAGE2](/ignore/dcgan.JPG)
* DCGAN이란?   
  * Convolutional 구조를 사용한 GAN 모델
  * [참고 사이트](http://jaejunyoo.blogspot.com/2017/02/deep-convolutional-gan-dcgan-1.html)   
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
<span style="color:red">작업2 : build_generator(), build_discriminator() 외에 수정 금지</span>   
<span style="color:red">다른 딥러닝 프레임워크 사용 금지</span>   
- - -
## ISSUE(질문이 들어오면 계속 업데이트합니다.)   
### Index   
1. #### [No such file or directory](#error1)   

#### 1.error1   
* 에러 내용
```
FileNotFoundError: [Errno 2] No such file or directory: 'loss_graph/gan_loss_epoch_5000.png'
```
* 에러 원인 : 해당 폴더가 존재하지 않아서 나는 에러(images 혹은 saved_model폴더가 없을 경우 같은 에러가 날 수 있습니다.)   
* 해결 : 해당 위치에 폴더 생성   