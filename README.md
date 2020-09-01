# Image Classification with TensorFlow Lite Model Maker
- android application에 모델을 적용하기 위해서는 tflite 변환이 필요. 
- on-device ML applications에 모델을 적용하기 위해 TensorFlow Lite Model Maker에서 모델 학습을 제공. 
- TensorFlow Lite Model Maker를 통해 모델 학습 및 tflite 변환.
- android application에 모델을 쉽게 적용할 수 있도록 한다.

# Model Maker 학습
농산물 부패를 감지하는 모델을 만들기 위해 체리를 선택하여 체리 부패 정도를 감지하는 모델을 생성한다. 

notebook: [image-classification](https://github.com/RottenFruitsOSS/image-classification/blob/master/Image_classification.ipynb)
```
0. tflite-model-maker 설치

1. cherry_dataset.zip 파일를 통해 이미지 데이터를 로딩한다. 
```
dataset: https://github.com/RottenFruitsOSS/DataSet

[cherry_dataset.zip](https://github.com/RottenFruitsOSS/image-classification/blob/master/cherry_dataset.zip)
```
2. model maker를 통하여 이미지 학습
  model = EfficientNet-Lite0, epochs = 1000
  이미지 사이즈 224로 최적화 모델 학습 진행
  
3. 모델 평가 및 loss, accuracy
   loss: 0.5192
   accuracy: 0.9688
   
4. TensorFlow Lite Model 변환 및 export
   model.tflite 파일 생성
```
## 예측 결과
검은색 = 예측 맞음

빨간색 = 예측 틀림 
![](https://raw.githubusercontent.com/RottenFruitsOSS/image-classification/master/predict_cherry.png)

## Android Application 모델 적용
RottenFruitsCamera: https://github.com/RottenFruitsOSS/RottenFruitsCamera
```
android/
  app/
    asset/custom_models
      custom.tflite       -------------> 해당 위치에 완성된 tflite 파일 위치(asset 폴더에 위치)
```

android/app/assets/custom_models 에 완성된 .tflite 파일을 추가시키면 새로 학습한 custom model을 모바일에서 사용할 수 있다. 
[here](https://github.com/RottenFruitsOSS/RottenFruitsCamera/tree/master/android/app/assets/custom_models)
