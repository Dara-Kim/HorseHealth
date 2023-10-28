# HorseHealth
Kaggle playground Competition-Predict Health Outcomes of Horses

Start Date - September 12, 2023<br/>
Final Submission Deadline - October 2, 2023
## 목차
1. [대회 소개 및 목표](#대회-소개-및-목표)
2. [데이터 셋 설명](#데이터-셋-설명)
3. [EDA](#eda)
4. [코드](#코드)
5. [결과 및 한계점](#결과-및-한계점)
6. [개선사항](#개선사항)

## 대회 소개 및 목표



Horse Survival Dataset을 이용해 말의 생존 여부를 3가지로 예측.
- Lived
- Euthanized
- Died

## 데이터 셋 설명

원본 데이터: https://www.kaggle.com/datasets/yasserh/horse-survival-dataset/data

말의 건강 상태 데이터 

- train.csv - the training dataset; outcome is the (categorical) target
- test.csv - the test dataset; your objective is to predict outcome
- sample_submission.csv - a sample submission file in the correct format

## EDA


## 코드
모델 설명 <br/>
다른 모델을 선택한 이유 <br/>
e.g. 이러이러해서 이걸 추가하면 좋을 것 같고 성능이 어떻게 변했다 <br/>
모델 간 비교 <br/>
기술적인 부분은 표로 (평가 지표를 이용해서) <br/>
왜 이걸 쓰려고 했는지 <br/>
왜 넣었고 왜 뺐는지 기록할 것(수정 기록) <br/>
12시간 전에 만들었다... 그런 실수를 안 하겠다.. <br/>

shake up으로 인해.. 직관이 좋은 결과를 냈다 <br/>

1. origin data 활용
2. feature engineering
   - 새로운 feature 생성
   - 컬럼 특성별 label encoding
   - 컬럼 특성별 scaling (별도의 scaler는 사용하지 않음)
   - *scaler를 사용하면 점수 하락*
   - 결측 행 제거
   - 범주형 feature의 결측값은 중간값으로
   - 숫자형 feature의 결측값은 KNNImputer로
3. 모델 선정: Lazy predict
   - lgbm의 feature importance 기준 feature 삭제
   - xgb, lgb, cat 모델 사용
   - optuna로 하이퍼파라미터 조정
4. stacking classifier 사용
   
## 결과 및 한계점


## 개선사항
