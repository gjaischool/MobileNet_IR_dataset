# keras_MobileNetV2

### [데이터셋 출처](https://www.aihub.or.kr/aihubdata/data/view.do?currMenu=&topMenu=&aihubDataSe=data&dataSetSn=173)

### 데이터셋 구성
훈련 이미지 개수: 41052  
훈련 라벨(키포인트) 개수: 41052  
검증 이미지 개수: 5447  
검증 라벨(키포인트) 개수: 5447

### [keras_MobileNetV2_dataset준비.ipynb](https://github.com/gjaischool/keras_MobileNetV2/blob/main/keras_MobileNetV2_dataset%EC%A4%80%EB%B9%84.ipynb)
: 기존의 json파일의 경우 70개의 얼굴의 keypoint를 가지고 있습니다. keras_MobileNetV2를 이용하기 위해 이미지 경로와 70개의 키포인트 좌표(x1, y1, ..., x70, y70)를 저장할 CSV 파일을 생성합니다.  
training dataset의 경우 1개, val dataset의 경우 2개의 json파일에 문제가 발생했습니다.

### 현재 Batch_size 32 * 3 및 64 * 3로 100 epoch 돌리는중

하위 pull request test
