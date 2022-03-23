# Bart Machine Translation
- AI기술 자연어 처리 과정 2기 (구름)
  영-한 번역기 Neural Machine Translation
 
# Nerual Machine Translation
- AI기술 자연어 처리 과정 2기 (구름)에서 진행한 BART를 이용한 신경망 기계 번역 팀 프로젝트입니다.
- 사용 데이터 : 교육기관에서 제공한 영-한 병렬 데이터셋
- Bart를 사용한 모델 성능 향상
  - Huggingface에 등록되어 있는 'gogamza/kobart-base-v1'를 사용함
  - 다른 다국어 모델의 경우 존재하지 않는다는 가정하에 BART만을 이용한 모델 성능 향상을 목표로 프로젝트를 진행함
- Learning Rate의 설정
  - 하나의 모델로 성능을 최대한 올려야하기 때문에 효과적인 하이퍼 파라미터를 찾는 것이 중요
  - Learning Rate를 제외한 Epoch과 Batch Size를 고정 시키고 실험을 진행
      - Loss 값이 충분히 떨어지는 지 확인하기 위해 Epoch의 값을 10으로 설정
      - Batch Size는 128로 
- Max Length 설정
  - 길이가 짧은 문장의 번역은 괜찮은 것으로 보이나 길이가 긴 문장의 번역은 아래의 사진과 같이 잘려서 출력이 되는 경우가 발생함
  -  그렇기 때문에 max_length를 설정함으로써 최적의 max_length를 확인

- 예시

![image](https://user-images.githubusercontent.com/89580953/159667570-336c61d2-3356-4522-b49d-1681d8b94a65.png)

- Max Lengtg 실험

![0length_com](https://user-images.githubusercontent.com/89580953/159668918-b7b5982c-7416-410e-9be5-5ca9974b4a26.png)



-
