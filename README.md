
<br> ![캡처](https://user-images.githubusercontent.com/64317686/119776563-0fbecd80-bf00-11eb-9225-56c05ec67844.JPG)
-  총 학습 횟수를 __K번__ 으로 고정
-  사전학습 모델에 본문을 입력으로 __추출 요약문__ 을 생성하는 과제를 __A번__ 학습
-  1차 미세조정 된 모델에 본문을 입력으로 __추상 요약문__ 을 생성하도록 __B (K - A)번__ 학습
<br><br>

### Requirements
- Python 3.7+
  - __pip install -r requirements.txt__ or manually install the packages below.
```
torch==1.8.1
transformers==4.6.0
json
rouge
pandas
numpy
summa
```
### Data
- 국립 국어원 요약 말뭉치 데이터셋, 신문 말뭉치 데이터셋 사용
- 본문은 신문 말뭉치 데이터셋, 요약문은 요약 말뭉치 데이터셋 에서 Parsing 
- 총 데이터 4,387개 8:1:1 비율로 나누어 3,509개의 학습 데이터, 439개의 검증 데이터, 439개의 평가 데이터를 사용해 학습 진행

### Run
- ##### Train 
  -  사전학습 모델 KoBART를 이용해 Fine-tuning
  -  arguments
      -  strategy (Choose strategy ['textrank', 'principal', 'lead_n'], default=None(Reference extractive summary))
      -  ext_epcohs
      -  abs_epochs
      -  seed (Random seed)
        ```
        python main.py --strategy "?" --exp_epochs "?" --abs_epcosh "?" --seed "?"
        ```
