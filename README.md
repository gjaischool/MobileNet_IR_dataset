# keras_MobileNet

### [데이터셋 출처](https://www.aihub.or.kr/aihubdata/data/view.do?currMenu=&topMenu=&aihubDataSe=data&dataSetSn=173)

### 데이터셋 구성
훈련 이미지 개수: 41052  
훈련 라벨(키포인트) 개수: 41052  
검증 이미지 개수: 5447  
검증 라벨(키포인트) 개수: 5447  
이미지 사이즈 : 720 x 1280

### [keras_MobileNetV2_dataset준비.ipynb](https://github.com/gjaischool/keras_MobileNetV2/blob/main/keras_MobileNetV2_dataset%EC%A4%80%EB%B9%84.ipynb)
: 기존의 json파일의 경우 70개의 얼굴의 keypoint를 가지고 있습니다. keras_MobileNetV2를 이용하기 위해 이미지 경로와 70개의 키포인트 좌표(x1, y1, ..., x70, y70)를 저장할 CSV 파일을 생성합니다.  
training dataset의 경우 1개, val dataset의 경우 2개의 json파일에 문제가 발생했습니다.

## 폴더내 파일 설명
### 1. V2_s224_b16_lr001.ipynb  
: MobileNetV2 / scale img size 224 / batchsize 16 / Adam / lr 0.001 / 100 epochs  
Epoch 83: val_loss improved from 2.90543 to 2.88290, saving model to b16_lr001.h5  
- 164s 190ms/step - loss: 17.9087 - mae: 3.3129 - val_loss: 2.8829 - val_mae: 1.2605

### 2. V2_s224_b32_lr001.ipynb  
: MobileNetV2 / scale img size 224 / batchsize 32 / Adam / lr 0.001 / 100 epochs  
Epoch 87: val_loss improved from 5.73788 to 5.03280, saving model to b32_lr001.h5  
- 126s 294ms/step - loss: 18.7572 - mae: 3.3922 - val_loss: 5.0328 - val_mae: 1.6460

### 3. V3s_s224_b16_lr001.ipynb  
: MobileNetV3 small / scale img size 224 / batchsize 16 / Adam / -50ep : lr 0.001 51ep- : lr 0.0005 / 100 epochs  
Epoch 65: val_loss improved from 32.58451 to 27.78898, saving model to v3s_b16_lr001.h5   
- 130s 152ms/step - loss: 36.0579 - mae: 4.7001 - val_loss: 27.7890 - val_mae: 3.8681 - lr: 5.0000e-04

### 4. V3s_SGD_b16_lr001.ipynb  
: MobileNetV3 small / scale img size 224 / batchsize 16 / SGD(momentum = 0.9) / -50ep : lr 0.001 51ep- : lr 0.0005 / 100 epochs 
Epoch 81: val_loss improved from 9.32639 to 6.76336, saving model to v3s_sgd_b16_lr001.h5  
- 130s 152ms/step - loss: 40.0433 - mae: 4.9617 - val_loss: 6.7634 - val_mae: 1.9311 - lr: 5.0000e-04

### 5. V3l_s224_b16_lr001.ipynb  
: MobileNetV3 large / scale img size 224 / batchsize 16 / Adam / -50ep : lr 0.001 51ep- : lr 0.0001 / 100 epochs 
Epoch 100: val_loss improved from 3.50238 to 3.10394, saving model to v3l_b16_lr001.h5  
- 143s 166ms/step - loss: 23.1025 - mae: 3.7658 - val_loss: 3.1039 - val_mae: 1.2559 - lr: 1.0000e-04

### 6.




## 진행하면서 배운점
1. 학습 경향성을 보기 위해 고정된 learning rate(ex 0.001)로 돌려보는게 좋다.
2. 모델에 따라 json파일을 변환 시키는 작업이 필요하다.
3. 720 * 1280 이미지를 224 * 224로 축소하는 과정에서 패딩 추가
4. gpu 3장을 활용하여 모델 학습
5. 학습 후 load_model 이용할때 역시 gpu 3장 활용
6. 기존에는 keypoint 값을 0~244로 진행하니 학습이 잘되지 않는 것을 발견
