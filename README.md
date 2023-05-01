# Bart Machine Translation
- AI기술 자연어 처리 과정 2기 (구름)
  영-한 번역기 Neural Machine Translation
 
# Nerual Machine Translation
- AI기술 자연어 처리 과정 2기 (구름)에서 진행한 BART를 이용한 신경망 기계 번역 팀 프로젝트입니다.
- 사용 데이터 : 교육기관에서 제공한 영-한 병렬 데이터셋
- Bart를 사용한 모델 성능 향상
  - Huggingface에 등록되어 있는 'gogamza/kobart-base-v1'를 사용함
  - 다른 다국어 모델의 경우 존재하지 않는다는 가정하에 BART만을 이용한 모델 성능 향상을 목표로 프로젝트를 진행함
  - 부족한 데이터 문제를 해결하기 위해 역변역 기법을 사용함
- Learning Rate의 설정
  - 하나의 모델로 성능을 최대한 올려야하기 때문에 효과적인 하이퍼 파라미터를 찾는 것이 중요
  - Learning Rate를 제외한 Epoch과 Batch Size를 고정 시키고 실험을 진행
      - Loss 값이 충분히 떨어지는 지 확인하기 위해 Epoch의 값을 10으로 설정
      - Batch Size는 128로 고정
  - 이후 Learining Rate 별로 Loss 깂과 성능 지표인 조화 평균을 비교함
    - Loss의 경우 Learning Rate가 빠르게 떨어지는 것을 확인가능
    - Loss 값이 낮을수록 조화평균의 값이 높은것은 아니라고 판단 
    - 따라서 Loss가 충분히 낮고 조화평균의 점수가 가장 높은 Learning Rate의 값이 1e-4을 설정 
   ![image31](https://user-images.githubusercontent.com/89580953/159669713-9cb599b3-13ad-41c3-b1cd-51f1ad7388fb.png)
   ![image33](https://user-images.githubusercontent.com/89580953/159669730-8263e4d0-bfd1-452f-9972-f7d26191359c.png)
   <center><img src = "https://user-images.githubusercontent.com/89580953/235446519-b88d1e31-875a-40a6-9474-992508e9d679.png" width = "100%" height = "100%"></center>  

- Max Length 설정
  - 길이가 짧은 문장의 번역은 괜찮은 것으로 보이나 길이가 긴 문장의 번역은 아래의 사진과 같이 잘려서 출력이 되는 경우가 발생함
  -  그렇기 때문에 max_length를 설정함으로써 최적의 max_length를 확인

예시

![image](https://user-images.githubusercontent.com/89580953/159667570-336c61d2-3356-4522-b49d-1681d8b94a65.png)

Max Lengtg 실험


![0length_com](https://user-images.githubusercontent.com/89580953/159668918-b7b5982c-7416-410e-9be5-5ca9974b4a26.png)


![back translation](https://user-images.githubusercontent.com/89580953/235446519-b88d1e31-875a-40a6-9474-992508e9d679.png)


- Beam Search
  - 기본적으로 번역은 Beam search를 사용하여 수행함
  - 최적의 해를 구하기 위해 가장 높은 확률의 시퀀스를 반환함
  - K의 값을 크게 가져간다면 최적의 해를 반환할 확률은 올라가지만 그 만큼 시간이 오래 걸리기 때문에 최적의 k 값을 찾는 것이 중요
  
![0beams_com](https://user-images.githubusercontent.com/89580953/159856589-c43e42d9-d5be-4936-946d-9c7a82a9df0b.png)



K = 5인 경우 Beam Search의 예시 (참고 : [Beam Search](https://opennmt.net/OpenNMT/translation/beam_search/))


![beam_search](https://user-images.githubusercontent.com/89580953/159671631-a4161a5d-e06e-41d5-bde1-de9006454db7.png)
