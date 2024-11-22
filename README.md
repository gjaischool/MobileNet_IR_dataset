# keras_MobileNet

### [데이터셋 출처](https://www.aihub.or.kr/aihubdata/data/view.do?currMenu=&topMenu=&aihubDataSe=data&dataSetSn=173)

### 데이터셋 구성
훈련 이미지 개수: 41052  
훈련 라벨(키포인트) 개수: 41052  
검증 이미지 개수: 5447  
검증 라벨(키포인트) 개수: 5447  
이미지 사이즈 : 720 x 1280

### IR_dataset_준비_분석.ipynb
: 기존의 json파일의 경우 70개의 얼굴의 keypoint를 가지고 있습니다. keras_MobileNetV2를 이용하기 위해 이미지 경로와 70개의 키포인트 좌표(x1, y1, ..., x70, y70)를 저장할 CSV 파일을 생성합니다.  
training dataset의 경우 1개, val dataset의 경우 2개의 json파일에 문제가 발생했습니다.

## 폴더내 파일 설명
[각 파일의 best model](https://drive.google.com/drive/folders/1K-WdH8WnHdSLzUm-ucGt8p5QEYICQ-pm)
### 1. V2_s224_b16_lr001.ipynb  
: MobileNetV2 / scale img size 224 / batchsize 16 / Adam / lr 0.001 / 100 epochs  
Epoch 83: val_loss improved from 2.90543 to 2.88290, saving model to b16_lr001.h5  
164s 190ms/step - loss: 17.9087 - mae: 3.3129 - val_loss: 2.8829 - val_mae: 1.2605

### 2. V2_s224_b32_lr001.ipynb  
: MobileNetV2 / scale img size 224 / batchsize 32 / Adam / lr 0.001 / 100 epochs  
Epoch 87: val_loss improved from 5.73788 to 5.03280, saving model to b32_lr001.h5  
126s 294ms/step - loss: 18.7572 - mae: 3.3922 - val_loss: 5.0328 - val_mae: 1.6460

### 3. V3s_s224_b16_lr001.ipynb  
: MobileNetV3 small / scale img size 224 / batchsize 16 / Adam / -50ep : lr 0.001 51ep- : lr 0.0005 / 100 epochs  
Epoch 65: val_loss improved from 32.58451 to 27.78898, saving model to v3s_b16_lr001.h5   
130s 152ms/step - loss: 36.0579 - mae: 4.7001 - val_loss: 27.7890 - val_mae: 3.8681 - lr: 5.0000e-04

### 4. V3s_SGD_b16_lr001.ipynb  
: MobileNetV3 small / scale img size 224 / batchsize 16 / SGD(momentum = 0.9) / -50ep : lr 0.001 51ep- : lr 0.0005 / 100 epochs   
Epoch 81: val_loss improved from 9.32639 to 6.76336, saving model to v3s_sgd_b16_lr001.h5  
130s 152ms/step - loss: 40.0433 - mae: 4.9617 - val_loss: 6.7634 - val_mae: 1.9311 - lr: 5.0000e-04

### 5. V3l_s224_b16_lr001.ipynb  
: MobileNetV3 large / scale img size 224 / batchsize 16 / Adam / -50ep : lr 0.001 51ep- : lr 0.0001 / 100 epochs   
Epoch 100: val_loss improved from 3.50238 to 3.10394, saving model to v3l_b16_lr001.h5  
143s 166ms/step - loss: 23.1025 - mae: 3.7658 - val_loss: 3.1039 - val_mae: 1.2559 - lr: 1.0000e-04

### 6. V2_s224_b16_lr001(추가학습).ipynb  
: MobileNetV2 / scale img size 224 / batchsize 16 / RMSprop / reduce lr / 100 epochs  
Epoch 75: val_loss improved from 2.13493 to 2.12921, saving model to v2_b16_rmsprop.h5   
147s 171ms/step - loss: 16.0767 - mae: 3.1307 - val_loss: 2.1292 - val_mae: 1.0208 - lr: 4.0000e-05

### 7. V3l_adam_lr001_norm.ipynb  
이전 모델에서는 학습이 되지 않는 것 같아 팀원들과 코드 리뷰중 keypoint 좌표가 정규화 하지 않는 것을 발견  
: MobileNetV3 large / scale img size 224 / batchsize 16 / Adam / lr 0.001 / 100 epochs  
Epoch 52: val_loss improved from 0.00014 to 0.00007, saving model to v3l_adam_lr001.h5   
134s 156ms/step - loss: 2.6769e-05 - mae: 0.0039 - val_loss: 7.1007e-05 - val_mae: 0.0063  
![1](https://github.com/user-attachments/assets/361171a3-51f9-41ea-b1e8-83caef7ea532)

### 8. V3s_adam_lr_norm.ipynb  
: MobileNetV3 small / scale img size 224 / batchsize 16 / Adam / -50ep : lr 0.001 51ep- : lr 0.0001 / 100 epochs  
Epoch 98: val_loss improved from 0.00006 to 0.00006, saving model to v3s_adam_lr.h5   
102s 119ms/step - loss: 3.0862e-05 - mae: 0.0041 - val_loss: 6.4468e-05 - val_mae: 0.0058 - lr: 1.0000e-04  
![1](https://github.com/user-attachments/assets/14d22431-1608-40f2-acb6-9e22f8d75c31)  

### 9. V2_adam_lr_norm.ipynb  
: MobileNetV3 small / scale img size 224 / batchsize 16 / Adam / -50ep : lr 0.001 51ep- : lr 0.0001 / 100 epochs  
Epoch 92: val_loss improved from 0.00005 to 0.00005, saving model to v2_adam_norm.h5   
127s 148ms/step - loss: 2.3603e-05 - mae: 0.0036 - val_loss: 4.7635e-05 - val_mae: 0.0049 - lr: 1.0000e-04  
![image](https://github.com/user-attachments/assets/3ef18a76-c12e-4db5-8be5-2266feeeb7dc)   

### 10. V3l_adam_aug.ipynb  
: MobileNetV3 large / scale img size 224 / batchsize 16 / Adam / -100ep : lr 0.001 101ep- : lr 0.0001 / 200 epochs  
Epoch 113: val_loss improved from 0.00004 to 0.00004, saving model to v3l_adam_lr001_aug.h5 
371s 72ms/step - loss: 2.3507e-05 - mae: 0.0036 - val_loss: 3.7017e-05 - val_mae: 0.0042 - lr: 1.0000e-04  
<중간에 커널이 끊어져 history 날아감. csv_logger 사용하자>  

### 10-1. V3l_adam_aug.ipynb(v3l_adam_lr001_aug.h5 추가 학습)
: MobileNetV3 large / scale img size 224 / batchsize 16 / RMSprop / 1e-7 / 100 epochs
 Epoch 61: val_loss improved from 0.00004 to 0.00004, saving model to v3l_rmsprop_aug.h5    
 368s 72ms/step - loss: 2.4243e-05 - mae: 0.0037 - val_loss: 3.6058e-05 - val_mae: 0.0042
![image](https://github.com/user-attachments/assets/e8fb06d0-c7ae-49d4-aeab-ca0fef5443e6)

### 10-2. V3l_adam_aug.ipynb(v3l_adam_lr001_aug.h5 추가 학습)  
: MobileNetV3 large / scale img size 224 / batchsize 16 / RMSprop / 1e-3 / 100 epochs  
Epoch 91: val_loss improved from 0.00004 to 0.00004, saving model to v3l_rmsprop_1e-3_aug.h5  
374s 73ms/step - loss: 2.3127e-05 - mae: 0.0036 - val_loss: 3.5635e-05 - val_mae: 0.0041 
![image](https://github.com/user-attachments/assets/d5100392-4a1d-468f-9077-aa29cccc2a75)  

### 11. V2_adam_aug.ipynb(현재 이 파일은 날아감...)
: MobileNetV2 / scale img size 224 / batchsize 16 / Adam / 1e-3 / 100 epochs  
Epoch 70: val_loss improved from 0.00027 to 0.00021, saving model to v2_adam_lr001_aug.h5   
332s 131ms/step - loss: 1.6884e-04 - mae: 0.0102 - val_loss: 2.0608e-04 - val_mae: 0.0100  
![image](https://github.com/user-attachments/assets/342aac8e-cc01-4541-b11c-f492cfa8c8b1)

### 12. V2_adam_half_aug.ipynb  
: MobileNetV2 / scale img size 224 / batchsize 16 / Adam / 1e-3 / 100 epochs   
Epoch 100: val_loss improved from 0.00018 to 0.00014, saving model to v2_adam_lr001_half_aug.h5 
202s 79ms/step - loss: 2.7715e-04 - mae: 0.0132 - val_loss: 1.3596e-04 - val_mae: 0.0093
![image](https://github.com/user-attachments/assets/256ec0a1-5a0e-45d9-99ba-5ceb958ad514)

### 모델 총 정리  
![image](https://github.com/user-attachments/assets/2b45ac0e-d0b9-4658-a6fd-d8fae2a081c7)

## 진행하면서 배운점
1. 학습 경향성을 보기 위해 고정된 learning rate(ex 0.001)로 돌려보는게 좋다.
2. 모델에 따라 json파일을 변환 시키는 작업이 필요하다.
3. 720 * 1280 원본 비율 유지하면서 224 * 224로 축소하는 과정에서 패딩 추가
4. gpu 3장을 활용하여 모델 학습
5. 학습 후 load_model 이용할때 역시 gpu 3장 활용
6. 기존에는 keypoint 값을 0~244로 진행하니 학습이 잘되지 않는 것을 발견(정규화의 중요성)
7. 랜덤 증강이다 보니 학습에 적절하지 않는 데이터가 존재해서 학습이 중간에 멈춤.
